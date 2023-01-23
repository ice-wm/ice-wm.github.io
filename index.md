---
title: IceWM
description: Window Manager
show_downloads: false
site_name: ice-wm.org
---

[![IceWM website logo][1]][2]

IceWM is a window manager for the X Window System.
The goal of IceWM is speed, simplicity,
and not getting in the user's way.
It comes with a taskbar with pager,
global and per-window keybindings
and a dynamic menu system.
Application windows can be managed by keyboard and mouse.
Windows can be iconified to the taskbar,
to the tray, to the desktop or be made hidden.
They are controllable by a quick switch
window (Alt+Tab) and in a window list.
A handful of configurable focus models are menu-selectable.
Setups with multiple monitors are supported by RandR and Xinerama.
IceWM is very configurable, themeable and well documented.
It includes an optional external background
wallpaper manager with transparency support,
a simple session manager and a system tray.
IceWM is available on popular Linux distributions like
Debian, Ubuntu, Arch, OpenSUSE, Gentoo, Slackware, CentOS,
antiX, NixOS, and also compiles on most \*BSDs.

### Software

IceWM was coded from scratch in C++ by Marko Maček since 1997.
It is now maintained at [Github][3].

### Releases

The [latest][15] released version is [3.3.1][4] (2023-01-23).

### Features

- Easy to use, simple and fast
- Standards compliant[&rarr;][22]
- Fully usable with keyboard
- Alt+Tab window switching
- Efficient resource usage
- Task bar (optional)
- Multiple workspaces
- Fully documented[&rarr;][23]
- A large number of themes[&rarr;][6]
- Usable with GNOME and KDE environments
- Regenerates menus when configuration changes
- Support for sound effects[&rarr;][24]
- Multiple focus modes
- Manual placement of windows option
- Autoraising of windows option
- Tooltips
- Configurable keybindings[&rarr;][25]
- Supports DockApps in a container
- Tabbed windows

### Screenshots

The [IceWM Screenshots Collection](screenshots/)

### Themes

IceWM is [themeable](themes/).
The visual appearance of icewm can be changed by a theme,
which is a collection of settings and small images.
More than 400 themes can be downloaded from [box-look.org][6].
[Extra](https://github.com/bbidulock/icewm-extra-themes/)
is a collection of 75 highlights.

### Translations

IceWM is [translated][8] into three dozen languages.
To improve the translation for your language at Weblate,
first register an account either [here][21] or [there][26],
then [update][8].

### Documentation

- [IceWM man pages](man/)
- [IceWM Manual](manual/)
- [Themes Howto](themes/)
- [IceWM FAQ](FAQ/)

### Bug Tracking

Report your icewm bugs on [Github][5].

### Install the latest release as follows

```bash
$ wget https://github.com/ice-wm/icewm/releases/download/3.3.1/icewm-3.3.1.tar.lz
$ tar -x --lzip -vpf icewm-3.3.1.tar.lz
$ cd icewm-3.3.1
$ ./configure --prefix=/usr
$ make
$ sudo make install
```
### Install from unreleased development source code

Gettext must be installed.

```bash
$ git clone https://github.com/bbidulock/icewm
$ cd icewm
$ ./autogen.sh
$ ./configure --prefix=/usr
$ make
$ sudo make install
```

If you have cmake, an alternative is:

```bash
$ git clone https://github.com/bbidulock/icewm
$ cd icewm
$ ./rebuild.sh -r --prefix=/usr
$ cd build
$ sudo make install
```

### Install package dependencies

To install all package dependencies
in one go use the following script.

```bash
$ wget https://ice-wm.org/scripts/os-depends.sh
$ sudo bash -x ./os-depends.sh
```

Verify package dependencies by:

```bash
$ pkg-config --modversion x11 xext xcomposite xdamage xfixes xrender xrandr xinerama xft fontconfig sm ice sndfile alsa ao gio-2.0 gio-unix-2.0 gdk-pixbuf-xlib-2.0 imlib2 librsvg-2.0 xpm libpng libjpeg
# or simpler:
$ ./rebuild.sh -d
```

### More installation and configuration

- [IceWM from scratch][10].
- [IceWM on arch wiki][16].
- [IceWM by arch user][17].

### Links

- [IceWM sound files](icewm-sounds).
- [IceWM release history](versions.html).
- [Compare window managers][11].
- List of [all window managers][12] and their [helper programs][27].
- [Extended window manager hints][19].
- [The anatomy of the modern window manager][18] (thesis).

### License

IceWM is released under the terms of the GNU Library General Public License.

### Donate

Contribute to ongoing development and support of IceWM by [donating][14].

[1]: images/logom.jpg "ice-wm.org"
[2]: https://ice-wm.org
[3]: https://github.com/bbidulock/icewm
[4]: https://github.com/ice-wm/icewm/releases/download/3.3.1/icewm-3.3.1.tar.lz
[5]: https://github.com/bbidulock/icewm/issues
[6]: https://themes.ice-wm.org
[8]: https://l10n.opensuse.org/projects/icewm/icewm-1-4-branch/
[9]: https://sandbox.cz/~covex/icewm/iceicons/iceicons-default-0.10.0.tar.gz
[10]: http://www.linuxfromscratch.org/blfs/view/svn/x/icewm.html
[11]: https://en.wikipedia.org/wiki/Comparison_of_X_window_managers
[12]: https://www.gilesorr.com/wm/table.html
[13]: https://ice-wm.org/gnome-wm-hints/
[14]: https://gijsbers.github.io/donate/
[15]: https://github.com/ice-wm/icewm/releases/latest
[16]: https://wiki.archlinux.org/index.php/IceWM
[17]: https://www.archlinuxuser.com/2013/02/how-to-install-configure-icewm-window.html
[18]: https://www.cs.ru.nl/bachelors-theses/2019/Max_van_Deurzen___4581903___The_anatomy_of_the_modern_window_manager_-_a_case_study_for_X_in_an_Agile_manner.pdf
[19]: https://specifications.freedesktop.org/wm-spec/wm-spec-latest.html
[20]: https://projects.mini-dweeb.org/attachments/download/4/report.pdf
[21]: https://l10n.opensuse.org/accounts/register/
[22]: https://github.com/ice-wm/icewm/blob/master/COMPLIANCE
[23]: https://ice-wm.org/man/
[24]: https://ice-wm.org/man/icesound
[25]: https://ice-wm.org/man/icewm-keys
[26]: https://idp-portal.suse.com/univention/self-service/#page=createaccount
[27]: https://www.gilesorr.com/wm/helpers.html

[ vim: set ft=markdown sw=4 tw=80 nocin nosi fo+=tcqlorn: ]: #
