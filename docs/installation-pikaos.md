# PikaOS Installation

> This page installs **Event Horizon Shell**. If you only want **Event Horizon Dotfiles** (config files only), stop here and use the README dotfiles section.

## Install Dependencies for Event Horizon Shell

```bash
sudo apt install libwayland-client0 libcairo2 libpango-1.0-0 libfreetype6 \
  fontconfig libxkbcommon0 libsdbus-c++-2 libpipewire-0.3-0 libpam0g \
  libcurl4 libwebp7 libvulkan1 hicolor-icon-theme libglib2.0-0 liblz4-1 \
  libfontconfig1
```

Optional (extra features): `libjpeg-turbo8 librsvg2-2 libdrm2 policykit-1`

If `libsdbus-c++-2` is not found, try `libsdbus-c++-1` (package name varies by release).

## Install Event Horizon Shell

Download the `.deb` from the [releases page](https://github.com/ryzendew/Event-Horizon-Releases/releases) and install:

```bash
sudo apt install ./event-horizon-de_<version>_amd64.deb
```

Optional components (install the same way):

```bash
sudo apt install ./horizon-shot_<version>_amd64.deb
sudo apt install ./horizon-files_<version>_amd64.deb
```

## Running

Add to your compositor's config. For example in Hyprland:

```
exec-once = EventHorizon
```

Or run from a terminal after your compositor is started:

```bash
EventHorizon
```

Settings: `EventHorizon --settings`


Follow these steps to install Event Horizon Shell on PikaOS.

## Step 1: Update your system

```bash
sudo apt update && sudo apt upgrade -y
```

## Step 2: Packages

## Install All Packages Hyprland 

Install all required packages in a single command:

```bash
sudo apt install -y --no-install-recommends hyprland xdg-desktop-portal-hyprland gnome-keyring brightnessctl cliphist gedit gnome-system-monitor gnome-text-editor grim nautilus pavucontrol ptyxis qt6ct slurp swappy tesseract-ocr wl-clipboard wlogout yad qtbase5-dev qt6-base-dev python3-pyqt6 python3-pip quickshell qml6-module-qtquick-controls qml6-module-qtcore qml6-module-qtquick-effects qml6-module-qt5compat-graphicaleffects qml6-module-qt-labs-folderlistmodel qml6-module-qt-labs-platform matugen jq dgop cava wlr-randr khal python3-requests quickshell-git
```

## Install All Packages Mangowm

```bash
sudo apt install -y --no-install-recommends mangowm xdg-desktop-portal-wlr brightnessctl cliphist gedit gnome-system-monitor gnome-text-editor grim nautilus pavucontrol ptyxis qt6ct slurp swappy tesseract-ocr wl-clipboard wlogout yad qtbase5-dev qt6-base-dev python3-pyqt6 python3-pip quickshell qml6-module-qtquick-controls qml6-module-qtcore qml6-module-qtquick-effects qml6-module-qt5compat-graphicaleffects qml6-module-qt-labs-folderlistmodel qml6-module-qt-labs-platform matugen jq dgop cava wlr-randr khal python3-requests quickshell-git
```

## Install All Packages Niri 

```bash
sudo apt install -y --no-install-recommends niri xdg-desktop-portal-gtk brightnessctl cliphist gedit gnome-system-monitor gnome-text-editor grim nautilus pavucontrol ptyxis qt6ct slurp swappy tesseract-ocr wl-clipboard wlogout yad qtbase5-dev qt6-base-dev python3-pyqt6 python3-pip quickshell qml6-module-qtquick-controls qml6-module-qtcore qml6-module-qtquick-effects qml6-module-qt5compat-graphicaleffects qml6-module-qt-labs-folderlistmodel qml6-module-qt-labs-platform matugen jq dgop cava wlr-randr khal python3-requests quickshell-git
```

## Step 3: Python Dependencies

```bash
pip install pynvml --break-system-packages
```

## Step 4: Install Fonts

Fonts are included with the config, but install them system-wide if you want.

### Noto Fonts (optional)

```bash
sudo apt install -y fonts-noto fonts-noto-color-emoji
```
## Step 5: Setup quickshell as a Service

**Here's how to set up a user-level systemd service**

### 1. Create the directory (if it doesn't exist)

```bash
mkdir -p ~/.config/systemd/user
```

### 2. Place your service file

Save the file as:

```bash
~/.config/systemd/user/quickshell.service
```

You can do it with a text editor:

```bash
nano ~/.config/systemd/user/quickshell.service
```

Then paste your content:

```ini
[Unit]
Description=Quickshell Wayland Shell
After=graphical-session.target

[Service]
Type=simple
Environment=QT_QPA_PLATFORM=wayland
Environment=QT_WAYLAND_RECONNECT=1
ExecStart=qs
Restart=on-failure
RestartSec=1

[Install]
WantedBy=default.target
```

### 3. Reload systemd and enable/start the service

```bash
# Reload user services
systemctl --user daemon-reload

# Enable and start it now
systemctl --user enable --now quickshell.service
```

### 4. Check status

```bash
systemctl --user status quickshell.service
```

### Useful commands

- **Restart** the service:  
  `systemctl --user restart quickshell.service`

- **Stop** it:  
  `systemctl --user stop quickshell.service`

- **Disable** (so it doesn't start automatically):  
  `systemctl --user disable quickshell.service`

- **View logs**:  
  `journalctl --user -u quickshell.service -f`
