# Release

- Ensure the [CHANGELOG](./CHANGELOG.md) is up-to-date.

- If this release is a major version, update all the example YAML in the
  [README](./README.md), e.g. `2.0.0` would need `@v1` -> `@v2`.

- All contributions currently go to the `develop` branch. To make a new
  release, checkout to the `main` branch and merge with `develop` and then proceed
  with the release process.

```bash
git checkout develop
git pull origin develop
git checkout main
git pull origin main
git merge develop
git push origin main
```

- Create a new named tag:

```bash
git tag -a vX.Y.Z -m 'Release version vX.Y.Z'
```

Replace `X.Y.Z` by the appropriate version number.

- Point the old `vX` tag to latest `vX.Y.Z` tag:

```bash
git checkout main
git tag -d vX
git push origin :refs/tags/vX
git tag -a vX -m 'Release version vX.Y.Z'
git push origin --tags
git push origin main
```

Replace `X.Y.Z` by the appropriate version number.

