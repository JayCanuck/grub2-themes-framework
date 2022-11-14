![banner](banner.png?raw=true)

> Fork of [vinceliuice/grub2-themes](https://github.com/vinceliuice/grub2-themes) which has been tailored for the [Framework laptop](https://frame.work/). Adds a default `framework` screen size option and a custom minimalist default `framework` theme (see preview below).  All existing theme backgrounds also updated for Framework laptop resolution.  Includes fanart from [dev-boom/framework-fan-art](https://github.com/dev-boom/framework-fan-art)


## Installation:

Usage:  `sudo ./install.sh [OPTIONS...]`

```
  -t, --theme     theme variant(s)          [framework|tela|vimix|stylish|whitesur]       (default is framework)
  -i, --icon      icon variant(s)           [color|white|whitesur]                        (default is color)
  -s, --screen    screen display variant(s) [framework|1080p|2k|4k|ultrawide|ultrawide2k] (default is framework)
  -r, --remove    Remove theme              [framework|tela|vimix|stylish|whitesur]       (must add theme name option, default is framework)

  -b, --boot      install theme into '/boot/grub' or '/boot/grub2'
  -g, --generate  do not install but generate theme into chosen directory       (must add your directory)

  -h, --help      Show this help
```

_If no options are used, a user interface `dialog` will show up instead_

### Examples:
 - Install Tela theme on 2k display device:

```sh
sudo ./install.sh -t tela -s 2k
```

 - Install Tela theme into /boot/grub/themes:

```sh
sudo ./install.sh -b -t tela
```

 - Uninstall Tela theme:

```sh
sudo ./install.sh -r -t tela
```

## Issues / tweaks:

### Correcting display resolution:

 - On the grub screen, press `c` to enter the command line
 - Enter `vbeinfo` or `videoinfo` to check available resolutions
 - Open `/etc/default/grub`, and edit `GRUB_GFXMODE=[height]x[width]x32` to match your resolution
 - Finally, run `grub-mkconfig -o /boot/grub/grub.cfg` to update your grub config

### Setting a custom background:

 - Make sure you have `imagemagick` installed, or at least something that provides `convert`
 - Find the resolution of your display, and make sure your background matches the resolution
   - 2256x1504 >> framework
   - 1920x1080 >> 1080p
   - 2560x1080 >> ultrawide
   - 2560x1440 >> 2k
   - 3440x1440 >> ultrawide2k
   - 3840x2160 >> 4k
 - Place your custom background inside the root of the project, and name it `background.jpg`
 - Run the installer like normal, but with -s `[YOUR_RESOLUTION]` and -t `[THEME]` and -i `[ICON]`
   - Make sure to replace `[YOUR_RESOLUTION]` with your resolution and `[THEME]` with the theme

## Contributing:
 - If you made changes to icons, or added a new one:
   - Delete the existing icon, if there is one
   - Run `cd assets; ./render-all.sh`
 - Create a pull request from your branch or fork
 - If any issues occur, report then to the [issue](https://github.com/vinceliuice/grub2-themes/issues) page

## Preview:
![preview](preview.png?raw=true)

## Documents

[Grub2 theme reference](http://wiki.rosalab.ru/en/index.php/Grub2_theme_/_reference)

[Grub2 theme tutorial](http://wiki.rosalab.ru/en/index.php/Grub2_theme_tutorial)

