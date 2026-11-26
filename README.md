# VEN-STATES Launcher

Standalone Windows launcher for **VEN-STATES RP** built with Rust and Tauri 2.

**Game server:** `188.127.241.74:3699`

## Current direction

- Launches the user's existing GTA San Andreas installation directly.
- Uses standard SA-MP 0.3.7 connection arguments; no Arizona Air client is required.
- Does not perform Arizona launcher-version checks.
- Keeps the existing download engine: resumable `.part` files, MD5 verification, fallback mirror support, and the hash cache.
- Game updates are routed only through VEN-STATES-owned CDN settings. No Arizona CDN fallback is configured.
- Automatically detects common GTA San Andreas installation locations and also supports manual folder selection.

## Game updater setup

The updater engine expects an HTTPS base URL that serves:

- `game.json` — a JSON manifest with a `data` array.
- `game/<relative-path>` — the files referenced by the manifest.

Configure the optional values in `launcher_settings.extra`:

- `ven_states_cdn_main`
- `ven_states_cdn_reserve`

Until VEN-STATES publishes its own manifest and client files, automatic game installation/update remains inactive. Existing cache and download-resume logic are retained.

See [VEN-STATES asset setup](ven-states/README.md).

## Build

Requirements: Windows 10/11 x64, Rust stable, Node.js 20+, and Microsoft C++ Build Tools.

```bash
npm ci
cargo test --manifest-path src-tauri/Cargo.toml
npm run build
```

The Windows NSIS installer is produced under:

`src-tauri/target/release/bundle/nsis/`

GitHub Actions runs the Rust tests and Windows installer build for pushes to `main`, `ven-states/**`, and pull requests to `main`.

## Project status

This repository is being separated from the original Arizona launcher codebase. The core launch path and version gate have been detached; optional catalog and patch features are being migrated to VEN-STATES-owned assets.

## License

GPL-3.0. See [LICENSE](LICENSE).
