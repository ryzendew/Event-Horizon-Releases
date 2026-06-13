# Arch Linux / CachyOS / EndeavourOS / XeroLinux Installation

Follow these steps to install DarkMatter Shell on Arch-based distros.


## Install Dependencies

```bash
sudo pacman -S wayland cairo pango freetype2 fontconfig libxkbcommon \
  sdbus-cpp pipewire pam curl libwebp openssl vulkan-icd-loader \
  hicolor-icon-theme glib2 lz4
```

Optional (extra features): `libjpeg-turbo librsvg libdrm polkit`

## Install Event Horizon DE

Download the `.pkg.tar.zst` from the [releases page](https://github.com/ryzendew/Event-Horizon-DE/releases) and install:

```bash
sudo pacman -U event-horizon-de-<version>-1-x86_64.pkg.tar.zst
```

Optional components (install the same way):

```bash
sudo pacman -U horizon-shot-<version>-1-x86_64.pkg.tar.zst
sudo pacman -U horizon-files-<version>-1-x86_64.pkg.tar.zst
```

## Running

Launch from your compositor's config. For example in Hyprland:

```
exec-once = EventHorizon
```

Or run from a terminal after your compositor is started:

```bash
EventHorizon
```

Settings: `EventHorizon --settings`

## Step 1: Update System

First, make sure your system is up to date:

```bash
sudo pacman -Syu
```

## Step 2: Install Official Repository Packages Hyprland

```bash
sudo pacman -S hyprland quickshell-git brightnessctl cliphist gedit grim mission-center nautilus pavucontrol polkit ptyxis qt6ct slurp swappy tesseract wl-clipboard xdg-desktop-portal-hyprland yad xorg-xhost jq matugen khal cava wlr-randr python-requests
```
## Install Official Repository Packages mangowm

```bash
sudo pacman -S quickshell-git brightnessctl cliphist gedit grim mission-center nautilus pavucontrol polkit ptyxis qt6ct slurp swappy tesseract wl-clipboard xdg-desktop-portal-wlr yad xorg-xhost jq matugen khal cava wlr-randr python-requests
```

## Install Official Repository Packages Niri

```bash
sudo pacman -S niri quickshell-git brightnessctl cliphist gedit grim mission-center nautilus pavucontrol polkit ptyxis qt6ct slurp swappy tesseract wl-clipboard yad xorg-xhost jq matugen khal cava wlr-randr python-requests swaybg swaylock swayidle xwayland-satellite xdg-desktop-portal-gnome xdg-desktop-portal-gtk
```

## Step 3: Install AUR Helper (if needed)

You'll need an AUR helper. I use `yay`, so install it if you don't have it already:

```bash
sudo pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay && makepkg -si && cd .. && rm -rf yay
```

## Step 4: Install AUR Packages

```bash
yay -S anyrun dgop python-pynvml wlogout
```

## mangowm

```bash
yay -S mangowm-git
```

Or build it yourself if you prefer:

```bash
# Install Go if you don't have it
sudo pacman -S --needed go

# Build it
cd /tmp
git clone https://github.com/AvengeMedia/dgop.git
cd dgop
make
sudo make install
cd .. && rm -rf dgop
```

## Step 5: Install Fonts

Fonts are included with the config, but install them system-wide if you want.



### Noto Fonts
```bash
# Install Fonts cmd
sudo pacman -S noto-fonts noto-fonts-emoji
```

## Step 6: Setup quickshell as a Service

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

