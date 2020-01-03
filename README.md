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
    "github>CondeNast/renovate-config:dontAutomergeTestFrameworks",
    "github>CondeNast/renovate-config:groupMinorUpdates(dependencies)"
  ]
}
```

## Presets

### `automergeMinor`

Enables automerge for minor and patch updates to non-condenast packages.

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
