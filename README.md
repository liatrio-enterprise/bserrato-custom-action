# github-actions-template
[![Test](https://github.com/liatrio/github-actions-template/actions/workflows/test.yml/badge.svg)](https://github.com/liatrio/github-actions-template/actions/workflows/test.yml)
[![semantic-release: angular](https://img.shields.io/badge/semantic--release-angular-e10079?logo=semantic-release)](https://github.com/semantic-release/semantic-release)

> ## Template Usage
> This repo is meant to help kickstart custom, reusable Actions. By sourcing
> repos from this template developers are encouraged
> to follow certain standards:
> - Linting job(s) for checking project files for syntax/formatting errors
> - Testing job(s) for verifying new changes don't break functionality
> - A Release workflow for creating automated, versioned releases of Actions
> - Usage documentation clearly visible via the `README.md`
>
> ### Developer TODOs
> - Populate the sections of this `README.md` with
> information specific to your new Action.
>
> ### Other Action Types
>If you'd like to create Docker or JavaScript actions, checkout these official
> templates from GitHub:
> - [Docker Action](https://github.com/actions/hello-world-docker-action)
> - [JavaScript Action](https://github.com/actions/hello-world-javascript-action)
>
> **Please remove this section after creating your new repo with your template
> and completing the Developer TODOs section!**

Prints a simple message to the console. It's primary purpose is to serve as an
example for how to create and release a custom Composite GitHub Action.

## Usage

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Custom Action
        uses: your-org-name/action-template@v1
```

| Input         | Description                                         | Required | Default                                     |
|---------------|-----------------------------------------------------|----------|---------------------------------------------|
| `target`      | Value to use when printing 'hello <target>' message |  false   | world                                       |

| Output | Description |
|--------|-------------|
| `N/A`  | `N/A`       |

## Contributing

This project
uses [semantic-release](https://github.com/semantic-release/semantic-release)
and [conventional commits](https://github.com/semantic-release/semantic-release/#commit-message-format)
to help automate the release process. In order to track changes use the
following commit formats to track changes according to semantic versioning
standards.

| Commit message                                                                                                                                                                           | Release type                                                                                                  |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
| `fix: stop graphite breaking when too much pressure applied`                                                                                                                             | (Patch) Fix Release                                                                                           |
| `feat: add 'graphiteWidth' option`                                                                                                                                                       | (Minor) Feature Release                                                                                       |
| `perf: remove graphiteWidth option`<br/><br/>`BREAKING CHANGE: The graphiteWidth option has been removed.`<br/>`The default graphite width of 10mm is always used for performance reasons.` | (Major) Breaking Release <br/> (Note that the `BREAKING CHANGE:` token must be in the footer of the commit) <br/><br/> Where commit message format is : <br/>[type]: [subject]<br/>[BLANK LINE]<br/>[body] <-- not required<br/>[BLANK LINE]<br/>[footer] |

Once changes are merged via Pull Request or direct commit to `main`, the
[release workflow](.github/workflows/release.yml) will analyze commits,
calculate the next version, and publish a new Release to GitHub.

### Git Hooks

In order to prevent commits with breaking code, the `hooks/` directory has
been included to run `pre-commit` checks against your local code. This will
run:

- [yamllint](https://github.com/adrienverge/yamllint#installation)
- [markdownlint](https://github.com/igorshubovych/markdownlint-cli#installation)
- [actionlint](https://github.com/rhysd/actionlint/blob/main/docs/install.md)

To configure your local repository to use these Git Hooks run `git config core.hooksPath hooks/`.
