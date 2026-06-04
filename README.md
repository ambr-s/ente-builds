# Custom Ente Desktop builds for apex-hosted Ente

Rebuilds of the [Ente Photos](https://ente.io) desktop app, preconfigured for the **`ente.apex.to`** instance and built on **Electron 42.3.2**, which resolves a cursor-rendering bug on GNOME/Wayland (the bottom half of the pointer getting clipped).

Builds are produced for **Linux, Windows and macOS** and published to this repo's [Releases](../../releases). Once installed, the app keeps itself up to date automatically (see [Auto-updates](#auto-updates)).

> [!NOTE]
> These builds talk to `ente.apex.to`. If that isn't your server, you'll have to override the server or get the official app from [ente.io/download](https://ente.io/download) instead.

## Install

### Linux (AppImage)

1. Download the latest `.AppImage` from [Releases](../../releases/latest).
2. Make it executable and run it:
   ```bash
   chmod +x ente*.AppImage
   ./ente*.AppImage
   ```
3. Run it **as an AppImage** (don't extract it first), that's what enables auto-updates. [AppImageLauncher](https://github.com/TheAssassin/AppImageLauncher) is handy for menu/desktop integration.

> [!TIP]
> For the best rendering on Wayland, launch with `ELECTRON_OZONE_PLATFORM_HINT=auto` so it runs natively rather than through XWayland.

### Windows

1. Download the latest `.exe` from [Releases](../../releases/latest) and run it.
2. These builds are **unsigned**, so SmartScreen warns once. Click **More info → Run anyway**. Background auto-updates afterward won't prompt again.

### macOS

1. Download the latest `.dmg` from [Releases](../../releases/latest) and drag the app to Applications.
2. The build is **self-signed but not notarized**, so Gatekeeper blocks the first launch. Clear the quarantine flag once:
   ```bash
   xattr -dr com.apple.quarantine "/Applications/ente photos.app"
   ```
   (Or right-click the app → **Open** → **Open**.) After that first launch, updates apply automatically.

## Auto-updates

- **Linux & Windows**: updates download silently in the background; relaunch to apply.
- **macOS**: updates automatically *after* the one-time first-launch step above. The updater fetches in-app, so no further Gatekeeper prompts.

Version numbers mirror upstream Ente exactly (Ente `v1.7.24` becomes this repo's `v1.7.24`) so the update channel lines up cleanly.
