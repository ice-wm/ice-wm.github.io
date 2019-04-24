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
IceWM is very configurable, themable and well documented.
It includes an optional external background
wallpaper manager with transparency support,
a simple session manager and a system tray.
IceWM is available on popular Linux distributions like
Debian, Ubuntu, Arch, OpenSUSE, Gentoo, Slackware, CentOS
and also compiles on most \*BSDs.

### Software

IceWM was coded from scratch in C++ by Marko Maček since 1997.
It is now maintained at [Github][3].

### Releases

The [latest][15] released version is [1.5.4][4] (2019-04-23).
Compared to version 1.4.2 (2017-07-30),
this release contains many bugfixes,
many portability fixes and updated translations.
A new quickswitch, new hotkeys, new focus behavior `FocusCurrentWorkspace`,
new theme option `TaskbuttonIconOffset` which is used
in theme [Outside-ice][10], SVG support for gdk-pixbuf.
Change focus model without restart. Change preferences via menus.
Improved locating and loading of icons. Extended window list menus.
Switch windows of same class. Monitoring applet options.
`MouseWinLower` hotkey. Omit borders for shaped applications.
Shuffle and cycle backgrounds periodically. A new website ice-wm.org.
Quickswitch can be either horizontal or vertical.
Easily change focus or workspaces by mouse wheel.
A gui to select `RandR` settings. A new compliant menu generator.
The monitoring applets require a lot less processor time.
The improved system tray supports more applications.
Mailbox monitoring was overhauled and now supports `TLS/SSL` connections
to POP and IMAP servers, Gmail and Maildirs.
Support for 32-bit visuals and compositing managers was added.
The order of buttons and icons on taskbar, tray bar and system tray
is now fully configurable.
Many new manual pages have been written and documentation is fully updated.
The addressbar now has a recallable history of previous commands.
`PagerShowPreview` is now the default.
IceWM now supports `_NET_WM_PING`, `_NET_REQUEST_FRAME_EXTENTS`,
`_NET_WM_STATE_FOCUSED` and `_NET_WM_WINDOW_OPACITY` protocols.
Support for sounds on guievents was updated.

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

The [IceWM Screenshots Collection](screenshots/)

### Themes

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

- [IceWM man pages](man/)
- [IceWM Manual](manual/)
- [Themes Howto](themes/)
- [IceWM FAQ](FAQ/)

### Bug Tracking

See [issues on Github][5].

### Install the latest release as follows

```bash
$ curl -L -s https://github.com/ice-wm/icewm/releases/download/1.5.4/icewm-1.5.4.tar.xz | tar Jxvpf -
$ cd icewm-1.5.4
$ CC=gcc CXX=g++ ./configure --prefix=/usr
$ make
$ sudo make install
```
### Install from unreleased development source code

```bash
$ git clone https://github.com/bbidulock/icewm
$ cd icewm
$ ./autogen.sh
$ ./configure --enable-gdk-pixbuf --prefix=/usr
$ make
$ sudo make install
```
### Install package dependencies

To install all required package dependencies
in one go use the following script.

```bash
$ wget https://ice-wm.org/scripts/os-depends.sh
$ sudo bash -x ./os-depends.sh
```

### Links

- [IceWM sound files](icewm-sounds/).
- [IceWM release history](versions.html).
- [IceIcons][7] - has [icons][9] designed for IceWM.
- [Compare window managers][11].
- [List all window managers][12].
- [GNOME window manager hints][13].

### License

IceWM is released under the terms of the GNU Library General Public License.

### Donate

Contribute to ongoing development and support of IceWM by [donating][14].

[1]: images/logom.jpg "ice-wm.org"
[2]: https://ice-wm.org
[3]: https://github.com/bbidulock/icewm
[4]: https://github.com/ice-wm/icewm/releases/download/1.5.4/icewm-1.5.4.tar.xz
[5]: https://github.com/bbidulock/icewm/issues
[6]: https://themes.ice-wm.org
[7]: https://sandbox.cz/~covex/icewm/iceicons/
[8]: https://l10n.opensuse.org/projects/icewm/icewm-1-4-branch/
[9]: https://sandbox.cz/~covex/icewm/iceicons/iceicons-default-0.10.0.tar.gz
[10]: https://www.box-look.org/p/1018109/
[11]: https://en.wikipedia.org/wiki/Comparison_of_X_window_managers
[12]: https://www.gilesorr.com/wm/table.html
[13]: https://ice-wm.org/gnome-wm-hints/
[14]: https://gijsbers.github.io/donate/
[15]: https://github.com/ice-wm/icewm/releases/latest

[ vim: set ft=markdown sw=4 tw=80 nocin nosi fo+=tcqlorn: ]: #
