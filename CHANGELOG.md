# CHANGELOG

## [v2.1.0] (2025-06-04)

- [#33] add an option to mark the registered version as release
- [#35] add an option to skip install latch with pip 
- [#32] fix link to the logo in the README
- [#32] fix the release workflow 
- [#31] add a GHA workflow to keep the readme up-to-date
- [#30] add a release workflow (#30)
- adding back in missing commits from v1.1.0
  - [#18] Support registering a Snakefile for Snakemake
  - [#18] Fix disabling the auto version register option

[v2.1.0]: https://github.com/fulcrumgenomics/setup-latch/releases/tag/v2.1.0

## [v2.0.0] (2025-03-18)

This release provides upport for latch 2.57.2 and later.  Earlier releases of latch may work, but are unsupported.

* [#26] Disable local registration (`register-remote: false`).  See: https://github.com/latchbio/latch/issues/534.
* [#26] Fix `register-remote: false` (requires --no-remote).  In latch 2.19.7, `latch register --remote` became the default.
* [#26] Update the pattern to match log for already registered workflows.  This matches latch 2.57.2 and above.
* [#26] Add a GHA to test registration
* [#26] Install latch prior to tests

[v2.0.0]: https://github.com/fulcrumgenomics/setup-latch/releases/tag/v2.0.0

## [v1.1.2] (2025-03-18)

* [24] update location of the banner

[v1.1.2]: https://github.com/fulcrumgenomics/setup-latch/releases/tag/v1.1.2

## [v1.1.1] (2025-03-18)

* [#21] migrate ubuntu-latest to ubuntu-24.04
* [#22] add fulcrum genomics more prominently
* [#23] add banner, better logging, and log grouping

[v1.1.1]: https://github.com/fulcrumgenomics/setup-latch/releases/tag/v1.1.1

## [v1.1.0] (2024-05-20)

- [#18] Support registering a Snakefile for Snakemake
- [#18] Fix disabling the auto version register option

[v1.1.0]: https://github.com/fulcrumgenomics/setup-latch/releases/tag/v1.1.0

## [v1.0.8] (2023-11-12)

- [#15] Fix registered version

[v1.0.8]: https://github.com/fulcrumgenomics/setup-latch/releases/tag/v1.0.8

## [v1.0.7] (2023-06-26)

- [#8] Update example 2 in the README
- [#12] Add post-latch registration step
- [#14] Update ssh permissions in action 

[v1.0.7]: https://github.com/fulcrumgenomics/setup-latch/releases/tag/v1.0.7

## [v1.0.6] (2023-05-16)

- [#6] Add register-version to the outputs

[v1.0.6]: https://github.com/fulcrumgenomics/setup-latch/releases/tag/v1.0.6

## [v1.0.5] (2023-05-16)

- [#7]: Upgrade latch when using the latest version
- [#5]: Fix link to the action.yaml in the README

[v1.0.5]: https://github.com/fulcrumgenomics/setup-latch/releases/tag/v1.0.5

## [v1.0.4] (2023-05-15):

- [#2] Bugfix: fix all `if` conditions in actions.yaml

[v1.0.4]: https://github.com/fulcrumgenomics/setup-latch/releases/tag/v1.0.4

## [v1.0.3] (2023-05-15)

- Update name from "Setup Latch SDK" to "Setup Latch"

[v1.0.3]: https://github.com/fulcrumgenomics/setup-latch/releases/tag/v1.0.3

## [v1.0.2] (2023-05-15)

- [#1] Add the ability to register your local workflow. Add a github workflow
  for Example 1.

[v1.0.2]: https://github.com/fulcrumgenomics/setup-latch/releases/tag/v1.0.2

## [v1.0.1] (2023-05-15)

### Features

- first official release!

[v1.0.1]: https://github.com/fulcrumgenomics/setup-latch/releases/tag/v1.0.1
