# Build Emma

**Build software with a resident agent.**

[buildemma.com](https://buildemma.com) · [⬇️ Download](../../releases/latest) · [Discord](https://discord.gg/cJVHKNeCxP)

A workspace you can daily-drive, collaboration that needs no server, and EMMA — an agent that runs on *your* models, on *your* machine, and never changes a line you haven't approved.

`local-first · no account · no telemetry · works offline · cloud models opt-in`

> **This repo is just the downloads.** There's no source code here. It's the public home for the installers, and for the update check inside the app.

## Download

Grab the installer for your system from the **[latest release](../../releases/latest)**.

| | |
|---|---|
| **Linux** | `.AppImage` (portable, no root), `.deb`, `.rpm` |
| **Windows** | `-setup.exe` installer, `.msi` |
| **macOS** | Not yet. It builds, but hasn't had its hands-on install check. |

**Windows:** the installer isn't code-signed yet, so Windows shows *"Windows protected your PC"* on first run. Click **More info → Run anyway**.

## What you need

- **[Ollama](https://ollama.com)** running with at least one model, e.g. `ollama pull qwen3:8b`
- *Optional:* a Claude or OpenAI key for cloud models. It's kept in the app's encrypted vault.

## Updates

Build Emma checks this repo for a newer release, tells you when there is one, and installs it when you say so. Every update is signed, and the app refuses one that isn't.

## Checking a download

Each release lists a SHA-256 checksum for every file.

## Help

[Discord](https://discord.gg/cJVHKNeCxP) · Gregorymoores@proton.me
