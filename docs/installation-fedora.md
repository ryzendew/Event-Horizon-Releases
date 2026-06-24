# Fedora / Nobara Installation
## Install Dependencies For the DE

```bash
sudo dnf install wayland cairo pango freetype fontconfig libxkbcommon \
  sdbus-cpp pipewire pam libcurl libwebp openssl vulkan-loader \
  hicolor-icon-theme glib2 lz4
```

Optional (extra features): `librsvg2 libdrm polkit`

## Install Event Horizon DE

Download the `.rpm` from the [releases page](https://github.com/ryzendew/Event-Horizon-Releases/releases) and install:

```bash
sudo dnf install ./event-horizon-de-<version>-1.x86_64.rpm
```

Optional components (install the same way):

```bash
sudo dnf install ./horizon-shot-<version>-1.x86_64.rpm
sudo dnf install ./horizon-files-<version>-1.x86_64.rpm
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

Follow these steps to install Event Horizon Shell on Fedora-based distros.

## Step 1: Dotfile install Setup : Update your system

```bash
sudo dnf update -y
```

## Step 2: Enable Required Repositories

You'll need RPM Fusion for some packages:

```bash
sudo dnf install -y https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install -y https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

And enable these COPR repos:

```bash
sudo dnf copr enable -y lionheartp/Hyprland
sudo dnf copr enable -y errornointernet/quickshell
sudo dnf install --nogpgcheck --repofrompath 'terra,https://repos.fyralabs.com/terra$releasever' terra-release
```

Update your package cache:

```bash
sudo dnf makecache
```
## Step 3: Install Everything Else

Here's the big package install command:

```bash
sudo dnf install -y hyprland xdg-desktop-portal-hyprland gnome-keyring brightnessctl cliphist gedit gnome-disks gnome-system-monitor gnome-text-editor grim nautilus pavucontrol polkit ptyxis qt6ct slurp swappy tesseract wl-clipboard wlogout yad quickshell-git python3-pyqt6 btop gedit jq cava wlr-randr khal python-requests
```

## Mangowm

```bash
sudo dnf install -y  mangowm xdg-desktop-portal-wlr gnome-keyring brightnessctl cliphist gedit gnome-disks gnome-system-monitor gnome-text-editor grim nautilus pavucontrol polkit ptyxis qt6ct slurp swappy tesseract wl-clipboard wlogout yad quickshell-git python3-pyqt6 btop gedit jq cava wlr-randr khal python-requests
```

## Niri 

```bash
sudo dnf install -y niri brightnessctl grim slurp swappy wl-clipboard cliphist swaybg swaylock swayidle mako fuzzel wlr-randr xwayland-satellite nautilus pavucontrol gnome-disks gnome-system-monitor qt6ct polkit gnome-keyring wlogout yad jq btop cava quickshell-git xdg-desktop-portal-gnome xdg-desktop-portal-gtk
```


## Step 4: Python Dependencies

```bash
pip install pynvml
```

## Step 5: dgop

Build it from source:

```bash
# Get Go and build tools
sudo dnf install -y golang git make

# Build it
cd /tmp
git clone https://github.com/AvengeMedia/dgop.git
cd dgop
make
sudo make install
cd .. && rm -rf dgop
```

## Step 6: matugen

Install via Cargo:

```bash
# Install Rust if needed
sudo dnf install -y rust cargo

# Install matugen
cargo install matugen
```

## Step 7: Install Fonts

Fonts are included with the config, but install them system-wide if you want.

### Noto Fonts

```bash
sudo dnf install -y google-noto-fonts google-noto-emoji-fonts
```

## Step 8: Setup quickshell as a Service

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
