# NEXUS OS architecture

## Product vision
A gaming-focused Linux distribution with an easy, unified experience and an original NEXUS identity. The project customizes an existing distribution; it does not create a kernel or Linux system from scratch.

## Target hardware
- CPU: AMD Ryzen 5 5600 (6 cores / 12 threads; no integrated graphics).
- GPU: AMD Radeon RX 7600.
- Memory: 16 GB RAM.
- Windows disk: 1 TB NVMe — preserve it.
- NEXUS test disk: separate 480 GB NVMe.

The RX 7600 must remain installed because the Ryzen 5 5600 has no integrated GPU. Prefer the base distribution's supported AMDGPU, Mesa and RADV stack; do not install Windows drivers or random proprietary driver packages.

## Planned components

### NEXUS Desktop
- KDE Plasma foundation.
- Dark, clean desktop with purple and cyan accents.
- Translucent top panel and dock-like app launcher.
- Original NEXUS icon set; do not redistribute Apple's proprietary icons.

### NEXUS Game Center
- Unified library for Steam, Heroic-supported Epic/GOG/Amazon libraries, Lutris and local games.
- Import native Linux games, Windows .exe/.msi installers and portable archives.
- Support AppImage and existing game folders.
- Per-game isolated Wine/Proton prefixes, install location selection, executable selection, metadata, covers, shortcuts, logs and uninstall.
- Simple automatic mode plus advanced settings for compatibility tool, prefix and launch arguments.

Security requirements:
- Never silently execute unknown installers.
- Confirm before launching .exe or .msi files.
- Validate archive paths and prevent path traversal during extraction.
- Explain that a file scan does not guarantee an installer is safe.
- Clearly disclose that some Windows games do not work on Linux due to anti-cheat, DRM or launcher restrictions.

### NEXUS Control
- Central settings, updates, hardware information and troubleshooting.

### NEXUS Core
- Shared services, configuration and integration layer.

### NEXUS Wallpapers
- Gamer categories: cyberpunk/cities, space, RGB setups, abstract neon and science fiction.
- 1080p, 1440p and 4K variants, favorites, user imports, timed rotation and multi-monitor support.
- Pause animated wallpapers while a game is fullscreen.

### NEXUS Welcome
- Brazilian Portuguese greeting, default phrase: “Seja bem-vindo, Luiz!”
- Masculine, deep, futuristic voice; friendly gamer personality.
- Prefer local neural TTS (Piper) after validating an appropriate voice model and redistribution license.
- User controls for name, volume, voice test, enable/disable and greeting frequency.
- Delay around eight seconds after login; suppress while a game is fullscreen.
- Do not claim a specific voice model is ready until it has been tested.

## Planned game library layout
```
NEXUS/
├── Games/
│   ├── Windows/
│   ├── Linux/
│   └── Portable/
├── Prefixes/
├── Downloads/
├── Installers/
├── Covers/
└── Library/
```


### NEXUS Universal Emulator
- Native system integration through a platform registry, emulator manager and Game Center launch adapters.
- Initial platform targets: DuckStation (PS1), PCSX2 (PS2), RPCS3 (PS3), shadPS4 (PS4, experimental), xemu (original Xbox), and Xenia (Xbox 360, experimental pending Linux build validation).
- Xbox One and Xbox Series X|S remain future/unsupported targets until a mature general-purpose emulator exists.
- Centralized detection, installation/update policy, per-emulator configuration, controller integration, saves and per-game compatibility metadata.
- Do not bundle copyrighted games, console firmware, BIOS or keys. Users supply legally obtained files.
- See [EMULATION.md](EMULATION.md) for the implementation plan and MVP scope.
