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
- Lombok (for boilerplate reduction)
- JUnit 5, Mockito, AssertJ (for testing)
- Semantic Release automation (release-please)


## Semantic Release

Automated releases are managed via [release-please](https://github.com/googleapis/release-please) using the `release-please-config.json` file.

### Semantic Release Process

- **Release Creation:**
  - The initial PR does not publish the release immediately; it prepares the repository for release and may include a snapshot version.
  - When changes are merged to the repository, release-please automatically creates another Pull Request (PR) proposing a new release. This PR includes updates to the changelog and bumps the version according to semantic commit messages.
  - **Important:** You must merge the second PR to complete the release process and ensure the repository is up-to-date with the latest published version.
- **Snapshot Management:**
  - Snapshot versions are used for ongoing development. Only after merging the release PR does the version get finalized and published. 
- **Artifact Publishing:**
  - Each module (folder) is released independently, allowing multiple artifacts to be published from the same repository.
