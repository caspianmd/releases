- `Caspian-Setup-<version>.exe` — Windows installer
- `Caspian-<version>.zip` — macOS app, zipped
- `Caspian-<version>.tar.gz` — Linux archive (no auto-update; tar.gz isn't a self-updating format)
- `latest.yml`, `latest-mac.yml` — update metadata electron-updater reads to detect a new version
- `caspianmd-caspian-<version>.tgz` — the `caspian` command-line tool's npm package (the desktop app bundles the same CLI). Publishing a release here runs `.github/workflows/publish-cli.yml`, which publishes this file to npm as `@caspianmd/caspian`; it needs the `NPM_TOKEN` repository secret.

## Live model table

- `model-table.json` (on `main`) — per-model pricing/throughput and context/output limits. The app's pre-flight cost estimate fetches it at runtime from `https://raw.githubusercontent.com/caspianmd/releases/main/model-table.json` (cached ~10 min, last good copy kept on disk, bundled table as offline fallback). Edit and push to update every install — no app release needed. Unlike the release assets above, this file lives on the branch, not on a tag.
