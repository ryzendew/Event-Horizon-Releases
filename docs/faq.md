# FAQ - Frequently Asked Questions

## Hardware & Compatibility

### Does this work on NVIDIA?

**Yes.** This was built on NVIDIA hardware. NVIDIA GPUs work great with Hyprland and Quickshell.

Other GPUs (AMD, Intel) should also work, but I primarily test on NVIDIA, so that's what I can guarantee.

### Can I use this on [distro]?

I've tested and support:
- **Arch Linux** (and derivatives like CachyOS, EndeavourOS, XeroLinux)
- **Fedora** (and derivatives like Nobara)
- **PikaOS**

Other distros might work, but I can't guarantee it or help if something breaks. You're on your own.

### What are the system requirements?

**None.** Just need a PC running one of the supported distros:
- Arch Linux (or derivatives)
- Fedora (or derivatives)
- PikaOS

Any CPU, RAM, or GPU that runs one of these distros will work.

**Requirements:**
- Must be running **Wayland** (not X11/Xorg)
- Recent enough Linux distro to support Hyprland

---

## Installation & Setup

### What's the difference between Event Horizon Dotfiles and Event Horizon Shell?

- **Event Horizon Dotfiles** = Just the config files (`.config/hypr/` and `.config/quickshell/`). Use this if you already have Hyprland or another compositor set up.
- **Event Horizon Shell** = Full environment setup guide. Use this if you want the complete Event Horizon experience from scratch.

### Do I need to clone this repo?

**No.** Do NOT clone this repo. Download the [releases](https://github.com/ryzendew/Event-Horizon-Releases/releases) instead. This repo contains releases only — no source code.

### I only want the dotfiles. What do I do?

Run `./install.sh` from the repo. It will auto-detect your distro and copy the config files to the right places.

### Can I customize the dotfiles?

**Yes, completely.** The dotfiles are fully customizable. Edit the config files in `~/.config/hypr/` and `~/.config/quickshell/` to look however you want.

If something looks broken or not how you like it, **change it and learn the settings.** That's the whole point. It's your desktop.

See the [Hypr Configuration](hypr-configuration.md) guide for how the config is organized.

---

## Customization & Troubleshooting

### My setup looks broken / doesn't look right

**Change it.** Edit the config files in `~/.config/hypr/` and `~/.config/quickshell/` to make it look how you want. The [Hypr Configuration](hypr-configuration.md) guide explains what each file does.

Read the comments in the config files — they explain what each setting does. Then customize it to your liking.

### How do I customize keybinds?

Edit `~/.config/hypr/custom/keybinds.conf`. See the [Hypr Configuration](hypr-configuration.md) guide for details.

### How do I add/remove widgets from the top bar or dock?

Edit `~/.config/quickshell/` config files. The structure is documented in the [Hypr Configuration](hypr-configuration.md) guide.

### Can I use a different compositor (Niri, Mangowm, etc.)?

Yes. The config files have sections for different compositors. You'll need to adapt them and follow the install guide for your chosen compositor.

---

## Reporting Issues

### How do I report a bug?

Check the [Reporting Guide](reporting-issues.md) for how to submit a proper bug report.

**Before you report:**
- Make sure it's actually a bug, not a config issue
- Search existing issues to avoid duplicates
- Include distro, kernel version, GPU, and error messages

### What's the difference between a bug and a config issue?

- **Bug:** The app crashes, Hyprland locks up, or something fundamental is broken
- **Config issue:** Something doesn't look right, a setting doesn't work, or a feature is missing

For config issues, read the [Hypr Configuration](hypr-configuration.md) guide and edit the files to fix it yourself.

### My issue is not listed. Where do I get help?

First, read all the docs:
1. [Hypr Configuration](hypr-configuration.md) — How things are organized
2. [Features](features.md) — What's included
3. [Installation Guide](installation.md) — Distro-specific setup
4. [Reporting Guide](reporting-issues.md) — How to report properly

If it's still not clear, file an issue on [GitHub](https://github.com/ryzendew/Event-Horizon-Releases/issues) with as much detail as possible.

---

## Support & Contributing

### Is this production-ready?

This is a hobby project. I use it daily, but it's not a professionally-supported product. If something breaks, you're expected to fix it or learn from it.

### Can I contribute?

This repo is for releases only. If you want to contribute to the actual Event Horizon project, check the main source repo.

### Will you help me customize my setup?

No. I don't provide custom configuration support. The [Hypr Configuration](hypr-configuration.md) guide and the config files themselves have comments explaining what everything does. Learn and customize it yourself.

---

## Other Questions?

Read the docs. Seriously. They explain most things.

If you have a question that's not answered here, check:
- [Installation Guide](installation.md)
- [Hypr Configuration](hypr-configuration.md)
- [Features](features.md)
- [Reporting Guide](reporting-issues.md)
