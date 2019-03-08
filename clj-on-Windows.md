Currently, `clj` on Windows is in an alpha state. Please try it and provide feedback in the [TDEPS](https://dev.clojure.org/jira/browse/TDEPS) jira or on #clj-on-windows room on Clojurians slack.

## Install

First, download the latest version of the installer:

* https://download.clojure.org/install/win-install-1.10.0.434.ps1

When you run the installer, you will be prompted with several possible install locations:

```
PS Y:\Downloads> .\win-install-1.10.0.434.ps1
Downloading Clojure tools
WARNING: Clojure will install as a module in your PowerShell module path.

Possible install locations:
  1) \\Drive\Home\Documents\WindowsPowerShell\Modules
  2) C:\Program Files\WindowsPowerShell\Modules
  3) C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\
Enter number of preferred install location: 1

Cleaning up existing install
Installing PowerShell module
Removing download
Clojure now installed. Use "clj -h" for help.
```

When choosing which location to install consider these tradeoffs:
* #1 can be installed without admin privileges but will create a directory in Documents
* #2 and 3 should probably be run only if you have admin privileges

## Known issues

### Install fails due to permission errors

You can use the following command to allow execution of external scripts for the current user:

```Set-ExecutionPolicy RemoteSigned -Scope CurrentUser```

Please make sure you understand the ramifications of this before running.

### Long classpath

If your dependencies create a long classpath (~8k characters), you will exceed the Windows command-line length limit. The best option is probably to reduce the path to your local Maven repository, which is typically at $HOME/.m2/repository. 

The local repository location to use can be overridden by creating or modifying the file at $HOME/.clojure/deps.edn:

```clojure
{:mvn/local-repo "/path/to/repo"}
```

The local-repo directory is included in the path to every downloaded dependency so shortening that can have a significant impact on classpath line length.

## Questions

We seek your feedback on the best way to integrate the Windows install into your development environment. What's important to you? Self-executing installer? Chocolatey package? Powershell module? Please let us know.
