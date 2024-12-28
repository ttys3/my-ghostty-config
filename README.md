# my-ghostty-config

this is my [Ghostty](https://github.com/ghostty-org/ghostty.git) config repository, which I use to manage my Ghostty configuration.

This repository should help you quickly set up a working Ghostty configuration.

## how to use the config?

```
cd ~/.config

git clone https://github.com/ttys3/my-ghostty-config.git ghostty

ghostty +validate-config
```

## How to install Ghostty from source code under Fedora Linux

ref https://ghostty.org/docs/install/build

```shell
sudo dnf install gtk4-devel zig libadwaita-devel
```

```shell
mkdir -p ~/repo/zig/
cd ~/repo/zig/
git clone https://github.com/ghostty-org/ghostty.git
cd ghostty
zig build -p $HOME/.local -Doptimize=ReleaseFast

# workaround to fix the desktop file for non-root user installation
desktop-file-edit --set-key=Exec --set-value=$HOME/.local/bin/ghostty ~/.local/share/applications/com.mitchellh.ghostty.desktop
```

## Troubleshooting

### 1. GNOME + Wayland with `GTK_IM_MODULE=fcitx` set can not activate fcitx5 input method

ref https://github.com/ghostty-org/ghostty/discussions/3628

solution:

```shell
desktop-file-edit --set-key=Exec --set-value="env GTK_IM_MODULE=wayland ghostty" ~/.local/share/applications/com.mitchellh.ghostty.desktop
```
