# Suckless terminal st

## installation

```
git clone https://github.com/LukeSmithxyz/st
cd st
sudo make install
```

## configuration

### emoji support in ubuntu

Use symbola fonts for emoji, because joypixels makes st crash:

```
 static char *font = "mono:pixelsize=14:antialias=true:autohint=true";
-static char *font2[] = { "JoyPixels:pixelsize=10:antialias=true:autohint=true" };
+static char *font2[] = { "Symbola:pixelsize=12:antialias=true:autohint=true", "PowerlineSymbols:pixelsize=12:antialias=true:autohint=true" };
 static int borderpx = 2;
```

install symbola fonts

```bash
sudo apt install fonts-symbola
```

### emoji support in arch linux

If st crashes when viewing emojis, install libxft-bgra from the AUR.

```bash
yay -S libxft-bgra
```
