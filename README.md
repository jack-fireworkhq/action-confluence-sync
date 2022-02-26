 <!-- Space: Projects -->
<!-- Title: ActionConfluenceSync -->

<!--


  ** DO NOT EDIT THIS FILE
  **
  ** 1) Make all changes to `provision/generator/README.yaml`
  ** 2) Run`task readme` to rebuild this file.
  **
  ** (We maintain HUNDREDS of open source projects. This is how we maintain our sanity.)
  **


  -->

[![Latest Release](https://img.shields.io/github/release/hadenlabs/action-confluence-sync)](https://github.com/hadenlabs/action-confluence-sync/releases) [![Lint](https://img.shields.io/github/workflow/status/hadenlabs/action-confluence-sync/lint-code)](https://github.com/hadenlabs/action-confluence-sync/actions) [![Issues](https://img.shields.io/github/issues/hadenlabs/action-confluence-sync)](https://github.com/hadenlabs/action-confluence-sync/issues) [![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/pre-commit/pre-commit) [![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow)](https://conventionalcommits.org) [![KeepAChangelog](https://img.shields.io/badge/changelog-Keep%20a%20Changelog%20v1.0.0-orange)](https://keepachangelog.com)

# action-confluence-sync

action-confluence-sync for project

## Requirements

This is a list of plugins that need to be installed previously to enjoy all the goodies of this configuration:

- [gomplate](https://github.com/hairyhenderson/gomplate)
- [Docker](https://www.docker.com)
- [python](https://www.python.org)
- [taskfile](https://github.com/go-task/task)

## Usage

To use this action, make a file `.github/workflows/confluence.yml`. Here's a template to get started:

```yaml
name: confluence-sync

on:
  pull_request:
  push:
    branches: [main]

jobs:
  confluence:
    runs-on: ubuntu-20.04
    steps:
      - name: Check out a copy of the repo
        if: ${{ !env.ACT }}
        uses: actions/checkout@v2
        with:
          fetch-depth: 0

      - name: Get changed files
        id: changed-files
        uses: tj-actions/changed-files@v17.1
        with:
          files: |
            *.md
          files_ignore: |
            *.tpl.md

      - name: Sync confluence
        uses: hadenlabs/action-confluence-sync@0.0.0
        with:
          confluence_base_url: '${{ secrets.CONFLUENCE_BASE_URL }}'
          confluence_user: '${{ secrets.CONFLUENCE_USER }}'
          confluence_token: '${{ secrets.CONFLUENCE_ACCESS_TOKEN }}'
          files: '${{ steps.changed-files.outputs.all_changed_files }}'
```

## Help

**Got a question?**

File a GitHub [issue](https://github.com/hadenlabs/action-confluence-sync/issues).

## Contributing

See [Contributing](./docs/contributing.md).

## Module Versioning

This Module follows the principles of [Semantic Versioning (SemVer)](https://semver.org/).

Using the given version number of `MAJOR.MINOR.PATCH`, we apply the following constructs:

1. Use the `MAJOR` version for incompatible changes.
1. Use the `MINOR` version when adding functionality in a backwards compatible manner.
1. Use the `PATCH` version when introducing backwards compatible bug fixes.

### Backwards compatibility in `0.0.z` and `0.y.z` version

- In the context of initial development, backwards compatibility in versions `0.0.z` is **not guaranteed** when `z` is increased. (Initial development)
- In the context of pre-release, backwards compatibility in versions `0.y.z` is **not guaranteed** when `y` is increased. (Pre-release)

## Copyright

Copyright © 2018-2022 [Hadenlabs](https://hadenlabs.com)

## Trademarks

All other trademarks referenced herein are the property of their respective owners.

## License

The code and styles are licensed under the LGPL-3.0 license [See project license.](LICENSE).

## Don't forget to 🌟 Star 🌟 the repo if you like action-confluence-sync

[Your feedback is appreciated](https://github.com/hadenlabs/action-confluence-sync/issues)
