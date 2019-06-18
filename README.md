[![*nix build status][nix-build-image]][nix-build-url]
[![Windows build status][win-build-image]][win-build-url]
[![Tests coverage][cov-image]][cov-url]
![Transpilation status][transpilation-image]

# github-release-from-cc-changelog

Retrieve release notes from CHANGELOG.md (as generated by [standard-version](https://github.com/conventional-changelog/standard-version)) and post them to GitHub

## Installation

```bash
npm i -g github-release-from-cc-changelog
```

## Prerequisites

- Github url needs to be configured at package.json `repository` field
- [Create a new token](https://github.com/settings/tokens/new) and set your environment variable `CONVENTIONAL_GITHUB_RELEASER_TOKEN` to the token you just created. The scopes for the token you need is `public_repo` or `repo` (if you need to access private repos).
- Tags for given versions need to be pre-pushed to repository at GitHub

## Usage

### CLI

At package directory run:

```bash
github-release-from-cc-changelog <version>
```

e.g.

```bash
github-release-from-cc-changelog 1.0.0
```

#### Reseolve and publish notes for all versions

At package directory run:

```bash
github-release-all-from-cc-changelog
```

### Programmatically

```javascript
const releaseFromChangelog = require("github-release-from-cc-changelog");

releaseFromChangelog(packageDirectory, version).then(() => {
  console.log(`Successfully pushed release notes for version ${ version }`);
});
```

#### Reseolve and publish notes for all versions

```javascript
const releaseAllFromChangelog = require("github-release-from-cc-changelog/all");

releaseFromChangelog(packageDirectory).then(() => {
  console.log(`Successfully pushed and released notes for all versions`);
});
```

## Test

```bash
npm test
```

[nix-build-image]: https://semaphoreci.com/api/v1/medikoo-org/github-release-from-cc-changelog/branches/master/shields_badge.svg
[nix-build-url]: https://semaphoreci.com/medikoo-org/github-release-from-cc-changelog
[win-build-image]: https://ci.appveyor.com/api/projects/status/7hwt5m89ged5lm78?svg=true
[win-build-url]: https://ci.appveyor.com/api/project/medikoo/github-release-from-cc-changelog
[cov-image]: https://img.shields.io/codecov/c/github/medikoo/github-release-from-cc-changelog.svg
[cov-url]: https://codecov.io/gh/medikoo/github-release-from-cc-changelog
[transpilation-image]: https://img.shields.io/badge/transpilation-free-brightgreen.svg
