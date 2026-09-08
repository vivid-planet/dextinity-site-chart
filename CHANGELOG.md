# dextinity-site

## 1.1.0

### Minor Changes

- ae1432b: Add an optional copy assets job that runs as a `pre-install` and `pre-upgrade` hook. Enable it with `copyAssets.enabled` and set the command to run in `copyAssets.command`. The job uses the site image and gets the same environment, secrets and image pull secret as the deployment. Its secrets and config map are deleted once the hook has finished, whether it succeeded or failed.

## 1.0.0

### Major Changes

- Initial release, rebranded from `comet-site` 2.2.0 in the `comet-charts`
  repository. The chart name, the template helper prefix and the label and annotation keys
  moved from `comet`/`comet-dxp.com` to `dextinity`/`dextinity.com`. Charts are published
  as OCI artifacts under `oci://ghcr.io/vivid-planet/charts` instead of a Helm repository.
