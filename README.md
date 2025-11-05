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


## Conventional Commits

This project follows the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification for all commit messages.
Conventional commits enable automated semantic versioning and changelog generation. Each commit message should follow this format:

```
<type>(<scope>): <description>
[optional body]
```

### Commit Types

The specification defines two required types:

- **feat:** MUST be used when a commit adds a new feature to your application or library (triggers a **minor** version bump)
- **fix:** MUST be used when a commit represents a bug fix for your application (triggers a **patch** version bump)

Other types MAY be used (these are common conventions):

- **docs:** Documentation only changes
- **style:** Code style changes (formatting, missing semi-colons, etc.)
- **refactor:** Code changes that neither fix a bug nor add a feature
- **perf:** Performance improvements
- **test:** Adding or updating tests
- **chore:** Changes to the build process or auxiliary tools
- **build:** Changes to build system or dependencies
- **ci:** Changes to CI configuration files and scripts

### Breaking Changes

Breaking changes MUST be indicated in one of two ways:

1. **Using `!` before the colon:** Appending `!` after the type/scope (triggers a **major** version bump)
   ```
   feat!: send email notification on user signup
   feat(api)!: change response format
   ```

2. **Using `BREAKING CHANGE:` footer:** Including `BREAKING CHANGE:` in the commit footer (triggers a **major** version bump)
   ```
   feat: update configuration system
   
   BREAKING CHANGE: configuration file format changed from JSON to YAML
   ```

### Examples

```
feat(spring-boot-3_5): add new REST endpoint for user management

fix(spring-boot-3_4): correct validation logic in controller

docs: update README with release process
```

## 📦 Semantic Release Process

Automated releases are managed via [release-please](https://github.com/googleapis/release-please) using the `release-please-config.json` file. Release-please analyzes conventional commit messages to automatically determine version bumps and generate changelogs.

### How It Works

1. **Create a Feature Branch**
   - Create a feature branch from `master`
   - Make your changes with conventional commit messages
   - Open a pull request

2. **Merge Your PR**
   - After review and approval, merge your PR to `master`
   - Release workflow monitors all commits on the main branch

3. **Release PR Creation**
   - Release workflow automatically creates a release PR
   - This PR includes:
     - Version bumps based on conventional commits
     - Updated CHANGELOG.md files
     - Updated `pom.xml` versions
   - Review the proposed changes

4. **Merge Release PR**
   - Once approved, merge the release PR
   - This triggers the actual release process

5. **Artifact Publishing**
   - Each module is published independently to GitHub Packages
   - Multiple artifacts can be released from the same repository
   - Publishing is handled via the [create-release-pr.yml](./.github/workflows/create-release-pr.yml) workflow

### Finding Released Packages

You can find all released packages for this repository on [GitHub Packages](https://github.com/marcelorodrigo/semantic-releasing/packages).
