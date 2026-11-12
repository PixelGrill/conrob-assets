# conrob-assets

Downloadable model and asset files for ConRob apps, hosted under our own
control so an app never depends on a third party account staying online or
staying unchanged.

## How this repo is organized

- One top-level folder per app (today: `mismo/`). Each app folder holds
  that app's manifests and attribution notes in git.
- The binary files themselves live in **GitHub Releases**, tagged per app
  (for example `mismo-voice-1`, `mismo-translation-1`), so each app can
  version its asset set independently and future apps get their own tags.
- Every release asset is listed in the owning app's manifest with its
  byte size and SHA-256. The apps verify size and SHA-256 after download
  and refuse a file that does not match, so the host can never silently
  change what an app runs.

## Why public

The apps download these files with no credentials, and GitHub release
assets in a private repo cannot be fetched by an unauthenticated app.
Everything mirrored here is open licensed (MIT, Apache-2.0, or CC-BY-4.0
with attribution recorded in the per-app folders), so a public repo is
both required and clean.

## Adding another app later

Create `<app>/` with its manifests and attribution, cut releases tagged
`<app>-<set>-<version>`, and record the hashes in the app folder before
pointing the app at the URLs.
