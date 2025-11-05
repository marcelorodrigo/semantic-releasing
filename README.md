# Semantic Releasing

A multi-module Java project demonstrating semantic release automation for Spring Boot projects
that have different Java versions and/or Spring Boot versions.

It made possible to publish two artifacts in the same repository,
using modules instead of branches to manage different versions of
the same project.

Each version is split into its own module.

## Project Structure

- **semantic-releasing-spring-boot-3_4/**: Spring Boot 3.4, Java 21
- **semantic-releasing-spring-boot-3_5/**: Spring Boot 3.5, Java 21

## Technologies

- Java 21
- Spring Boot 3.4 & 3.5
- Maven
- Semantic Release automation (release-please)


## Semantic Release

Automated releases are managed via [release-please](https://github.com/googleapis/release-please) using the `release-please-config.json` file.

## 📦 Releases

### Releasing a package
This repository uses [release-please](https://github.com/googleapis/release-please) to create release PRs.

**Important:** All pull requests must use [Conventional Commit Messages](https://www.conventionalcommits.org/en/v1.0.0/) in their commit history.
This is required for release-please to correctly determine the next [semantic version](https://semver.org/) and generate changelogs.

release-please automates changelog and version updates, but actual publishing is handled via
[create-release-pr.yml](./github/workflows/create-release-pr.yml) workflow.

A typical flow from beginning to end looks like this:
1. You create a feature branch and make a PR from it, using semantic conventional commits
2. The PR is reviewed and merged
3. A release PR is automatically created
4. Release PR is also checked and merged
5. New versions of the changed modules will automatically be released

You can find the released packages for this repository on [GitHub](https://github.com/marcelorodrigo/semantic-releasing/packages).
