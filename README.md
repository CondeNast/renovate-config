# CondeNast/renovate-config

This is a collection of [GitHub-hosted presets](https://docs.renovatebot.com/config-presets/#github-hosted-presets) for Renovate dependency bot. 🤖

## Usage

In your `renovate.json`:

```
{
  "extends": [
    "github>CondeNast/renovate-config",
    "github>CondeNast/renovate-config:forceCondenastUpdates"
  ]
}
```

The `CondeNast/renovate-config` preset should go at the start of the `extends` array.

The `CondeNast/renovate-config:forceCondenastUpdates` preset should go at the end of your `extends` array to ensure that PRs for Condé Nast package updates are created as soon as possible, to bypass any rate limiting and schedules.

If you would like to [auto-merge](https://docs.renovatebot.com/configuration-options/#automerge) minor upgrades, here is a recommended configuration for doing that:

```
{
  "extends": [
    "github>CondeNast/renovate-config",
    "github>CondeNast/renovate-config:automergeMinor",
    "github>CondeNast/renovate-config:dontAutomergeMajor(help wanted)",
    "github>CondeNast/renovate-config:dontAutomergeNode(help wanted)",
    "github>CondeNast/renovate-config:dontAutomergeTestFrameworks(help wanted)",
    "github>CondeNast/renovate-config:dontAutomergeCIDependencies(help wanted)",
    "github>CondeNast/renovate-config:condenastStabilityDays",
    "github>CondeNast/renovate-config:forceCondenastUpdates"
  ]
}
```

You can also use any individual **semantic presets** without using the base preset. Here's a configuration that groups things but doesn't auto-merge them:

```
{
  "extends": [
    "config:base",
    "github>CondeNast/renovate-config:groupMinorUpdates(dependencies)",
    "github>CondeNast/renovate-config:groupCIDependencyUpdates",
    "github>CondeNast/renovate-config:groupLinterUpdates",
    "github>CondeNast/renovate-config:groupNodeUpdates",
    "github>CondeNast/renovate-config:forceCondenastUpdates"
  ]
}
```

## Semantic Presets

A description for each preset can be found in the JSON file for the preset stored in this repo.

### Condé Nast presets

* [`github>CondeNast/renovate-config:forceCondenastUpdates`](./forceCondenastUpdates.json) - **NOTE: this preset should go at the end of the `extends` array.**
* [`github>CondeNast/renovate-config:condenastStabilityDays`](./condenastStabilityDays.json)

### PR Group presets

* [`github>CondeNast/renovate-config:groupMinorUpdates`](./groupMinorUpdates.json)
* [`github>CondeNast/renovate-config:groupCIDependencyUpdates`](./groupCIDependencyUpdates.json)
* [`github>CondeNast/renovate-config:groupLinterUpdates`](./groupLinterUpdates.json)
* [`github>CondeNast/renovate-config:groupNodeUpdates`](./groupNodeUpdates.json)

### Auto-Merge presets

* [`github>CondeNast/renovate-config:automergeMinor`](./automergeMinor.json)
* [`github>CondeNast/renovate-config:dontAutomergeMajor`](./dontAutomergeMajor.json)
* [`github>CondeNast/renovate-config:dontAutomergeNode`](./dontAutomergeNode.json)
* [`github>CondeNast/renovate-config:dontAutomergeTestFrameworks`](./dontAutomergeTestFrameworks.json)
* [`github>CondeNast/renovate-config:dontAutomergeCIDependencies`](./dontAutomergeCIDependencies.json)
* [`github>CondeNast/renovate-config:unpublishSafe`](./unpublishSafe.json) - **NOTE: `unpublishSafe` doesn't work if you apply it to dependency groups, because the whole group will be on pause as long as one or more of the dependencies in the group was published in the last 24 hours. For this reason, `unpublishSafe` is not compatible with `groupMinorUpdates`.**


### Package Pattern presets

These presets can be used to apply custom rules to a set of packages using [`packageRules`](https://docs.renovatebot.com/configuration-options/#packagerules).

* Node.js sources - [`github>CondeNast/renovate-config:node`](./node.json)
* Condé Nast packages - [`github>CondeNast/renovate-config:orgPackages`](./orgPackages.json)
* Testing frameworks - [`github>CondeNast/renovate-config:testFrameworks`](./testFrameworks.json)
