# Installation Guide

> **Do NOT clone this repo.** Download the releases from [https://github.com/ryzendew/Event-Horizon-Releases/releases](https://github.com/ryzendew/Event-Horizon-Releases/releases) instead. This is a releases-only repository.

Here's how to get Event Horizon Shell set up on your system. The process is a bit different depending on what distro you're running.

## Table of Contents

Pick your distro and follow the steps.

- [Arch Linux / CachyOS / EndeavourOS / XeroLinux](installation-arch.md)
- [Fedora / Nobara](installation-fedora.md)
- [PikaOS](installation-pikaos.md)
- [Post-Installation](#post-installation)
- [Next Steps](#next-steps)

> This page covers **Event Horizon Shell** installation. If you only want **Event Horizon Dotfiles**, use the dotfiles install instructions in the README instead.

## Installation by Distribution

Each distro has its own page with all commands, including fonts:

- [Arch Linux / CachyOS / EndeavourOS / XeroLinux](installation-arch.md)
- [Fedora / Nobara](installation-fedora.md)
- [PikaOS](installation-pikaos.md)

> These pages install **Event Horizon Shell**. If you only want **Event Horizon Dotfiles**, stop here and use the README dotfiles instructions.

---

## Post-Installation

After you've installed everything, run this:

```bash
xdg-user-dirs-update
```

This makes sure your user directories are set up properly.

---

## Next Steps

Once everything is installed:

1. Copy the config files to your system (usually `~/.config/hypr/` and `~/.config/quickshell/`)
2. Check out the [Features](features.md) doc to see what's included
3. Read the [Hypr Configuration](hypr-configuration.md) guide to customize things

