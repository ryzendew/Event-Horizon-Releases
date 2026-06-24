# Event Horizon Releases

My personal desktop environment setup for Linux, built on Hyprland and Quickshell. It's basically a complete desktop experience that I've been tweaking and refining over time.

PLEASE READ THE DOCS BEFORE ASKING FOR HELP ... IT EXPLAINS EVERYTHING JUST LOOK BELOW!

## What is this?

A repo for release artifacts and configuration files for Event Horizon Shell and Event Horizon Dotfiles. This is not a full Linux distribution installer.

## Reporting Issues

Found a bug or have an issue? Please check the [Reporting Guide](docs/reporting-issues.md) for how to submit a good bug report.

## Quick Start

This repo contains two separate things:

- **Event Horizon Dotfiles** — config files only
- **Event Horizon Shell** — desktop shell environment install guidance

### Event Horizon Dotfiles

Run the universal installer to install the dotfiles and config files only:

```
chmod +x install.sh
```

```bash
./install.sh
```

The installer will:
- ✅ **Ask for confirmation** before starting installation
- ✅ Auto-detect your distribution (Arch, Fedora, Ubuntu, Debian, PikaOS)
- ✅ Check for already installed packages and skip them
- ✅ Handle sudo permissions automatically
- ✅ Install all required dependencies
- ✅ **Automatically copy config files** to `~/.config/hypr/` and `~/.config/quickshell/`
- ✅ **Backup existing configs** to `.bak` folders (only on first install)
- ✅ Provide fallbacks if `matugen` or `dgop` compilation fails
- ✅ Continue installation even if some components fail

### Event Horizon Shell

If you want the full desktop shell experience, follow the distro-specific install docs:

- [Installation Guide](docs/installation.md)

## Manual Installation

If you prefer manual setup for Event Horizon Shell, use the [Installation Guide](docs/installation.md) and pick your distro page.

## Next Steps

1. Your Event Horizon setup is ready! Config files are automatically installed.
2. Check out the [Features](docs/features.md) documentation
3. Read the [Hypr Configuration](docs/hypr-configuration.md) guide to customize things
4. Your previous configs are backed up as `.bak` folders if you need to restore them

## Documentation

### Installation

**Universal Installer (Recommended):** Run `./install.sh` - auto-detects your distro and handles everything!

**Manual Installation:** See the [Installation Guide](docs/installation.md) and use the distro-specific pages:

- [Arch Linux and derivatives (CachyOS, EndeavourOS, XeroLinux)](docs/installation-arch.md)
- [Fedora and derivatives (Nobara)](docs/installation-fedora.md)
- [PikaOS](docs/installation-pikaos.md)

Covers all packages, fonts, and post-installation setup.

### [Features](docs/features.md)

What's included in this setup:

- Desktop stuff (top bar, dock, control center)
- System integration (audio, displays, network, power)
- Various utilities
- Customization options
- Application support

### [Hypr Configuration](docs/hypr-configuration.md)

How the Hyprland config is organized:

- File structure and what goes where
- How to customize things
- Window rules and keybinds
- Monitor setup
- Shader effects

## Supported Distributions

I've tested this on:

- **Arch Linux** (and derivatives)
- **Fedora** (and derivatives)
- **PikaOS**

Other distros might work, but I haven't tested them and can't help if something breaks.

## What's Inside

- **Hyprland** - The window manager (tiling Wayland compositor)
- **Quickshell** - Shell system with widgets and launchers
- **Material You** theming using matugen
- System integration for audio, network, displays, etc.
- Lots of customization options

## License

This was originally inspired by [DankMaterialShell](https://github.com/AvengeMedia/DankMaterialShell), but I've rewritten everything and it's no longer a fork. The design keeps changing as I tweak things.

Do whatever you want with it. Fork it, modify it, use parts of it - I don't care about attribution Because it's open source DUH.
