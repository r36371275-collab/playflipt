# playflipt
flipper zero animation player( arch linux) 
# PlayFlipt on Arch Linux

PlayFlipt plays Flipper Zero `.bm` animations on an Arch Linux desktop. It renders the animation in a Flipper-style player and opens it as a looping GIF. The installer package includes a default animation.

## Requirements

- Arch Linux with a graphical desktop
- Internet access to install dependencies

## Download

On the GitHub repository page, select **Code → Download ZIP** and extract the archive. Keep the complete folder structure: `Install-playflipt.sh` must remain next to the `payload` directory.

## Install dependencies

Open a terminal and run:

```bash
sudo pacman -S --needed nodejs ffmpeg shared-mime-info desktop-file-utils xdg-utils
```

## Install PlayFlipt

Change to the extracted repository directory. For example:

```bash
cd ~/Downloads/playflipt
bash Install-playflipt.sh
```

The installer runs for your user and does not need `sudo`. It installs the player and bundled animation under `~/.local/share/betterpet-player`, registers `.bm` files, and creates a desktop launcher.

## Run PlayFlipt

- Double-click the desktop shortcut created by the installer to play the bundled animation. The current installer labels it **Play-Better-Pet**.
- To play another Flipper animation, double-click its `frame_0.bm` file. If asked which application to use, select **Better-Pet Animation Player** (the player installed by PlayFlipt).

The animation opens as a looping GIF in your default image viewer.

## Troubleshooting

- **Node.js not found:** install the dependencies above, then run `Install-playflipt.sh` again.
- **FFmpeg not found:** run `sudo pacman -S ffmpeg`, then rerun the installer.
- **The bundled animation is missing:** download and extract the entire repository, including `payload/default-animation`.

## Uninstall

Remove the per-user application and file association:

```bash
rm -rf ~/.local/share/betterpet-player
rm -f ~/Desktop/Play-Better-Pet.desktop
rm -f ~/.local/share/applications/betterpet-bitmap-viewer.desktop
rm -f ~/.local/share/mime/packages/betterpet-bitmap.xml
update-mime-database ~/.local/share/mime
update-desktop-database ~/.local/share/applications
```

These commands remove PlayFlipt's files and `.bm` association. They do not uninstall Node.js, FFmpeg, or the other system packages.
