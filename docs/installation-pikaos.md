# PikaOS Installation

Follow these steps to install DarkMatter Shell on PikaOS.

## Step 1: Update System

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
## Step 4: Setup quickshell as a Service

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
