# `fulcrumgenomics/setup-latch`

[![Example 1: Basic usage](https://github.com/fulcrumgenomics/setup-latch/actions/workflows/example-1.yml/badge.svg?branch=main)](https://github.com/fulcrumgenomics/setup-latch/actions/workflows/example-1.yml)
[![Test: latch register](https://github.com/fulcrumgenomics/setup-latch/actions/workflows/test-register.yml/badge.svg?branch=main)](https://github.com/fulcrumgenomics/setup-latch/actions/workflows/test-register.yml)
[![License](http://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/fulcrumgenomics/setup-latch/blob/main/LICENSE)
[![Latch version](https://img.shields.io/badge/latch->=2.57.2-violet)](https://pypi.org/project/latch)


This action sets up the [`latch`](https://github.com/latchbio/latch) CLI and SDK.

<p>
<a href="https://fulcrumgenomics.com"><img src=".github/logos/fulcrumgenomics.svg" alt="Fulcrum Genomics" height="100"/></a>
</p>

[Visit us at Fulcrum Genomics](https://www.fulcrumgenomics.com) to learn more about how we can power your Bioinformatics with setup-latch and beyond.

<a href="mailto:contact@fulcrumgenomics.com?subject=[GitHub inquiry]"><img src="https://img.shields.io/badge/Email_us-brightgreen.svg?&style=for-the-badge&logo=gmail&logoColor=white"/></a>
<a href="https://www.fulcrumgenomics.com"><img src="https://img.shields.io/badge/Visit_Us-blue.svg?&style=for-the-badge&logo=wordpress&logoColor=white"/></a>

Supports [latch version >= 2.57.2](https://pypi.org/project/latch).

Visit https://docs.latch.bio to learn more about `latch`.

By default, this action will setup ssh config in `~/.ssh/config` for `latch` commands that require ssh by disabling strict host key checking (`StrictHostKeyChecking No` for all hosts in the `~/.ssh/config`).

The action will optional add the provided latch workspace identifier and token to `~/.latch/workspace` and `~/.latch/token` files respectively.
This is used when registering your local workflow code to Latch (see the `register*` inputs).
See https://console.latch.bio/settings/developer.

Finally, the `latch` package is installed.

## Inputs and outputs

For a full list of available _inputs_ and _outputs_ for this action see
[action.yaml](action.yaml).

## Usage

### Example 1: Basic usage

[![Example 1: Basic usage](https://github.com/fulcrumgenomics/setup-latch/actions/workflows/example-1.yml/badge.svg)](https://github.com/fulcrumgenomics/setup-latch/actions/workflows/example-1.yml)

This example shows how to install the latest version of `latch` and echo the version installed.

```yaml
jobs:
  setup-latch-job:
    runs-on: ubuntu-24.04
    name: A job to setup latch
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: '3.10'
      - id: latch
        uses: fulcrumgenomics/setup-latch@v2
      - run: echo latch version ${{ steps.latch.outputs.latch-version }}
        shell: bash
```

### Example 2: Register your local workflow code to Latch

This example shows how to register your local workflow code to Latch.
The `workspace` and `token` are required and accept the workspace identifier and developer token respectively.
In this example, they are stored as [encrypted secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets).

```yaml
jobs:
  setup-latch-job:
    runs-on: ubuntu-24.04
    name: A job to register a latch workflow
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: '3.10'
      - id: latch
        uses: fulcrumgenomics/setup-latch@v2
        with:
            workspace: ${{ secrets.LATCH_WORKSPACE }}
            token: ${{ secrets.LATCH_TOKEN }}
            register: true
      - run: echo latch version ${{ steps.latch.outputs.register-version }}
        shell: bash
```

<!-- start usage -->

### Inputs

```yaml
- uses: fulcrumgenomics/gha-timer@v1
  with:
    # The version of latch to install (see https://pypi.org/project/latch/).
    # Default: latest
    latch-version: ''

    # Workspace id (see ~/.latch/workspace), typically numeric.
    # Default: 
    latch-workspace: ''

    # Latch token (see ~/.token). Please store this in a secret!
    # Default: 
    latch-token: ''

    # Set up the ~/.ssh directory.
    # Default: true
    ssh-config: ''

    # Register repository workflow code to Latch. Visit docs.latch.bio to learn more.
    # Default: false
    register: ''

    # The relative path to the root of the package to register
    # Default: .
    register-pkg-root: ''

    # Use a remote server to build workflow.
    # Default: true
    register-remote: ''

    # Whether to automatically bump the version of the workflow each time register is
    # called.
    # Default: false
    register-disable-auto-version: ''

    # Path to the Snakefile (for Snakemake) to register
    # Default: 
    register-snakefile: ''

    # Whether the workflow should fail if the worfklow is already registered.
    # Default: false
    already-registered-do-not-fail: ''

    # Whether to mark the registered workflow as a release (must set `register` to
    # 'true').
    # Default: false
    mark-as-release: ''

    # Whether to skip installing the latch CLI. If true, the latch CLI must be
    # available via the shell (bash).
    # Default: false
    skip-install: ''
```

### Outputs

There are currently no outputs

<!-- end usage -->
