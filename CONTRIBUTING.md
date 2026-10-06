# How to Contribute to the Modpack

[**Chinese**](/docs/CONTRIBUTING_zh_cn.md) | [**English**](/CONTRIBUTING.md)

Thank you for your interest in contributing to GregTech Lite and its addon mods. This document is intended for beginners and first-time contributors. By participating, you agree to follow the [Code of Conduct](/CODE_OF_CONDUCT.md).

## Table of Contents

- [Before You Start](#before-you-start)
- [How to Contribute](#how-to-contribute)
  - [Report a Bug](#report-a-bug)
  - [Suggest an Improvement](#suggest-an-improvement)
  - [Code Contributions](#code-contributions)
  - [Documentation and Localization](#documentation-and-localization)
- [Pull Request](#pull-request)
- [Branching Strategy](#branching-strategy)
- [Commit Messages](#commit-messages)
- [Code Style](#code-style)
- [Setting Up the Development Environment](#setting-up-the-development-environment)
- [Review and Merge](#review-and-merge)
- [License](#license)
- [Questions](#questions)

## Before You Start

Before contributing, please:

- Read the [Code of Conduct](/CODE_OF_CONDUCT.md).
- Search existing issues and pull requests to avoid duplicates.
- For larger changes, open an issue or discussion first so maintainers can give feedback.
- Keep changes focused. A pull request should solve only one problem or implement one feature.
- Be respectful and patient during review.

## How to Contribute

First confirm the type of contribution you want to make, then read the corresponding section below.

### Report a Bug

Bug reports are welcome. Please fill in the corresponding issue template in the Issues section first. All modpack bug reports are centralized in this repository, not in the issue tracker of our [Core Mod](https://github.com/GregTechLite/GregTech-Lite-Core); that area is for developers and contributors only.

If logs are long, use a paste service such as GitHub Gist or Pastebin; do not paste the full log directly into the issue.

### Suggest an Improvement

Feature suggestions and balance discussions are welcome. Please fill in the corresponding issue template in the Issues section first.

A good suggestion should include:

- The problem or need you encountered.
- Your proposed solution.
- Use cases and expected behavior.
- Possible alternatives.
- Impact on progression, balance, or compatibility.
- Whether you are willing to implement it.

### Code Contributions

Before writing code:

- For larger changes, discuss the design in an issue or discussion first.
- Follow the existing code style and project structure.
- Keep changes focused and avoid unrelated refactoring.
- Add or update tests if applicable.
- Update documentation and localization files as needed.
- Unless the project explicitly requires it, do not commit generated files, IDE files, or local environment files.
- Before opening a pull request, make sure the project builds successfully.

### Documentation and Localization

Documentation and localization contributions are equally valuable.

- Fix typos, unclear wording, and outdated information.
- Keep translation terminology consistent.
- When adding or modifying user-facing text, update the relevant language files whenever possible.
- Do not reformat unrelated documentation.

## Pull Request

Unless otherwise specified by maintainers, all pull requests should target the `main` branch.

Pull request titles must use the following format:

```text
<type>: <Summary>
```

Available types:

- `feat`
- `refactor`
- `chore`
- `build`
- `ci`
- `fix`
- `docs`

Rules:

- The type must be one of the allowed types above.
- The type is followed by a colon and a space: `: `.
- The summary part starts with a capital letter.
- Scopes are not allowed. For example, `feat(ui): Add screen` is not allowed.
- Do not add punctuation at the end of the title.

Examples:

```text
feat: Add new machine configuration
fix: Make circuit recipe correct
refactor: Clean up recipe registration
```

A pull request should:

- Have a clear title that follows the format above.
- Explain what was changed, why it was changed, and how it was tested.
- Link related issues, for example `Closes #123`.
- Focus on a single topic.
- Pass CI/CD checks.
- Respond to review comments and make relevant changes based on them.

Pull request checklist:

- [ ] I have read `CONTRIBUTING.md` and `CODE_OF_CONDUCT.md`.
- [ ] My branch is based on the latest `main`.
- [ ] I did not work directly on `main`.
- [ ] I used the correct branch naming rule.
- [ ] I did not reuse an old branch.
- [ ] I ran the build or relevant tests.
- [ ] I updated documentation or localization if needed.
- [ ] My changes are focused and do not include unrelated modifications.
- [ ] My PR title follows the required format.
- [ ] My commit messages follow the required format.

## Branching Strategy

The default branch is `main`. Since `main` should remain stable, do not push directly to `main`. All pull requests target `main`.

### Force Push

Force pushes are generally not allowed. Only people with maintainer permission may perform force pushes, and only when necessary. Do not rewrite shared history. If you need to update a pull request, add new commits or merge the latest `main` into your branch instead of force pushing.

### If You Are a Member

If you have member permission for the repository:

- Create a new branch from the latest `main`.
- The branch naming rule is `id/xxx`, for example: `ms/ui-rework`.
- Push the branch and open a pull request to `main`.
- Do not work directly on `main`.

Example:

```bash
git switch main
git pull
git switch -c ms/ui-rework
# make changes
git push -u origin ms/ui-rework
```

### If You Are an External Contributor

If you do not have member permission:

- Fork the repository.
- Do not work directly on the `main` branch of your fork.
- Keep your fork's `main` clean and sync it with the upstream repository regularly.
- Before each contribution, sync your fork's `main` with upstream `main`, then create a new branch based on it.
- Branch names in your fork do not need a prefix; use `xxx` directly, for example: `ui-rework`.
- Do not reuse the same branch to submit multiple pull requests.
- After a pull request is merged or closed, sync your fork and create a new branch for the next contribution.
- Open a pull request from your branch to upstream `main`.

Example:

```bash
git remote add upstream <upstream-repo-url>
git fetch upstream
git switch main
git merge --ff-only upstream/main
git push origin main
git switch -c ui-rework
# make changes
git push -u origin ui-rework
```

## Commit Messages

Commit messages in a pull request must follow these rules:

- Use all lowercase letters.
- Do not add punctuation.
- Do not use type prefixes such as `feat:` or `fix:`.
- Keep them short and descriptive.

Examples:

```text
add new machine configuration
fix circuit recipe
update contribution guide
```

Note: PR titles use the `<type>: <Summary>` format, but commit messages do not use a type prefix.

## Code Style

- Follow the project's existing style.
- If the project provides formatter, lint, or Checkstyle configuration, use them.
- Do not reformat unrelated files.
- Keep imports, naming, and formatting consistent with nearby code.
- Keep localization keys consistent.
- Avoid wildcard imports unless the project already uses them.

## Setting Up the Development Environment

The exact setup depends on the part you are developing. Always check the `README` for the required JDK version, Gradle version, and run instructions.

General steps:

1. Install the JDK version required by the project.
2. Install an IDE, such as IntelliJ IDEA.
3. Clone the repository.
4. Import the project as a Gradle project.
5. Build the project.
6. If applicable, run the client or server for testing.
7. If you forked the repository, add the upstream remote.

Example:

```bash
git clone <repo-url>
cd GregTech-Lite
./gradlew build
```

Common run tasks, if available:

```bash
./gradlew runClient
./gradlew runServer
```

On Windows, use `gradlew.bat` instead of `./gradlew`.

If you only modify modpack content, follow the instructions in the Modpack project's `README` or documentation to test the modpack in a launcher or development instance.

## Review and Merge

Maintainers review pull requests. During review:

- Respond to feedback in a timely manner.
- Unless asked otherwise, make changes in new commits.
- After addressing comments, request review again.
- Keep discussions focused and respectful.

When a pull request is approved and CI/CD passes, it may be merged. The final merge strategy is decided by maintainers, and not all pull requests are guaranteed to be accepted.

## License

Your contributions will be licensed under the same license as the project. See the `LICENSE` file for details. If you contribute content that requires additional attribution, it will be placed in the `NOTICE` file.

## Questions

If you have questions, you can use Issues or Discussions, or ask in the project community channels. Please search existing discussions before asking.
