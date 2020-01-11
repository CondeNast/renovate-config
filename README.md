# CondeNast/renovate-config

This is a collection of [GitHub-hosted presets](https://docs.renovatebot.com/config-presets/#github-hosted-presets) for Renovate dependency bot.

## Usage

renovate.json

```
{
  "extends": [
    "github>CondeNast/renovate-config:unpublishSafe",
    "github>CondeNast/renovate-config:forceCondenastUpdates",
    "github>CondeNast/renovate-config:automergeMinor",
    "github>CondeNast/renovate-config:condenastStabilityDays",
    "github>CondeNast/renovate-config:dontAutomergeNode",
    "github>CondeNast/renovate-config:dontAutomergeTestFrameworks",
    "github>CondeNast/renovate-config:groupMinorUpdates(dependencies)"
  ]
}
```

## Presets

### `automergeMinor`

Enables automerge for non-major updates.

### `condenastStabilityDays`

If automerging is enabled, PRs for condenast packages will be created immediately but automerging will be delayed until 24 hours have passed. This allows for manual intervention if there is a problem with a release.

### `dontAutomergeNode`

Disables automerge for Node.js upgrades and also groups them together. This is helpful if you have multiple places where the Node.js version is set (e.g. multiple different Docker base images) and these don't always get release in sync with each other, so you have to wait for all of the new releases before you can merge them.

### `dontAutomergeTestFrameworks`

Disables automerge for testing frameworks. Upgrades to testing frameworks need to be validated manually to avoid false positive results.

### `forceCondenastUpdates`

Ensure PRs for condenast packages as soon as possible after publish.

### `groupMinorUpdates`

Groups minor dependency updates for non-condenast packages.

### `orgPackages`

Package filter for `@condenast` packages.

### `testFrameworks`

Package filters for automated test frameworks (e.g. `jest`, `nock`, `cypress`).

### `unpublishSafe`

Delays opening PRs for new dependencies by 24 hours to avoid build failure in the case where a package version gets unpublished by its author (packages cannot be unpublished after 24 hours).

NOTE: `unpublishSafe` doesn't work if you apply it do dependency groups, because the whole group will be on pause as long as one or more of the dependencies in the group was published in the last 24 hours. For this reason, `unpublishSafe` is not compatible with `groupMinorUpdates`.
