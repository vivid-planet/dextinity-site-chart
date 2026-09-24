# dextinity-site

## 1.1.1

### Patch Changes

- 1907725: Replace `rsync` with `cp` in the build CronJob

    Since rsync 3.5.0 the build job fails when it writes the tar to the `generated-sites` volume, with `failed to set permissions on "/mnt/generated-sites/.build_<date>.tar.<suffix>": Operation not permitted` and exit code 23. rsync sets the permissions of the file it transfers and the volume does not allow that. No build reaches the volume, so the site keeps serving the previous one.

    rsync has nothing to offer in this step anyway: it copies a single local file, without delta transfer or a remote host. `cp` takes the mode from the source while it creates the file and runs no `chmod` afterwards, so the volume accepts the copy. `rm` takes over what `--remove-source-files` did.

## 1.1.0

### Minor Changes

- ae1432b: Add an optional copy assets job that runs as a `pre-install` and `pre-upgrade` hook. Enable it with `copyAssets.enabled` and set the command to run in `copyAssets.command`. The job uses the site image and gets the same environment, secrets and image pull secret as the deployment. Its secrets and config map are deleted once the hook has finished, whether it succeeded or failed.

## 1.0.0

### Major Changes

- Initial release, rebranded from `comet-site` 2.2.0 in the `comet-charts`
  repository. The chart name, the template helper prefix and the label and annotation keys
  moved from `comet`/`comet-dxp.com` to `dextinity`/`dextinity.com`. Charts are published
  as OCI artifacts under `oci://ghcr.io/vivid-planet/charts` instead of a Helm repository.
