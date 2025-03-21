# Release

- Ensure the [CHANGELOG](./CHANGELOG.md) is up-to-date.

- Ensure that `package.json` and `package-lock.json` have the correct `version` property (use `npm version --no-git-tag-version X.Y.Z`).

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
