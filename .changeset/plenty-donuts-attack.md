---
"dextinity-site": minor
---

Add an optional copy assets job that runs as a `pre-install` and `pre-upgrade` hook. Enable it with `copyAssets.enabled` and set the command to run in `copyAssets.command`. The job uses the site image and gets the same environment, secrets and image pull secret as the deployment. Its secrets and config map are deleted once the hook has finished, whether it succeeded or failed.
