---
title: IceWM
description: Window Manager
---

[![IceWM website logo][1]][2]


IceWM is a window manager for the X Window System.
The goal of IceWM is speed, simplicity,
and not getting in the user's way.

IceWM is available on popular Linux distributions
like Debian, Ubuntu, Arch, OpenSUSE and Slackware.

### Software

IceWM has been coded from scratch in C++.

It is maintained at [Github][3].

### Releases

The latest released version is [1.4.2][4].

### Features

- Easy to use, simple and fast
- Standards compliant
- Fully usable with keyboard
- Alt+Tab window switching
- Efficient resource usage
- Task bar (optional)
- Multiple workspaces
- Fully documented
- A large number of themes
- Usable with GNOME and KDE environments
- Menus are automatically redefined when configuration changes
- Sound support
- Multiple focus modes
- Manual placement of windows option
- Autoraising of windows option
- Tooltips
- Configurable keybindings

### Screenshots

The [IceWM Screenshots Collection](screenshots)

### Themable

IceWM is themeable. Every setting from the preferences file can be changed
by a theme. This includes titlebars, borders, icons, events, the taskbar,
etc. IceWM supports pixmapped and non-pixmapped themes and comes with an
example theme for all the theme types (warp3, warp4, win95, motif, nice,
pixmap, metal, gtk) that IceWM supports.
Currently more than 400 themes can be downloaded from
[box-look.org][6].

### Translations

IceWM is [translated][8] into three dozen languages.

### Documentation

- [IceWM Manual](manual)
- [Themes Howto](themes)
- [IceWM FAQ](FAQ)
- [IceWM man pages](man)

### Bug Tracking

See [issues on Github][5].

### Install from source

```bash
$ git clone https://github.com/bbidulock/icewm
$ cd icewm
$ ./autogen.sh
$ ./configure --enable-gdk-pixbuf --prefix=/usr
$ make
$ sudo make install
```

### Links

- [IceWM sound files](icewm-sounds).
- [IceWM release history](versions.html).
- [IceIcons][7] - has [icons][9] designed for IceWM.

### License

IceWM is released under the terms of the GNU Library General Public License.

[1]: images/logom.jpg "ice-wm.org"
[2]: https://ice-wm.org
[3]: https://github.com/bbidulock/icewm
[4]: https://github.com/bbidulock/icewm/releases
[5]: https://github.com/bbidulock/icewm/issues
[6]: https://www.box-look.org/browse/cat/142/ord/latest/
[7]: https://sandbox.cz/~covex/icewm/iceicons/
[8]: https://l10n.opensuse.org/projects/icewm/icewm-1-4-branch/
[9]: https://sandbox.cz/~covex/icewm/iceicons/iceicons-default-0.10.0.tar.gz
