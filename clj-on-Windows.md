Currently, `clj` on Windows is in an alpha state. Please try it and provide feedback in the [TDEPS](https://dev.clojure.org/jira/browse/TDEPS) jira or on #clj-on-windows room on [Clojurians slack](http://clojurians.net/).

## Install

First, download the latest version of the installer:

* https://download.clojure.org/install/win-install-1.10.1.489.ps1

When you run the installer, you will be prompted with several possible install locations:

```
PS Y:\Downloads> .\win-install-1.10.1.489.ps1
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

## Run
If you are using Windows PowerShell, invoke via `clj` or `clojure`.

If you need to run outside powershell, for example from the old Windows Command Prompt or [Git Bash](https://gitforwindows.org/), try:
```
powershell -command clj 
```
With command line argument:
```
powershell -command clj '-J"-Dfile.encoding=UTF-8"'
```
### Escaping Quotes
Escaping quotes can be a bit tricky. Here is the same command in different shells:

PowerShell 
```
clj -Sdeps '{:deps {viebel/klipse-repl {:mvn/version ""0.2.3""}}}' -m klipse-repl.main
```
Command Prompt 
```
powershell -command clj -Sdeps '{:deps {viebel/klipse-repl {:mvn/version """"""0.2.3""""""}}}' -m klipse-repl.main
```  
Git Bash 
```
powershell -command 'clj -Sdeps "{:deps {viebel/klipse-repl {:mvn/version """"0.2.3""""}}}" -m klipse-repl.main'
```

## Known issues

### Install fails due to permission errors

You can use the following command to allow execution of external scripts for the current user:

```Set-ExecutionPolicy RemoteSigned -Scope CurrentUser```

Please make sure you understand the ramifications of this before running.

If the above does not work for you, you might want to try:

```powershell.exe -noprofile -executionpolicy bypass -file .\win-install-1.10.1.489.ps1```

### Install fails in zip expansion

This seems to happen sometimes with an error like:

```
New-Object : Exception calling ".ctor" with "3" argument(s): "End of Central Directory record could not be found."
```

This might be a corrupted download (need better info on this) - try running it again.

### Quoted strings in -Sdeps argument not handled correctly

See: [TDEPS-121](https://dev.clojure.org/jira/browse/TDEPS-121)

### Long classpath

If your dependencies create a long classpath (~8k characters), you will exceed the Windows command-line length limit. The best option is probably to reduce the path to your local Maven repository, which is typically at $HOME/.m2/repository. 

The local repository location to use can be overridden by creating or modifying the file at $HOME/.clojure/deps.edn:

```clojure
{:mvn/local-repo "/path/to/repo"}
```

The local-repo directory is included in the path to every downloaded dependency so shortening that can have a significant impact on classpath line length.

See:  [TDEPS-120](https://dev.clojure.org/jira/browse/TDEPS-120)

## Questions

We seek your feedback on the best way to integrate the Windows install into your development environment. What's important to you? Self-executing installer? Chocolatey package? Powershell module? Please let us know.

* Scoop is another option that people seem to like -- see https://github.com/littleli/scoop-clojure as an example of how it could be packaged for Scoop (that depends on this wiki page existing and containing the latest version number for the Powershell installer!).
