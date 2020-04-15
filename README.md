Parent POM
-------

## Purpose

Code reuse (build logic reuse) between child projects. 
Easier upgrading of all plugins.  

## Changelog

### 5.12
* New maven-forge-plugin with proper failsafe/surefire JAVA_HOME env var support (previous versions did not correctly hack this variable in failsafe)

### 5.10
* `slow` and `fast` modes.  **slow** is default, **fast** skips everything inessential to permit quick building.
* `-Dfast -DskipTest` is the fastest way to build a project using this parent.

### Migrating from previous versions
Any custom pom profile for fast/slow in a child project should mimic the `slow` profile definition in this project, 
so that a single `-Dfast` activates both child and parent.  See terracotta-platform for an example.

### 5.9
* `-DskipIts` is now supported in addition to `-DskipTests`

### 5.6
maven-forge-plugin with toolchains support replaces surefire and failsafe.

#### Migrating from previous versions
* Replace any mentions of surefire and failsafe with org.terracotta:maven-forge-plugin (do not specify version)
* Remove any of the above if they are not customizing configuration (plugin executions are already defined)
* Remove any property definitions that may unintentionally override this parent (eg `maven-forge-plugin.version`)


## Methodology

* Avoid unnecessary duplication in child poms.