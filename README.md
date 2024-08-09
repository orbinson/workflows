# Reusable GitHub Workflows

To use the workflows defined in this repository you can [call](https://docs.github.com/en/actions/using-workflows/reusing-workflows) them in you project workflow jobs where `<worflow>` needs to be replaced with the yaml file name present in the [workflows](.github/workflows) folder.

```yml
jobs:
  call-workflow:
    uses: orbinson/workflows/.github/workflows/<workflow>.yml
```

## AEM Maven Build

The [aem-maven-build](.github/workflows/aem-maven-build) workflow uses a Java 11 environment and a build cache to perform a `mvn install`.

## GitHub Release

## Maven Release

The [maven-release](.github/workflows/maven-release) workflow uses a Java 11 environment and a build cache to perform to following actions

* Remove `SNAPSHOT` from the project version
* Update `CHANGELOG.md`
* Deploy to Maven repository
* Tag, commit and push stable version
* Create GitHub release with `CHANGELOG.md` and released artifacts
* Increment development version

The workflow allows to specify if you need to

* Release to the project Maven repository
* Create GitHub release
* Push changes

In order to use the workflow you need to set the following secrets

| secret | description |
|-|-|
| `MAVEN_USERNAME` | Username to deploy to maven repository |
| `MAVEN_PASSWORD` | Password to deploy to maven repository|
| `MAVEN_GPG_PASSPHRASE` | GPG passphrase to sign maven artifacts |
| `MAVEN_GPG_PRIVATE_KEY` | GPG private key to sign maven artifacts |
