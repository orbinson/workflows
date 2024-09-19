# Reusable GitHub Workflows

To use the workflows defined in this repository you
can [call](https://docs.github.com/en/actions/using-workflows/reusing-workflows) them in you project workflow jobs where
`<worflow>` needs to be replaced with the yaml file name present in the [workflows](.github/workflows) folder. A ref,
which in this example is the `main` branch, needs to be specific when calling workflows.

```yml
jobs:
  call-workflow:
    uses: orbinson/workflows/.github/workflows/<workflow>.yml@main
```

## AEM Maven Build

The [aem-maven-build](.github/workflows/aem-maven-build.yml) workflow uses a Java 11 environment and a build cache to
perform a `mvn install`.

**Example:**

```yml
jobs:
  call-workflow:
    uses: orbinson/workflows/.github/workflows/aem-maven-build.yml@main
```

## GitHub Release

The [github-release](.github/workflows/github-release.yml) workflow will create a GitHub release by performing the
following actions

* Update the `CHANGELOG.md` file where the `[Unreleased]` section is replaced with the provided `version` and a new
  `[Unreleased]` section is created
* Updated `CHANGELOG.md` is committed and tagged with the provided `version`
* A GitHub release is created version tag

The following **inputs** should be provided for the workflow

| Key       | Description                               |
|-----------|-------------------------------------------|
| `version` | Semantic version of release to be created |

**Example:**

```yml
jobs:
  call-workflow:
    uses: orbinson/workflows/.github/workflows/github-release.yml@main
    with:
      version: 1.0.0
```

## Maven Release

The [maven-release](.github/workflows/maven-release.yml) workflow uses a Java 11 environment and a build cache to
perform to following actions

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

| secret            | description                             |
|-------------------|-----------------------------------------|
| `username`        | Username to deploy to maven repository  |
| `password`        | Password to deploy to maven repository  |
| `gpg-passphrase`  | GPG passphrase to sign maven artifacts  |
| `gpg-private-key` | GPG private key to sign maven artifacts |

**Example:**

```yml
jobs:
  call-workflow:
    uses: orbinson/workflows/.github/workflows/maven-release.yml@main
    with:
      central: true
      github: true
      push: true
    secrets:
      username: ${{ secrets.SONATYPE_USERNAME }}
      password: ${{ secrets.SONATYPE_PASSWORD }}
      gpg-passphrase: ${{ secrets.GPG_PASSPHRASE }}
      gpg-private-key: ${{ secrets.GPG_PRIVATE_KEY }}
```
