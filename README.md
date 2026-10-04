# Collie releases

Binaries of Collie, a voice assistant that watches your coding agents. The source is private; this
repository only holds releases.

Each release has the `collie-server` daemon for macOS (Apple Silicon), Linux x86_64 and Linux arm64,
`SHA256SUMS`, and `Collie-<version>.zip` (the macOS app). The app downloads the daemon of its own
version from here when it installs it, and checks it against the checksums it was built with.

## Verify a download

    shasum -a 256 -c SHA256SUMS --ignore-missing

## Offline install

Download the bundle for the target and put it into `~/Library/Caches/collie/bundles/<version>/` on
the Mac that runs the app, or start the app with `COLLIE_DIST=<folder with the bundle>`. A variable does not reach an app launched from Finder: use `open --env COLLIE_DIST=<folder> Collie.app` (macOS 13+) or run `Collie.app/Contents/MacOS/collie-app` from a shell with the variable set. The command
line installer takes `collie-server install --bundles <folder>`.

## Third-party software

The bundles include LiveKit server (Apache-2.0), ONNX Runtime (MIT) and sherpa-onnx (Apache-2.0);
their licenses are in `LICENSES/`. Speech models are not included: the daemon downloads them from
their authors when asked.
