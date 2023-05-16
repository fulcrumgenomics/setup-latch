# `fulcrumgenomics/setup-latch`

This action sets up the [`latch`](https://github.com/latchbio/latch) CLI and SDK.

By default, this action will setup ssh config in `~/.ssh/config` for `latch` commands that require ssh by disabling strict host key checking (`StrictHostKeyChecking No` for all hosts in the `~/.ssh/config`).

The action will optional add the provided latch workspace identifier and token to `~/.latch/workspace` and `~/.latch/token` files respectively.

Finally, the `latch` package is installed.

## Inputs and outputs

For a full list of available _inputs_ and _outputs_ for this action see
[action.yml](action.yml).

## Usage example

```yaml
jobs:
  setup-latch-job:
    runs-on: ubuntu-latest
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

