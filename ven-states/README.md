# VEN-STATES launcher assets

This directory is the project-owned location for launcher feeds and, later, the game manifest.

## Game updater contract

The existing updater engine is retained. Configure these values in `launcher_settings.extra`:

- `ven_states_cdn_main`: HTTPS base URL that serves `game.json` and `game/<relative-path>`.
- `ven_states_cdn_reserve`: optional HTTPS mirror with the same files.

The manifest must use the existing tree format: a JSON object with a `data` array. Each downloadable file entry needs `type: "file"`, `name`, `size`, and MD5 `hash`. Directory entries use `type: "dir"` and nested `data`.

Do not point these settings at an Arizona host. The updater deliberately has no Arizona fallback.

## Current state

The feed below is only launcher news. A real `game.json` and game-file mirror have not been published yet, so automatic game installation/update remains disabled until VEN-STATES assets are uploaded.
