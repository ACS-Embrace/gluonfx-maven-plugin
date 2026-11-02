# Changelog

What each published version of Embrace's GluonFX plugin for Maven contains. Versions are
`major.minor.patch-embrace` (see "Versions and releases" in README.md): major when Embrace's builds
must change to use it, minor for a new feature they can take without changes, patch for fixes only.
The `-embrace` marker keeps our versions apart from Gluon's, which are published under the same name
(`com.gluonhq:gluonfx-maven-plugin`).

## 2.0.0-embrace

First version under this scheme; it replaces the `1.1.x-SNAPSHOT` versions.

**Based on** Gluon's plugin after its 1.0.27 release (development of 1.0.28). Gluon's later commits
only set version numbers, so there is nothing further to take.

- **Substrate:** uses Embrace's Substrate `1.0.0-embrace` by default (it was `0.1.31-SNAPSHOT` in
  1.1.23-SNAPSHOT, and the JDK 23 trial `0.1.32-SNAPSHOT` in 1.1.24-SNAPSHOT).
- **Publishing:** to Embrace's S3 repository, through the `release` profile only.
- The plugin's own code is unchanged from Gluon's.
