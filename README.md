# NEXUS OS Alpha 0.1 — Gaming Edition

NEXUS OS is a planned gaming-focused Linux distribution built on an existing Linux base rather than a kernel written from scratch.

## Project goals
- A polished KDE Plasma desktop with an original NEXUS visual identity (dark surfaces, purple/cyan accents, dock-like launcher and original icons).
- One Game Center for game stores, native Linux games, Windows installers and portable games.
- A configurable Brazilian Portuguese welcome greeting with local speech synthesis.
- Gamer wallpapers, system controls and hardware diagnostics.

## Planned foundation
- Base image: Bazzite KDE / Universal Blue.
- Image customization: BlueBuild.
- Target test hardware: AMD Ryzen 5 5600, Radeon RX 7600, 16 GB RAM.
- Test destination: separate 480 GB NVMe SSD.

## Safety
**Do not install to or format the 1 TB NVMe that contains Windows.** During installation testing, disconnect that drive if possible. Verify disk model and capacity before selecting any target.

Windows game compatibility is not universal. Anti-cheat, DRM and launchers may prevent some titles from running. Unknown installers must never be executed without explicit user confirmation.

## Current status
This repository is an initial project scaffold, not a finished operating system or installable ISO. The desktop theme, Game Center, full Welcome integration, wallpaper manager and ISO pipeline still require implementation and testing.

See [Architecture](docs/ARCHITECTURE.md), [Roadmap](docs/ROADMAP.md) and [Build notes](docs/BUILD.md).
