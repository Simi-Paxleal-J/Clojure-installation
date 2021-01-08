This is a page to collect tools that use or work with tools.deps.alpha (or the clojure tools).

## User-level configuration for Clojure tools

* [practicalli/clojure-deps-edn](https://github.com/practicalli/clojure-deps-edn) - aliases for community tools and library repository configuration examples

## Project creation

* [clj-new](https://github.com/seancorfield/clj-new) - generate new project templates using just the `clj` command-line tool
* [clj-template](https://github.com/io-tupelo/clj-template) - Clone this template project and start writing code. Includes both Deps/CLI (+ Kaocha) and Leiningen (+ lein-test-refresh)

## Lint tool integration

* [clj-check](https://github.com/athos/clj-check) - `lein check` alternative for Clojure CLI
* [cljfmt-runner](https://github.com/JamesLaverack/cljfmt-runner) — run cljfmt to find and/or fix code formatting issues

## Build tool integration

* [boot-tools-deps](https://github.com/seancorfield/boot-tools-deps) - plugin to use deps.edn dependencies from Boot
* [lein-tools-deps](https://github.com/RickMoynihan/lein-tools-deps) - plugin to use deps.edn dependencies from Leiningen
* [shadow-cljs](https://github.com/thheller/shadow-cljs) - ClojureScript compilation
* [depify](https://github.com/hagmonk/depify) - creates or updates a deps.edn file for existing Leiningen projects
* [meyvn](https://github.com/danielsz/meyvn) - a tools.deps interface to Maven for building, packaging etc
* [less4clj](https://github.com/Deraen/less4clj) - Less compiler for Clojure using Less4j
* [sass4clj](https://github.com/Deraen/sass4clj) - SASS compiler for Clojure using Libsass Java wrapper

## Packaging

* [clj.native-image](https://github.com/taylorwood/clj.native-image) - Generate GraalVM native images with Clojure CLI and deps.edn
* [badigeon](https://github.com/EwenG/badigeon) - Clojure build library using tools.deps
* [depstar](https://github.com/seancorfield/depstar) - Builds JARs, uberjars, does AOT, manifest generation, etc for tools.deps projects
* [Pack](https://github.com/juxt/pack.alpha) - Clojure project packager using tools.deps
* [revolt](https://github.com/mbuczko/revolt) - trampoline to building/packaging tasks, generates highly configurable [capsules](http://www.capsule.io/)
* [cambada](https://github.com/luchiniatwork/cambada) - a packager for Clojure supporting jar, uberjar and GraalVM's native-image
* [uberdeps](https://github.com/tonsky/uberdeps) - Uberjar builder for deps.edn projects
* [vulcan](https://github.com/omnyway-labs/vulcan) - Tool to simplify workflow with Git-based Clojure dependencies using clojure.tools.deps

## Continuous Integration
* [DeLaGuardo/setup-clojure](https://github.com/DeLaGuardo/setup-clojure) - a GitHub Action step

## Versioning and Releasing

* [Metav](https://github.com/jgrodziski/metav) - Deduce version from git state and release Clojure project based on tools.deps (check clean state of repo, bump version, tag, push)
* [garamond](https://github.com/workframers/garamond) - post-processes generated `pom.xml` files with version numbers from git tags

## Testing

* [test-runner](https://github.com/cognitect-labs/test-runner) - Clojure test runner based on deps.edn
* [cljs-test-runner](https://github.com/Olical/cljs-test-runner) - ClojureScript test runner based on deps.edn
* [Kaocha](https://github.com/lambdaisland/kaocha) - Full featured test runner

## Deps management

* [antq](https://github.com/liquidz/antq) - Point out your outdated dependencies.
* [Depot](https://github.com/Olical/depot) - Find newer versions of your deps
* [find-deps](https://github.com/hagmonk/find-deps) - Find and add deps using the Clojars and Maven search APIs
* [deps-ancient](https://github.com/slipset/deps-ancient/) - tells you if your `deps.edn` contains outdated deps
* [tools.deps.graph](https://github.com/clojure/tools.deps.graph) - create dependency graphs for your `deps.edn`
* [deps-try](https://gitlab.com/eval/deps-try) - quickly try out dependencies on rebel-readline
* [vizns](https://github.com/SevereOverfl0w/vizns) - visualize the relationships between namespaces and dependencies
* [morpheus](https://github.com/benedekfazekas/morpheus) - visualize dependency graphs of variables

## Runtimes

* [Planck](http://planck-repl.org) - self-hosted ClojureScript REPL with `plk` analog of `clj`
* [ohmyclj](https://gitlab.com/eval/ohmyclj/) - dev/test/run standalone Clojure scripts with ease
* [deps.clj](https://github.com/borkdude/deps.clj/) - a port of the `clojure` bash script to Clojure

## Deployment

* [Datomic Ions](https://docs.datomic.com/cloud/ions/ions.html) - deploy Clojure code to an autoscalable Datomic cluster in AWS
* [deps-deploy](https://github.com/slipset/deps-deploy) - A Clojure library to deploy your stuff to clojars
* [s3-mvn-upload](https://github.com/kennyjwilli/s3-mvn-upload) - Deploy a JAR file to a S3 Maven repository

## Calling lein from clj

* https://github.com/oakes/full-stack-clj-example

## Configuration and Environment Variables

* [clj-config](https://gitlab.com/orangefoxcollective/clj-config) - A Clojure library for managing configuration and environment variables

## Migrations

* [clj-migratus](https://gitlab.com/orangefoxcollective/clj-migratus) - A command line tool for managing migrations with Migratus