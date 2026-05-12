# setup-c3

GitHub Action for installing the [C3 compiler](https://github.com/c3lang/c3c) in a workflow and adding `c3c` to `PATH`.

## Usage

```yaml
name: Build

on:
  push:
  pull_request:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v6

      - name: Setup C3
        uses: jotrorox/setup-c3@v1

      - name: Build
        run: c3c build
```

By default this installs the latest C3 prerelease/nightly.

## Inputs

| Input | Default | Description |
| --- | --- | --- |
| `version` | `nightly` | C3 release to install. Use `nightly`, `latest`, or a specific tag such as `v0.7.11`. |
| `build` | `release` | Artifact build to install. Use `release` or `debug`. |

## Outputs

| Output | Description |
| --- | --- |
| `c3c-path` | Absolute path to the installed compiler executable. |
| `version` | Installed compiler version string. |
| `release-tag` | C3 release tag that was installed. |

## Examples

Install the latest stable release:

```yaml
- uses: jotrorox/setup-c3@v1
  with:
    version: latest
```

Install a specific release:

```yaml
- uses: jotrorox/setup-c3@v1
  with:
    version: v0.7.11
```

Install the debug artifact:

```yaml
- uses: jotrorox/setup-c3@v1
  with:
    build: debug
```
