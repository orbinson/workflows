# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

- Upload AEM content packages in target folders

## [0.0.2] - 2024-09-19

### Changed

- Bump versions of actions to `actions/checkout@v4` and `actions/setup-java@v4`
- Change maven release secret names
- Add `java-version` input work `AEM Maven Build` and `Maven Release` workflow

## [0.0.1] - 2024-09-18

### Added

- AEM Maven Build workflow to build AEM projects based on the [AEM Project Archetype](https://github.com/adobe/aem-project-archetype)
- Maven Release workflow to release artifacts a Maven
- GitHub Release workflow to release code as a GitHub release
- Documentation how to use the workflows

[unreleased]: https://github.com/orbinson/workflows/compare/0.0.2...HEAD
[0.0.2]: https://github.com/orbinson/workflows/compare/0.0.1...0.0.2
[0.0.1]: https://github.com/orbinson/workflows/compare/e94feb18236bbf5ad86a4d0acfe3c473289fa53d...0.0.1
