# `fulcrumgenomics/setup-latch`

This action sets up the [`latch`](https://github.com/latchbio/latch) CLI and SDK.
Visit https://docs.latch.bio to learn more about `latch`.

By default, this action will setup ssh config in `~/.ssh/config` for `latch` commands that require ssh by disabling strict host key checking (`StrictHostKeyChecking No` for all hosts in the `~/.ssh/config`).

The action will optional add the provided latch workspace identifier and token to `~/.latch/workspace` and `~/.latch/token` files respectively.
This is used when registering your local workflow code to Latch (see the `register*` inputs).
See https://console.latch.bio/settings/developer.

Finally, the `latch` package is installed.

## Inputs and outputs

For a full list of available _inputs_ and _outputs_ for this action see
[action.yaml](action.yaml).

## Usage example

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
        uses: fulcrumgenomics/setup-latch@v1
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
        uses: fulcrumgenomics/setup-latch@v1
        with:
            workspace: ${{ secrets.LATCH_WORKSPACE }}
            token: ${{ secrets.LATCH_TOKEN }}
            register: true
      - run: echo latch version ${{ steps.latch.outputs.register-version }}
        shell: bash
```
