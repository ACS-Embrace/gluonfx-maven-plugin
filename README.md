# GluonFX plugin for Maven

[![Maven Central](https://img.shields.io/maven-central/v/com.gluonhq/gluonfx-maven-plugin)](https://search.maven.org/search?q=g:com.gluonhq%20AND%20a:gluonfx-maven-plugin)
[![Github Actions](https://github.com/gluonhq/gluonfx-maven-plugin/actions/workflows/build.yml/badge.svg)](https://github.com/gluonhq/gluonfx-maven-plugin/actions/workflows/build.yml)
[![BSD-3 license](https://img.shields.io/badge/license-BSD--3-%230778B9.svg)](https://opensource.org/licenses/BSD-3-Clause)

GluonFX plugin for maven leverages GraalVM, OpenJDK and JavaFX 11+, 
by compiling into native code the Java Client application and all its required dependencies, 
so it can directly be executed as a native application on the target platform.

## Versions and releases (Embrace)

This is Embrace's copy of Gluon's plugin. It is versioned `major.minor.patch-embrace`, independently
of Gluon's numbering:

* **major** when Embrace's builds must change to use the release,
* **minor** for a new feature they can take without changes,
* **patch** for fixes only.

The `-embrace` marker matters: our releases are published under the same name as Gluon's
(`com.gluonhq:gluonfx-maven-plugin`), so the marker stops a build from picking up a Gluon release
of the same number. `CHANGELOG.md` lists what each version contains and which Substrate it uses.

* **The plugin decides the Substrate version** (`substrate.version` in `pom.xml`), so Embrace's
  APK build only names the plugin version.
* **Test builds** are versioned like `2.0.1-embrace-dev-<topic>` and installed to local Maven only
  (`mvn clean install`).
* **Releases** are published with the `release` profile, which holds the S3 repository: a plain
  `mvn deploy` has nowhere to publish to. The profile first refuses `-SNAPSHOT` and `-dev` versions,
  snapshot dependencies, and uncommitted changes. The plugin has no native code, so it can be
  published from any machine.
  1. Set the version (and `substrate.version` if it changes) in `pom.xml`, and add its entry to
     `CHANGELOG.md`, on `embrace_master`.
  2. Publish: `mvn -Prelease clean deploy` (needs the S3 credentials the wagon uses).
  3. Tag the commit with an annotated tag and push it, e.g.
     `git tag -a 2.0.0-embrace -m "2.0.0-embrace" && git push origin 2.0.0-embrace`.
* The jar's manifest carries `Implementation-Version` and `Git-Commit`.

Versions before 2.0.0-embrace were `1.1.x-SNAPSHOT`, which could change between builds.

## Requirements

Check the requirements for the [target platform](https://docs.gluonhq.com/#_platforms) before you get started.

## Getting started

Follow this [guide](https://docs.gluonhq.com/#_gluonfx_plugin_for_maven) on how to apply the plugin and use the different goals.

## Documentation and samples

Check the [documentation](https://docs.gluonhq.com/) for more details about the plugin and running the [samples](https://github.com/gluonhq/gluon-samples/).

## Issues and Contributions ##

Issues can be reported to the [Issue tracker](https://github.com/gluonhq/gluonfx-maven-plugin/issues)

Contributions can be submitted via [Pull requests](https://github.com/gluonhq/gluonfx-maven-plugin/pulls), 
providing you have signed the [Gluon Individual Contributor License Agreement (CLA)](https://cla.gluonhq.com).
