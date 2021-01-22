When building or testing your application inside a Docker container, you will need to configure Docker to [forward its SSH agent connections](https://docs.docker.com/develop/develop-images/build_enhancements/#using-ssh-to-access-private-data-in-builds). This allows the container to authenticate against any SSH dependencies defined in your deps.edn file or in aliases used in your build script.

When invoking Docker commands, you will need to enable the [Docker BuildKit](https://docs.docker.com/develop/develop-images/build_enhancements/) and pass the default ssh agent to any build commands:

```shell
DOCKER_BUILDKIT=1 docker build --ssh default .
```

Now, any Docker RUN steps with `-mount=type=ssh` will have access to the `SSH_AUTH_SOCK` environment variable and your SSH agent. All other steps will not have this access. This currently also requires enabling the experimental dockerfile syntax by adding this line at the top of your Dockerfile:

```docker
# syntax=docker/dockerfile:1.0.0-experimental
```

To load dependencies with this connection, we'll need to install git and your known ssh hosts into the build container. For GitHub, you'll want to add the following steps:

```docker
RUN apt-get update -y
RUN apt-get install git
RUN mkdir -p -m 0600 ~/.ssh && ssh-keyscan github.com >> ~/.ssh/known_hosts
```

Now we can execute the build with our SSH connection:

```docker
RUN --mount=type=ssh clojure -Spom && \
    clojure -Sdeps '{:deps {seancorfield/depstar {:mvn/version "0.5.2"}}}' \
    -m hf.depstar.uberjar my-app.jar -C -m my-app.main
```

## Sample Dockerfile

```docker
# syntax=docker/dockerfile:1.0.0-experimental

### Build the application within a Docker image
FROM clojure:openjdk-8-tools-deps as builder
WORKDIR /home/app
COPY . .

### Install git so we can pull dependencies from GitHub repositories
RUN apt-get update -y
RUN apt-get install git

### Download public RSA keys for github.com
RUN mkdir -p -m 0600 ~/.ssh && ssh-keyscan github.com >> ~/.ssh/known_hosts

### Use seancorfield/depstar to create a POM and build the app into an uberjar
### This fetches dependencies AOT, so we don't need to fetch anything when the app starts
### Make sure your app specifies a (:gen-class) directive in the my-app.main namespace
### This will AOT compile the my-app.main namespace, and anything required in that namespace
RUN --mount=type=ssh clojure -Spom && \
    clojure -Sdeps '{:deps {seancorfield/depstar {:mvn/version "0.5.2"}}}' \
    -m hf.depstar.uberjar my-app.jar -C -m my-app.main
```