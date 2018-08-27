This is a page to collect tools that use or work with tools.deps.alpha (or the clojure tools).

## Project creation

* [clj-new](https://github.com/seancorfield/clj-new) - generate new project templates using just the `clj` command-line tool

## Lint tool integration

* [clj-check](https://github.com/athos/clj-check) - `lein check` alternative for Clojure CLI
* [cljfmt-runner](https://github.com/JamesLaverack/cljfmt-runner) — run cljfmt to find and/or fix code formatting issues

## Build tool integration

* [boot-tools-deps](https://github.com/seancorfield/boot-tools-deps) - plugin to use deps.edn dependencies from Boot
* [lein-tools-deps](https://github.com/RickMoynihan/lein-tools-deps) - plugin to use deps.edn dependencies from Leiningen
* [shadow-cljs](https://github.com/thheller/shadow-cljs) - ClojureScript compilation
* [depify](https://github.com/hagmonk/depify) - creates or updates a deps.edn file for existing Leiningen projects
* [meyvn](https://github.com/danielsz/meyvn) - a tools.deps interface to Maven for building, packaging etc

## Packaging

* [clj.native-image](https://github.com/taylorwood/clj.native-image) - Generate GraalVM native images with Clojure CLI and deps.edn
* [badigeon](https://github.com/EwenG/badigeon)
* [depstar](https://github.com/healthfinch/depstar) - clj-based uberjarrer
* [Pack](https://github.com/juxt/pack.alpha) - Clojure project packager using tools.deps
* [revolt](https://github.com/mbuczko/revolt) - trampoline to building/packaging tasks, generates highly configurable [capsules](http://www.capsule.io/)

## Testing

* [test-runner](https://github.com/cognitect-labs/test-runner) - Clojure test runner based on deps.edn
* [cljs-test-runner](https://github.com/Olical/cljs-test-runner) - ClojureScript test runner based on deps.edn

## Deps management

* [Depot](https://github.com/Olical/depot) - Find newer versions of your deps
* [find-deps](https://github.com/hagmonk/find-deps) - Find and add deps using the Clojars and Maven search APIs

## Runtimes

* [Planck](http://planck-repl.org) - self-hosted ClojureScript REPL with `plk` analog of `clj`

## Deployment

* [Datomic Ions](https://docs.datomic.com/cloud/ions/ions.html) - deploy Clojure code to an autoscalable Datomic cluster in AWS