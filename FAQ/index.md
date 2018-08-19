---
title: IceWM FAQ and Howto
---

### Authors
- Adam Pribyl
- Markus Ackermann
- Josef 'Jupp' Schugt


### Last modified

2005/05/24, 21:11 CEST


### General FAQ - ReadMeFirst


As IceWM is lightwieght it still does a lot. **If you are looking for
some option go throught *preferences* file.** It is well constructed
and you usually find what you are searching - e.g. you want to change some
quickswitch option then try to grep "QuickSwitch" from preferences.
Therefore it makes no sense to describe all of the preferences here.

### Fulltext search

If you want fulltext search of this FAQ use a [text version](IceWM-FAQ.txt).

### The most Frequently Asked Questions with short answers


This is list of the most frequently asked quiestions with short answers.
Usually you can find more explaining answer in following chapers.

### IceWM does not start icewmbg, startup etc. How should I start IceWM? "icewm-session"
### Is that possible to place icons on desktop using PURE IceWM? "No."
### Where are icewm files? "Depends - locate *icewm."
### How to change default theme? ".icewm/theme", Theme="thenicest/default.theme".
### Does IceWM knows dynamicly created desktops or 2D desktops? No.
### Is there a way to group similar applications in the toolbar when minimized? No.
### How can I disable the taskbar (or toolbar) in IceWM? preferences, ShowTaskBar=0
### Is there any way to have the time and date show in the taskbar? "Yes. man date || strftime"
### Is there a button to minimize all windows?  IceWM > 1.2.13, preferences, TaskBarShowShowDesktopButton=1 or use alt+shift+F9.
### How can I autostart apps at X && IceWM start? Use .Xsession || .xinitrc || .Xclients || ".icewm/startup."
### Is it possible to add submenus to the menu? "Yes. file menu; format: menu name icon {content}."
### How to disable Alt+drag feature? preferences, ClientWindowMouseActions=0
### How is that with WM_CLASS and windowptions? "This doc should reflect correct status."

### Introduction


In this section I give a short description of what IceWM is.

### What is IceWM?


IceWM is a **window manager for** the **X** window system.
It is designed to be **small, fast, lightweight,** and to
emulate the **look and feel of Motif, OS/2 and Windows.**

While it is **very configurable,** it is not pathologically so
(like Enlightenment or FVWM). In short, IceWM provides a
**customizable look** with a relatively **consistent
feel.**

Now that you know what IceWM is and are still reading on you are
obviously interested in using it. To use a program you will first
need to have it. The obvious question is:

### Where to get it?

See [here](/).

### Under which operating systems does it run?


IceWM successfully ran under (in alphabetical order):


- **AIX 4.3.3**
- **Digital Unix (Compaq Tru64 Unix)**
- **FreeBSD**

- **Linux on DEC Alpha (64 bit architecture)**
- **Linux on Intel compatibles (32 bit architecture)**
- **NetBSD**

- **OpenBSD**

- **Solaris**



### Minimal Requirements


A default IceWM installation just depends on the X window system (any X
window system will do, no matter how old or from which vendor)  and libXpm
and therefore should run sufficiently fast even on an old 386, a sparc IPC
or any other box capable of running X. For some of the nifty features like
shaped borders, gradient frames and gradient menus it might help to have a
computer which is slightly faster or which doesn't have an ancient X
version.

### Installation


Now you have the IceWM source package at hand and will want to
install it. So the next question will be:

### How to install IceWM from RPM


The IceWM developers provide RPM packages for all new releases independently
from the distributions which use this package format. IceWM's RPM
distribution is split into several files. You need icewm-x.y.z-v.rpm.
Optionaly you can download others like icewm-themes, icewm-l10n and
icewm-menu-gnome.


### How to compile and install IceWM from source?


IceWM (0.9.3x and up) uses the standard
GNU autoconf tool, so installation of IceWM is much the same as the
installation of any other package that uses this tool.

First you **untar** the package using

```
    tar xzf icewm-1.2.x.tar.gz
```

then you **change** to the created **directory** using

```
    cd icewm-1.2.x
```

IceWM comes with a configure script that can be supplied with several
compile-time options. To see them listed use

```
    ./configure --help
```

After you have decided which (if any) options you want to set,
**run** the `configure` script:

```
    ./configure [option ...]
```

Assuming that the configure script exited successfully, you should
then **compile** IceWM using

```
    make
```

which will build IceWM with the options specified by the configure
script. If everything compiles successfully, you can now
**install** IceWM on your machine by entering

```
    make install
```

**Note:** To do so you will typically need to become
**root** (at least if you didn't supply an install directory you
as a user have write access to - this you can change in Makefile).

Now you have an IceWM binary sitting on your disk. Is that what you
really want? Obviously not, you want to *run* IceWM. The next
section describes how to set up IceWM as your default window manager.


### How to make IceWM my default window manager?


In order to run IceWM, you must **assure** that the
**executable** (called `icewm`) **is
in** your **path.** You should then **add IceWM to**
your **X start-up script** (which could be
`.xinitrc`, `.xsession` or
`.Xclients`).

**Note:** Supplying the full path to IceWM isn't sufficient - if
IceWM isn't in your path, restarting it will fail (even if you don't do
this by hand it is done automatically on changing the theme).

Which of the scripts mentioned above is the right one mainly depends
on whether you manually start X (using `startx`)
or have X running all the time.

First I explain what you need to do if you manually start X. Then I
address the case "X is running all the time" (which means
that you log in via `xdm` or something like that).
Finally I describe what both cases have in common.

### Running IceWM at X startup


If you use `startx` to start up X then you run
your window manager from the `.xinitrc` file.

### Running IceWM after graphical login


If your system has a graphical login (X is already running while you
log in) you are using a display manager such as
`xdm`, `kdm` or
`gdm`. In this case `.xinitrc`
has no effect (it is not read in by `xdm`). You
must instead use a `.xsession` file.

**Hint:** It is absolutely no problem to have a
`.xsession` and a `.xinitrc`
file (which is especially useful for inhomogeneous networks).

Mandrake users repeatedly reported that their `.xsession` wasn't read
and no applications started. To work around that in the `kdm` login
interface choose `Default` and add IceWM as the last
entry to your `.xsession`.

### Besides the differences


You might have noticed that - besides being  used in different
cases - `.xsession` and
`.xinitrc` are essentially the same. On some
systems they are in fact the very same file which is called
`.Xclients` with `.xinitrc` and
`.xsession` both being symbolic links to this
file.

Irrespective which start script you use (`.xsession`,
`.xinitrc` or `.Xclients`) it must
be executable. This may be achieved by issuing the following command:

```
    chmod u+x ~/.filename
```

A minimalist's start-up file consists of only the command to start
the window manager (in our case `icewm`). Most geeky people
add other stuff to the file to make it look more complicated and
confuse beginners.

Though that may be the reason for some of us, the greater majority
add commands to customize X and to start some programs on login
(typical example: an `xterm`)

The following is a (reasonable) `.xinitrc` file
used as an example by Marko:

```
    #-----------------------------------------------------------
    # .xinitrc
    #-----------------------------------------------------------

    # run profile to set $PATH and other env vars correctly
    . $HOME/.bash_profile

    # setup background
    xsetroot -solid '#056'

    # setup mouse acceleration
    xset m 7 2

    # run initial programs
    xterm &

    # start icewm, and run xterm if it crashes (just to be safe)
    exec icewm || exec xterm -fg red

    #-----------------------------------------------------------
```

**Note:** To run IceWM, the `icewm` command
needs to be executed. This means that all programs that are run
before starting `icewm` either have to terminate
immediately or to run in background. Also, don't
`exec` them because that terminates execution of
`.xinitrc.`

### IceWM > 1.2.13


Beginning with IceWM 1.2.13 there is a binary `icewm-session`.
This binary helps you to handle all IceWM subparts (icewmbg, icewm, icewmtray, startup, shutdown started in this order).
Therefore you can use `icewm-session` to start IceWM.
`icewm` now starts only window manager itself.


If you want to start only some parts of the IceWM, then you can add them to
your `.xsession` or similar file before `exec icewm`, otherwise it is
enough to use only `exec icewm-session`.

### Configuration


Congratulations! Now you have IceWM up and running. You don't like
the default look? Don't worry: This section is on customizing IceWM.

As it is the case with most Linux and Unix programs IceWM can be
configured using plain text config files.

### You mean I have to edit these files?

There is a lot of utilities nowadays. See utilities section -
"Tools for IceWM".

The config files need to be changed if you want to change IceWM's
behavior.  This does not necessarily mean that you have to use an
editor for this - graphical configuration tools for IceWM are
available, although IceWM doesn't feature in-built configuration. More
about these tools in the Utilities section.
Still hand editing of these files is most effective and you can find even more
than you are looking for.
To notify IceWM about the
changes you've made just send it a SIGHUP or restart it from the Logout
menu.

### Where are the configuration files?


You could not find the config files? Maybe you were looking in wrong
places - the location depends upon the method you used to install
IceWM.

In a plain vanilla source install, the global version of the files
will be located in `/usr/local/share/icewm`. If
you installed the standard RPM, they will be in
`/usr/X11R6/lib/X11/icewm/` or `/usr/local/lib/Xll/icewm/`. The system wide
configuration files for the Debian package seem to be in
`/etc/X11/icewm/`. Generaly you can try to use `locate icewm` command to find parts of IceWM.

However, if you wish to make a configuration of your own you should
not edit these global config files but create a subdirectory of your
home directory called `~/.icewm/`. Copy the system
wide files to your local `.icewm` directory and
edit these copies.

**Note:** You may have to alter the permissions of the copies in
order to read and write to them.

### The configuration files


You can customize IceWM by editing the following configuration files:

- `"menu"`
    Controls the contents of the `start` menu
- `"preferences"`
    Controls the general behavior of IceWM
- `"keys"`
    Controls which additional key combos are available to users
- `"toolbar"`
    Controls the row of launcher icons on the taskbar and has the
    same syntax as the menu file
- `"winoptions"`
    Controls the behavior of individual applications (as identified
    by the names of their respective windows)
- `"startup"`
    Script or command (must be executable) executed by `icewm-session` on startup
- `"theme"`
    IceWM theme path/name.
- `"prefoverride"`
    To override theme preferences.


### menu


The `menu` file controls the contents in your menu (You knew that,
right?). It has the following syntax:

```
    prog Program Icon app -with -options
```

`prog` is a keyword, telling IceWM that it's a program entry. Other keywords
are `separator` to draw a separator and
```
menu Xyz folder_icon {
  prog ...
}
```
to open a new sub menu called Xyz. `Program` is
the name which will be shown in the menu. Enclose it in apostrophes if you
need more than one word here. `Icon` will be used as the menu
entry's icon, if a corresponding image is found in IceWM's IconSearchPath.
And finally `app -with -options` is what's going to be started if
a user chooses this entry.

Note that the menu only shows entries which are found in your PATH, IceWM is
clever enough to omit non-usable entries.

There are also two advanced options `runonce` and
`menuprogreload "title" icon_name timeout program_exec`

`runonce` is used to start application only once - if its already running do not start it upon
clicking. Runonce needs some other options - see manual.
`menuprogreload` is used to created dynamic menus:
timeout is integer value, it specifies minimum time
interval (in seconds) between menu reloading. Zero value means
updating menus every time when user click it.

This is an example by the author of this feature:

```
#!/bin/sh
#
# icewm-ps-menu.sh - Process menu for IceWM.
#
# Written by Konstantin Korikov.
#
# This is test script that generates IceWM menu
# with running user process list. It uses menuprogreload
# feature of IceWM menu. To use this script, add followed
# line to ~/.icewm/menu or  ~/.icewm/toolbar
#
#   menuprogreload ps - 0 icewm-ps-menu.sh
#

if [ $# = 1 ]; then
        set `ps -p $1 --no-header -o pid,%cpu,%mem,time`
        echo "prog 'CPU: $2%' - true"
        echo "prog 'MEM: $3%' - true"
        echo "prog 'TIME: $4' - true"
        echo "separator"
        for i in HUP INT KILL TERM; do
                echo "prog $i - kill -$i $1"
        done
else
        ps -aU `id -ru` --no-headers -o '%p|%c' |
        awk -F '|' -v sc="$0" \
          '{ printf("menuprogreload \"%d %s\" - 0 %s %d\n", $1, $2, sc, $1) }'
fi
```

Some more can be found in patch 993038 in IceWM patch tracker.


### preferences


The `preferences` file is the main configuration file. The default
file is pretty much self documenting, so go and have a look. In case you
ever wondered about themes: they can define all the options you can use in
this file - and their definitions **override** all your personal customization!

### keys


In the `keys` file one can define shortcuts for starting programs.
The existing entries make clear what one has to define.

### toolbar


The `toolbar` file defines some buttons which can be clicked next to
the menu in the toolbar. It uses the same format as the menu file.
You can also have folders in the toolbar. The easiest way to do that
is simply by copying a menu from the /menu file over to the /toolbar file.

### winoptions


The `winoptions` file can be used to define the appearance of X
applications like on which desktop they should appear, if should have a
border, menu, titlebar, etc.

### startup


The `startup` is a script (must be executable) that is executed by
`icewm-session` command on startup.

It can look like this:
```
#!/bin/sh
idesk&
(sleep 2; psi&)&
```

Do not forget to make this file executable
```
$ chmod +x startup
```

Note: It is recommended to use '#!/bin/sh' as the first line, to use /bin/sh
to execute the script.

Also make sure all applications are starting at background (&).

### theme


The `theme` file is new from IceWM 1.2.10. It specifies which
theme should be used
```
Theme=myfavorittheme/default.theme
#Theme=myfavorittheme/default.theme
```

# contains theme history (max. 10 lines).


The `theme` file is changed every time you
switch theme in menu and selected theme is therefore used after IceWM restart.

### prefoverride


The `prefoverride` file is new from IceWM 1.2.12. In this file you can
specify any preference which will override any preference specified by theme or
anything else. This is introduced to solve troubles with order of preferences
interpretation and give a user possibility to customize global things he wants to
have allways the same.


### Customizing The Behavior


IceWM's reactions on your actions can be pretty much configured as you like
it. You can choose which focus model you like, what should happen on
mouse clicks on the titlebars, or which mouse button calls which menu when
clicked on the desktop.

### What are the focus models good for?


To answer this question it is a good idea to first take a look at the
four general focus models that are implemented by IceWM:


- `ClickToRaise`
    When a window is clicked, it is raised and activated. This is the
    behavior of Win95 and OS/2.
- `ClickToFocus`
    A Window is raised and focused when titlebar or frame border is
    clicked and it is focused but not raised when the window interior
    is clicked.
- `PointerFocus`
    When the mouse is moved, focus is set to window the mouse is
    pointing at. It should be possible to change the focus with the
    keyboard when the mouse is not moved.
- `ExplicitFocus`
    When a window is clicked, it is activated but not raised. New
    windows do not automatically get the focus unless they are
    transient windows for the active window.


*"A window is raised"* is telling and needs no
further explanation.

*"A window is activated, is focused, gets the
focus,..."* means that input (e. g. keystrokes) now are sent
to that window.

**In short:** The focus model controls what you have to do to
make a window pop up and to have it listen to what you type.

### Use UseRootButtons and ButtonRaiseMask


`UseRootButtons` and
`ButtonRaiseMask` are so called **bitmask
options.**

This concept is e.g. used by `chmod` where
`"4"` stands for read access, `"2"`
for write access and `"1"` for execute (or change
directory) access and you add up the relevant numbers to control the
file access.

As far as `UseRootButtons` and
`ButtonRaiseMask` are concerned,
`"1"` stands for the first mouse button,
`"2"` for the second one and `"4"`
for the third one. The following list shows which number stands for
which combination of mouse buttons:

```
    ---------------------------------
     Value   Stands for
    ---------------------------------
       0     No mouse button at all
       1     Button 1
       2     Button 2
       3     Buttons 1 and 2
       4     Buttons 3
       5     Buttons 1 and 3
       6     Buttons 2 and 3
       7     All three mouse buttons
    ---------------------------------
```

Any value greater than seven has the same effect as seven.
`UseRootButtons` controls which buttons call up a
menu when clicked on an unoccupied region of the desktop.
`ButtonRaiseMask` determines which buttons will
raise a window when clicked on that window's title bar.

### Set the mouse button a menu which is bound to


There is an option for each of the root menus which controls which
button is bound to that menu.

```
    -----------------------------------------
     Option Name            Controls
    -----------------------------------------
     DesktopWinMenuButton   Window menu
     DesktopWinListButton   Window list
     DesktopMenuButton      Application menu
    -----------------------------------------
```


The value of each option determines the button to which the
corresponding menu is bound according to the following scheme:

```
    -----------------------------
     Value   Stands for
    -----------------------------
       0     No mouse button
       1     Left mouse button
       2     Right mouse button
       3     Middle mouse button
      4-6    Other buttons
    -----------------------------
```

### Setting the lock command


By default IceWM uses `xlock` (without any
argument) to lock your screen. There may be several reasons for using
a different lock command:


- There is no `xlock` on your machine.
- `xlock` tends to crash on your machine either
    leaving you locked out (best case) or unlocking your session
    (worst case).
- `xlock` has some CPU intensive modes compiled in that
    interfere with your SETI@HOME session.


It is very easy to set a lock command: Simply add

```
    LockCommand="xlock -mode blank"
```

to your `$HOME/.icewm/preferences` and
`xlock` will run in `blank` mode (which
shows nothing but a black screen).

The example was chosen on purpose: Using this mode you have the best
chance of your monitor going asleep (enter power saving mode).

### Can the taskbar applet monitor ethernet (or isdn) instead of my modem?


In the `preferences` file just change the option
`NetworkStatusDevice` to read

```
    NetworkStatusDevice="eth0"
```

Replace `"eth0"` by `"ippp0"` to monitor
ISDN connections. AFAIK eth0 support is limited to Linux and *BSD since
commercial Unices tend to use another format for their network interfaces.

### Can the taskbar applet monitor more devices?


In the `preferences` file just change the option
`NetworkStatusDevice` to read

```
    NetworkStatusDevice="eth0"
```

Replace `"eth0"` by `"eth0 ppp0"` to monitor
eth0 and ppp0.


### I'd like to check remote mailboxes with the taskbar mail applet


No problem either. Your `MailBoxPath` in the `preferences`
file should read

```
    MailBoxPath="imap://username:password@remote.host"
```

Replace `imap` with `pop` or `pop3` if necessary. Be sure to have save
permissions on the preferences file so nobody else can get your mail password.


### How do I disable Alt+mouse drag to move the window to send Alt+mouse to application


To send all Alt+key keys to application you can use window option `window_class.fullKeys: 1`
However the preference you looking is `ClientWindowMouseActions=0`. This disable
Alt+mouse drag to move window for all IceWM handled windows.


### Control The Look and Behavior Of Applications


This section is about how you can make windows appear on a certain
workspace, have them displayed without a border or titlebar, or put them
above or under other windows. All this can be accomplished using the
`winoptions` preferences file, some of it even interactively.

### Assign an option to a given application


Assigning a particular option (icon, default layer, default
workspace, etc.) to a given application or application window can be
done as follows:

First, you should acquire the `"WM_CLASS"` descriptor
using `xprop.` Simply run

```
    xprop |grep WM_CLASS
```

in an XTerm. The first item is the window name and the second item it
the window class. You can then add the desired options to your
`winoptions` file. Entries in that file have one
of the following formats:

```
    name.class.option: value
    class.option:      value
    name.option:       value
```

The `"WM_CLASS"` for a Netscape Navigator window is

```
    "Navigator", "Netscape"
```

To assign the icons `"navigator_*.xpm"` to the
Netscape Navigator window, use this option:

```
    Navigator.Netscape.icon: navigator
```

The other options work according to roughly the same pattern. The list
of winoptions you can find in the [manual](/manual/)
 chapter about Window Options.


### How do I make a window stay on top?


There are two slightly different ways to do this. Use whatever suits your
need. Option one: the window always stays on top of any other windows. Set
the following option `name.class.layer: onTop`.
Option two: the window sits in a rectangular zone of the desktop where no
other windows can be placed: Use the doNotCover option:
`name.class.doNotCover: 1`. By the way: this is how the taskbar or
the GNOME panel work. It's a good idea to use this on gkrellm, your icq
client, or other monitoring tools you'd always like to have in view.

### Have windows iconified/maximized as soon they are mapped


There may be programs that you either want to start up iconified or
maximized. Until now, there is no possible entry in your
`winoptions` file that iconifies or maximizes a
windows of a given name or class as it is mapped.

Fortunately some programs (like Netscape) have a command line option
to be started iconic and most X program support
`"-geometry"` to specify a default window size.

### How to make windows appear on certain workspace?


Either use `winoptions` and define

```
xmms.workspace: 7
Mozilla.workspace: 9
```

This allways starts xmms on workspace 7 and Mozilla on workspace 9, keep in
mind, IceWM starts counting at 0. IceWM will switch to the nominated
workspace on every start of these programs.

Or you can use `icesh`:

```
icesh -class xeyes setWorkspace 0
```

This move xeyes to my workspace 0.


### Using IceWM With The Keyboard


It should be possible to control everything by keyboard. Here we show some
of the not so obvious ways to achieve important window managing tasks only
with keystrokes.

### Basic predefined keyboard shortcuts


```
Alt-Tab = Switches between the open windows
Alt-F4 = Closes a window
Alt-F9 = Minimizes a window
Alt-F10 = Maximizes a window
Alt-F12 = Rolls the window up
(leaving only the titlebar visible, press Alt-F12 again and the window rolls back down)
Alt-Shift-F10 = Maximizes the window vertically
Alt-Ctrl-arrow left = Changes workspaces from 1-12
Alt-Ctrl-arrow right = Changes workspaces from 12-1
Alt-Ctrl-Esc = Opens the  window list
Ctrl-Esc = Opens the  menu
```


### Switching Desktop using keyboard


You are accustomed to a window manager that allows you to switch
between virtual desktops using your keyboard? IceWM allows for this,
too.

Before I describe how to switch between virtual desktops I want to
describe how to control their number. Imagine that your
`$HOME/.icewm/preferences` has a row reading

```
    WorkspaceNames="1","2","3","4","5","6","7","8","9","0"
```

This setting results in ten virtual desktops and ten buttons in your
taskbar looking like this:

```
    +---+---+---+---+---+---+---+---+---+---+
    | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 0 |
    +---+---+---+---+---+---+---+---+---+---+
```

If you name less desktops you obtain less if you name more you get
more.

For understanding how switching virtual desktops works in IceWM you
should imagine that the buttons represent your virtual desktops and
that these desktops are arranged in one long row.

You can imagine two ways of switching between desktops:


- Switching to desktop number seven
- Switching to the desktop on the left/right of the present one


IceWM has both ways:


-  To switch to desktop number *n* you simply press
    `"Ctrl-Alt-n"`
-  To switch one desktop to the left you press
    `"Ctrl-Alt-Cursor_Left"`
-  To switch one desktop to the right you press
    `"Ctrl-Alt-Cursor_Right"`


`"Cursor_Left"` `("Cursor_Right")`
represents the key that moves your cursor one character to the left
(right).

If you are using `"Ctrl-Alt-Cursor_Right"` on the
rightmost desktop you switch to the leftmost desktop. From here,
`"Ctrl-Alt-Cursor_Left"` brings you back to the
rightmost desktop.

*What if you have more than ten virtual desktops?* In this
case `"Ctrl-Alt-n"` will only work for the first ten
desktops while switching to the left or right still works for all
desktops.

IceWM has another feature to offer: You may not only use your
keyboard to switch desktops, you can also use it to move windows from
one desktop to another. The next section is on this (you should read
it, too).

**Note:** To switch desktops when moving mouse on desktop edges use preference:
```
EdgeSwitch=1
```
then you can change workspaces automatically by moving your cursor to the left/right edges of your screen.


### Moving windows between desktops using keyboard


In the previous section I explained how to switch between desktops.
If you didn't already read it you should do it now because moving the
active window to another desktop works almost the same like switching
to a certain desktop. All you have to do is pressing the
`"Shift"` while switching to the desktop:


-  To move a window to desktop number *n* you simply
    press `"Ctrl-Alt-Shift-n"`
-  To move a window one desktop to the left you press
    `"Ctrl-Alt-Shift-Cursor_Left"`
-  To move a window one desktop to the right you press
    `"Ctrl-Alt-Shift-Cursor_Right"`


### Using the CLI (command line interface)


You should run IceWM with `"TaskBarDoubleHeigth=1"`
because that will enable the CLI (see *"What is the blank bar in the task bar good for?"* for some
more information).

The CLI is especially useful if you rather frequently need to access
man pages and don't want to have xman hang around all the time.

If you enter `man perl` and press
`"Ctrl-ENTER"` an XTerm will pop up displaying the
main Perl man page. If you press `"q"` not only the
man page no longer is displayed but the XTerm will terminate, too.

This only is *one* example of how to use the CLI. You can use
it to issue any other command as well. A problem that might occur is
that the XTerm will terminate before you had time to read the output
of a command (it terminates as soon as the command is done).

In most such cases it is sufficient to pipe the output through
`less` (this is one of the rare cases you cannot
use `more` because it terminates after displaying
the last line). However, there are cases (mainly programs that write
colorful output such as `ls`) that may result in
trouble with `less`.

Fortunately Linux (any Unix version?) offers a solution to these
cases, too: The `sleep` command. It sleeps some
time, then terminates. So you could use

```
    ls $HOME/bin --color ; sleep 1m
```

to list all programs in your `$HOME/bin`
directory. The `sleep` command will wait the given
period of time (in this case a minute) before the XTerm automatically
will close (you can use `"Ctrl-C"` to abort the
`sleep` command before that time went by).


### May I use Win(95) keys with IceWM?


Sure you can. Josef Oswald reported:

this is in `.xinitrc`
```
clear mod4
keycode 64 = Alt_L
keycode 113 = Alt_R
keycode 115 = Meta_L
keycode 116 = Meta_R
add Mod4 = Meta_L Meta_R
```

in `.Xmodmap` there is:
```
add Mod1 = Alt_L
add Mod2 = Mode_switch
keycode 117 = Menu
```

and then in

`~/.icewm/preferences`

```
Win95Keys=1 # was 0

# KeySysWinMenu="Shift+Esc"
```

as can be seen I did _not_ enable the above, as I don't like pressing
two keys. If one wants to use it, it does work.

On a free workspace the right Win95 opens the list of Workspaces.

Now also in Open-office I can use the right menu key to open the menus in the
OOo taskbar with the letters for the shortcut I can switch to the desired
menu without needing to leave the keyboard,  my preferred way of working
on the pc.




### Customizing The Look Through Themes


IceWM can be customized using a great variety of themes. You can download them
usually as .tar.gz archives on the net.
To install themes simply unpack them into your `~/.icewm/themes/` directory.

### What image formats can I use with IceWM?


If IceWM is compiled with the standard xpm libraries, then it can
only employ xpm images (as backgrounds, etc.). If, however, IceWM is
compiled with `imlib` support, it can display all
common image formats including jpeg, gif, png, and tiff.

### Setting background color/image


If you provide the appropriate options in your
`preferences` file and start `icewmbg`, IceWM will set the
background color or the background image for you. You can use

```
    DesktopBackgroundColor="color"
```

to set a background color and

```
    DesktopBackgroundImage="image"
```

to set a background image. To keep IceWM from setting a background
color/image you simply set *both* options to an empty string:

```
    DesktopBackgroundColor=""
    DesktopBackgroundImage=""
```

**Hints:**

1.
    Commenting out
    `DesktopBackgroundColor="color"`
    and `DesktopBackgroundImage="image"`
    does not have the intended effect.
2.
    IMHO using a background image (especially a huge one) isn't that
    good an idea. It awfully slows down the X windowing system.


To distinguish between filling whole desktop with image or to place it self
standing in the middle you can use

```
    DesktopBackgroundCenter=""
```

DesktopBackgroundCenter is used to tell IceWM how you want your wallpaper placed on the screen.
If set to 1 your picture will be centered on screen. As a result of that, you will only have one picture in the middle of your desktop.
If set to 0 your picture file will fill the whole screen. That is a good thing if you are using a pattern thingy to cover the whole desktop.


### Setting the clock format


Setting up the look of the task bar clock of IceWM as well as the
format of the associated tooltip is rather easy. IceWM uses the same
format as the Unix standard function `strftime` so
when in doubt you can always refer to

```
    man 3 strftime
```

To set the clock format you use

```
    TimeFormat="<format string>"
```

and for the clock tooltip format you use

```
    DateFormat="<format string>"
```


Ordinary characters placed in the format string are printed without
conversion (if possible, see below). Conversion specifiers are
introduced by a percent character `"%",` and are
replaced by a corresponding string.

**Important Note:** While `"DateFormat"` and
`"TimeFormat"` both support all the format
descriptors the latter only has full support if used with

```
    TaskBarClockLeds=0
```

(which is set equal 1 by default).

The reason for this is that there are no icons to display the name of
a month, day, or time zone. To be more precise there are only icons
for

1. digits (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
2. colon, dot, slash, and space
3. A, P, and M (for AM and PM)


Format descriptors which may only be in
`"TimeFormat"` if
`"TaskBarClockLeds=0"` (in general or depending on
the locale) are labeled as **restricted** in the following
table. It shows the replacement for all format descriptors available.

The values in parentheses show what the different format specifiers
display for

`YYYY/MM/DD HH:MM:SS TimeZone = 1999/09/04 19:09:22 UTC`

on my machine with hardware clock and Linux running UTC, local being
"C" (i.e.  no internationalization at all):


- `"%a"` (Sat) restricted
    The abbreviated weekday name according to the current locale.
- `"%A"` (Saturday) restricted
    The full weekday name according to the current locale.
- `"%b"` (Sep) restricted
    The abbreviated month name according to the current locale.
- `"%B"` (September) restricted
    The full month name according to the current locale.
- `"%c"` (Sat Sep 04 19:09:22 1999) restricted
    The preferred date and time representation for the current
    locale.
- `"%d"` (04)
    The day of the month as a decimal number (range 01 to 31).
- `"%H"` (19)
    The hour as a decimal number using a 24-hour clock (range 00 to
    23).
- `"%I"` (07)
    The hour as a decimal number using a 12-hour clock (range 01 to
    12).
- `"%j"` (247)
    The day of the year as a decimal number (range 001 to 366).
- `"%m"` (09)
    The month as a decimal number (range 01 to 12).
- `"%M"` (09)
    The minute as a decimal number.
- `"%p"` (PM) restricted
    Either "am" or "pm" according to the given
    time value, or the corresponding strings for the current locale.
- `"%S"` (22)
    The second as a decimal number.
- `"%U"` (35)
    The week number of the current year as a decimal number, starting
    with the first Sunday as the first day of the first week.
- `"%W"` (35)
    The week number of the current year as a decimal number, starting
    with the first Monday as the first day of the first week.
- `"%w"` (06)
    The day of the week as a decimal, Sunday being 0.
- `"%x"` (09/04/99) restricted
    The preferred date representation for the current locale without
    the time.
- `"%X"` (19:09:22) restricted
    The preferred time representation for the current locale without
    the date.
- `"%y"` (99)
    The year as a decimal number without a century (range 00 to 99).
- `"%Y"` (1999)
    The year as a decimal number including the century.
- `"%Z"` (UTC) restricted
    The time zone or its name or its abbreviation.
- `"%%"` restricted
    A literal "%" character.


### I have more icons to add


You can either copy them to systemwide `icons` directory or you can copy
them to `~/.icewm/icons` or you can use option

```
IconPath="/home/username/.icewm/myicons:/usr/share/pixmaps"
```
from preferences file. Remember that the new path you are adding must be seperated with a colon (:).


### How to learn making themes for IceWM?


There is documentation on [themes](/themes/)
written by MJ Ray and update by Adam Pribyl.


### Miscellaneous Questions


This section is a collection of questions on subjects that go beyond
simply **using** IceWM.

### What does Logout(Cancel) Command do?


For most users, nothing. Both commands were meant for GNOME
integration as alternative commands that would be run when users
initiated a logout or logout cancel. Since GNOME did not seem to
incorporate this feature, they generally go unused.

### What is the blank field in the task bar good for?


If you are running IceWM with the
`"TaskBarDoubleHeight"` option set, a blank field in
the task bar occurs. It is a command line interface.

In this field you can enter commands to start programs. If you click
inside the field and enter `xclock` the X clock is
started.

If you click on it and simply press `"Ctrl-Enter"`
an XTerm is being started.

If you enter a non-X command and press
`"Ctrl-Enter"` an that command is being executed in
an XTerm.

### How to keep IceWM from grabbing keystrokes


What if you are running an application and need to use a keystroke
that is grabbed by IceWM?

Marko suggests the following workaround:


1. Activate scroll lock
2. Do problematic key stroke
3. Deactivate scroll lock


He advises that this will only work if
`"ScrollLock"` is set up as a modifier.

Here is how to use the X11 `xmodmap` utility to setup `ScrollLock` as
a modifier (from Marco Molteni):
-  check which modifiers are free:

```
    $ xmodmap -pm

    xmodmap:  up to 2 keys per modifier, (keycodes in parentheses):

    shift       Shift_L (0x32),  Shift_R (0x3e)
    lock        Caps_Lock (0x42)
    control     Control_L (0x25),  Control_R (0x6d)
    mod1        Alt_L (0x40),  Alt_R (0x71)
    mod2        Num_Lock (0x4d)
    mod3
    mod4        Super_L (0x73),  Super_R (0x74)
    mod5
```

-  in this example `mod3` is free, so we bind the `ScrollLock` key to it:
     $ xmodmap -e "add mod3 = Scroll_Lock"
   this invocation of `xmodmap` should be put in the script that starts the
   window manager, for example `$HOME/.xinit` or `$HOME/.xsession`, see

### How to lock the screen


Screen locking is something you should do whenever you leave your
machine (even at home and even for only a few seconds - just imagine
a cat pushing the enter button at the wrong moment). It should be a
habit like logging out root as soon as possible.

### ... by keyboard


With IceWM screen locking is very easy: If you press

```
    Ctrl-Alt-Del
```

a menu pops up offering you the following tasks:


- Lock `"W"`orkstation
- `"L"`ogout
- `"C"`ancel
- `"R"`estart icewm
- Re`"b"`oot
- Shut`"d"`own


The letters that are emphasized in this FAQ are underlined in real
life. The meaning of this emphasis is that you may e. g. press
`"W"` to lock your workstation.

Another possibility (this is the one I prefer because I once to often
pressed `"L"` in order to lock my machine) is to
press `"ENTER".` The result is the same because the
button that is active by default is *"Lock
Workstation".*

A more obvious reason for using `"ENTER"` in place
of `"W"` is that it is easier to type in:
`"Del"` and `"ENTER"` are next to
each other.

You could as well use your mouse to click on *"Lock
Workstation"* but if you are already using your keyboard to
evoke the menu why not use the keyboard to select from it?

### ... by mouse


If you prefer to use your mouse to lock the screen you may add the
following entry to your `$HOME/.icewm/toolbar`

```
    prog    xlock   xlock   xlock
```

You could as well add that line
`$HOME/.icewm/menu` or
`$HOME/.icewm/programs` but that's not a good
idea: Screen locking is often done in a hurry and if you have to scan
through a menu this will increase the chance that you will not lock
your machine at all.

### ... using a lock command other than xlock


How to define a different lock command is described in section "Setting the lock command"

### Does IceWM support session management?


From 1.2.13 IceWM has some basic session management to manage all its parts.
But this is where the more complicated desktop environments like
GNOME, KDE or xfce join the game. IceWM still is mainly a window manager...
but of course you can always start your favorite apps upon X start-up/login
using the `.xinitrc` or `.xsession`files. Or use IceWM as the
window manager instead of the default GNOME/KDE wm.

### Can I have icons on the desktop?


Sure, but not from IceWM. Again, this is desktop environment work, but
usually done by the respective file managers, since they already know about
MIME types, file endings and such. IceWM users usually use idesk, dfm, rox, kfm or gmc,
where idesk, dfm and rox are better suited for work on smaller (older) machines than the
other two.

### Why doesn't IceWM accept my background image/color?

Usually this is because it's the wrong image format. It can happen when
IceWM is compiled only with libXpm.
With imlib, IceWM is able to read most of the often used image
formats like png, gif, jpeg, instead of just xpm images with libXpm. Another
reason can be, that the theme defines another image or color.

### Can I have bigger icons in menu, taskbar, quickswitch etc.?

From IceWM 1.2.14 it is possible to specify size of icons in IceWM preferences.
There are four relevant options:
```
MenuIconSize=16
SmallIconSize=16
LargeIconSize=32
HugeIconSize=48
```
These values are default but you can change them to whatever you want.
`MenuIconSize` specifies size of icons in menu. Three other are used for
any other icon in IceWM. E.g. `SmallIconSize` is used in taskbar,
application frames and window list. `LargeIconSize` is used in quickswitch.

You have to take in mind that when you change size of `SmallIconsSize`
then all above described parts will have icons of different size, but taskbar
and frames will not change their high accordingly! Also when you specify the size
that is not available, then icons will be resize - this can cause some disturbance
mainly when you are using xpm icons.

There is a trick to increase size of taskbar however. Taskbar height is sized according
size of start button. E.g. for linux if your `linux.xpm` in taskbar
folder is 50x32 then your taskbar will be 32 pixels high.

To change the height of frames you have to make theme with higher frames.


### How can I translate IceWM into my language?


Create a copy of `icewm.pot` and rename it to
`cs.po` or whatever is right for your language.

Then you have to translate the file using any of the tools for
gettext file transaltion, e.g. kbabel, or you can edit it by hand.
After translation you can send it to icewm-devel list or post it
as patch in patch tracker.


If you want to test file yourself you can add this file
into `po` directory under IceWM sources and then configure IceWM
(`./configure`) and type `make` in `po` directory.
This creates .mo file, which you can either copy to locale locations
(e.g. /usr/local/share/locale/cs/LC_MESSAGES) or you can do `make install`.

### How to use Xrandr with IceWM?


IceWM supports since a few versions the xrandr feature of X11. This can
very easily be used to define a menu item on your toolbar to change the
display resolution, provided that you run recent enough versions of both
X11 and IceWM that supports xrandr. You can run `xrandr -q` to see the
resolutions supported using your present X configuration (maximum
resolution and color depth). You can edit this menu fragment when you
have checked which resolutions work and then you can put it into your
`./icewm/toolbar` file

```
# IceWM toolbar menu to change the display resolution.
# This needs xrandr support from both X11 and Icewm.
#
# Xrandr is considered an experimental feature, so your screen may go
# blank if you have a problem with some resolution setting.
# It is a good idea to close your other windows before testing.
#
# Check your own resolutions with xrandr -q and modify accordingly.
# This example assumes a default resolution of 1280x1024.
#


menu Resolution redhat-system-settings {
   prog 1280x1024 1280x1024 xrandr -s 0
   prog 1152x864  1152x864  xrandr -s 2
   prog 1024x768  1024x768  xrandr -s 3
   prog  800x600   800x600  xrandr -s 4
   prog  640x480   640x480  xrandr -s 5
}
```

The redhat-system-settings is a bitmap I picked up from my Fedora Core 3
box, you can put there whatever you want of course.



### Example: configuration A-Z


This is sample of possible configuration you need to do to have IceWM
running with all you need. Following applies for RedHat(9). Placement of files can be
bit different.

### X window login

To have possibility to switch to IceWM  in GDM greeter (after start to runlevel 5 = Xwindow),
then you need to do following things:


- Add to `/etc/X11/gdm/Sessions/` (gdm is default greeter) file `IceWM` with content
```
  #!/bin/bash
  exec /etc/X11/xdm/Xsession icewm
```

- Modify `/etc/X11/xdm/Xsession` to understand what "icewm" is (this is not necessary)
- Add to `/usr/share/apps/switchdesk/` file `Xclients.icewm` with content
```
  #!/bin/bash
  exec /usr/local/bin/icewm-session
```



### IceWM configuration

To configure all of IceWM options go to sections about configuration.
Generally all you need to customize IceWM globaly, is to edit `/usr/local/share/icewm/preferences` etc.

### Additional applications

### Icons on desktop

Usually people want to have icons on desktop. One of most simple applications that can
satisfy this need is `idesk` (see Tools to find it). I personaly recommend
to use 0.3.x version - this has almost no requirements and is really simple.

Configuration of idesk is almost as easy as configuration of IceWM, but has one disadvantage:
idesk does not have in version 0.3.x global configuration file - therefore each user needs to
have proper configuration file in his/her home.

To configure idesk you need to:

- Add `~/.ideskrc` file with content like this
```
table Config
  FontName: Helvetica
  FontSize: 9
  FontColor: #ffffff
  PaddingX: 35
  PaddingY: 25
  Locked: true
  HighContrast: false
  Transparency: 50
  Shadow: true
  ShadowColor: #000000
  ShadowX: 1
  ShadowY: 1
  Bold: false
end
```

- Add `~/.idesktop` directory
- Add `whatever.lnk` files into it, with content like this

```
table Icon
  Caption: Mozilla
  Command: mozilla
  Icon: /usr/share/pixmaps/mozilla-icon.png
  X: 22
  Y: 13
end
```

- Do not forget you need to start idesk at the beginning of the session.
  Best to achieve this is using your `~/.icewm/startup` file (for details see Configuration section).
  In case of idesk you can add line:
```
idesk > /dev/null & # start idesk - desktop icon manager
```






### Control tools

To have some "control center" like application you can use Vadim A. Khohlov's `icecc` -
IceWM Control center. (see Tools to find it) His utility is also very simple, fast and has editors
for all of the IceWM options.

To integrate it into menu you have to edit `/usr/local/share/icewm/menu` and add there line like this
```
prog "Control Center" "icecc_icon" icecc
```

Please note that icecc needs some other programs like gvim and python to work properly.

### Tools for IceWM


This section is a collection of tools that simplify the usage of
IceWM. Head on over to the utilities section of the IceWM homepage if you
want an up to date overview about all available tools.

### IcePref


**Note:** IcePref is a history these day, but you can still find it.

### Description (by the author of IcePref)


IcePref is a small graphical utility (written with Python and the Gtk
toolkit) designed to simplify the configuration of IceWM.

It currently supports the options of IceWM version 1.0.4 and should
(in theory) work consistently with versions at least as high as
1.0.4. While it is not a particularly elegant program, I have found
IcePref useful and hope that it will be found useful by those who use
IceWM and also have Gtk installed.

IcePref should be especially useful to those who have GNOME, and who
are therefore likely to have PyGNOME and PyGTK already installed on
their boxes.


### IcePref2


IcePref2 is maintained successor to IcePref.
It is included in *IceWM Control Panel*.

### Description


IcePref2 is advanced preferences file editor.



### IceME


The IceWM Menu Editor allows users to edit their menu without knowing
anything about config files.
It is included in *IceWM Control Panel*.


### IceWM Control Panel

### Description (by author of IceWM Control Panel)


IceWM Control Panel is the first full-featured, Gtk-based control panel
for IceWM. It is meant to run in IceWM, but can be used in ANY window
manager as a general-purpose control panel. It was inspired by the Qt-based
application called IceMC, but includes many more tools, a more familiar
Windoze Control Panel-like interface, and uses the MUCH faster Gtk user
interface (Who runs a fast Window Manager like IceWM, to launch SLOW-running,
memory-intensive Qt/KDE-based applications?? I sure don't).
Let's face it: IceWM and fast Gtk interfaces work well together.

IceWM Control Panel includes applications for editing preferences (IcePref2),
menus (IceMe), themes, sounds (IceSoundMngr), cursors, keys, mouse, wallpapers,
winoptions, icon browser etc.


### IceWM Control Center

### Description


This is Vadim Khohlov's software. A good collection of the configuration
software for IceWM, include: menu/toolbar editor, Ice Sound Configurator,
theme Switcher, backgroundoptions editor, IceWM's winoptions editor, keys
editor.


### IceWMConf

### Description (by the author of IceWMConf)


IceWMConf is a small application which helps with configuring IceWM.
It tries to be self-configuring, starting with the basic options from
the system preferences files and then overriding them with user
preferences.

In this way, it should pick up new options introduced by later
versions of IceWM. (It does mean that old options aren't deleted, so
you have to occasionally "trim" your user file to remove
lines IceWM grumbles about, but that isn't very necessary.)

Its user interface is functional bordering on spartan, but builds its
own option categories and has an option name search facility. If you
want a really user friendly configuration tool, I suggest IcePref.



### IceWO

### Description


IceWO is an icewm's winoption file editor. It allows you to set winoptions
for any window by clicking on buttons, without manual editing winoptions file.


### IceMC

### Description


IceMC is a graphical menu editor for IceWM, designed to be simple and stable.
You can configure your menu entries with copy, paste, and drag'n'drop.


### MenuMaker

### Description


MenuMaker is utility written entirely in Python that scans through the system for
installed programs and generates menu for specified X window manager.
It is by far more superior to existing solutions in terms of knowledge base size,
maintainability and extensibility, and has a number of features that have no counterparts
in its class. MenuMaker is intended for users of lightweight *NIX graphical desktop environments.

### IDesk

### Description


iDesk gives users of minimal wm's (fluxbox, pekwm, windowmaker...) icons on
their desktop. The icon graphics are either from a png or svg (vector) file
and support some eyecandy effects like transparency. Each icon can be confgured
to run one or more shell commands and the actions which run those commands are
completely configurable. In a nutshell if you want icons on your desktop and
you don't have or dont't want KDE or gnome doing it, you can use idesk.


### DFM

### Description


DFM is a file manager for Linux and other UNIX like Operating Systems.
DFM is the abrvabation for Desktop File Manager. "Desktop" stands for the
capability to place icons on the root window.


### Bugs and Problems


This section is for problems that are intrinsic to the philosophy of
IceWM or that are caused by bugs.

### IceWM ignores my color settings


Some users wonder why the colors specified in their preference files
seem to have no effect upon the actual appearance of things. The
reason is that these settings may be overridden by settings in the
theme file.

The theme file can control all of the options
controlled by the `preferences` file, but usually
theme authors are decent confine their meddling to superficial
aspects of window manager behavior and leave control over most
important behaviors to the user.

If this wasn't the reason: If you are running X in 8-bit mode then it
is possible that the specified color simply isn't available.

You don't know if X is running in 8-bit mode? Run

```
    xwininfo | grep Depth
```

in an XTerm and click on the root window (the desktop). If this
command displays

```
    Depth: n
```

you are running X in n-bit mode (n typically is 8, 16, 24 or 32).

### Programs are missing in the menus


A very annoying problem are programs you added to the
`menu` file but
that are missing in the corresponding menus. That isn't really a bug
of IceWM. The point of view of IceWM is that it makes no sense to
display a program that *are not present.*

The crucial point is the meaning of *"to be
present".* It does not mean *"to be
installed"* but *"to be found using the present
path"* (*echo $PATH* or *which program* to find if program is in
PATH).

To fix the problem you have at least three possibilities:


1.  You give the full path and not only the program name itself.
2.  You set the path in your `.xinitrc`, `.xsession` or `.Xclients`.
3.  You use a wrapper script for running IceWM.


The first two solutions are straightforward. Using a wrapper script
is a bit tricky therefore I'll describe how to do it.

Become root and move `icewm` to
`icewm.bin.`

```
    mv /usr/local/bin/icewm /usr/local/bin/icewm.bin
```

Edit `icewm` so that it reads something like this:

```
    #!/bin/sh

    PATH=<what the path shall be>
    export $PATH

    exec icewm.bin $*
```

It is very important to add the `"$*".` Otherwise
all command line arguments (such as *"use another
theme")* will be ignored.

**Hint:** Using `bash`, `ksh` and
`zsh` you can contract

```
    PATH=<what the path shall be>
    export $PATH
```

into

```
    export PATH=<what the path shall be>
```

You could also **add** directories to the path (instead of
simply overwriting it). To do this you use

```
    PATH=$PATH:<what shall be added>
```

### IceWM maximizes windows over the GNOME panel


This used to be a really annoying problem, but seems to be gone with newer
versions of IceWM and GNOME. If it still happens on your machine try to set

```
    Panel.doNotCover: 1
```

in your `winoptions` file.

### The IceWM binaries are very big


You might wonder why the IceWM binaries is that big. This is because
they contain an awful lot of (debugging) symbols. Without them the
binaries are **much** smaller. The command to remove the symbols
is `strip:` Go to the directory where IceWM has
been installed in (typically `/usr/local/bin/)`
and issue:

```
    ls -l icewm icewmhint icewmbg icewmtray genpref
    strip -s icewm icewmhint icewmbg icewmtray genpref
    ls -l icewm icewmhint icewmbg icewmtray genpref
```

The `ls` commands are not really needed, but show
you the (maybe dramatic) change of size of the icewm binaries.

Use `man strip` and `info
strip` to find out more details about the
`strip` command.

### Screen locking doesn't work


The reason for this is that the standard lock command
(`xlock`) could not be found by IceWM.
See "Setting the lock command" for details on setting
a different lock command.

### Background does not show up


IceWM is divided in few separated parts. One of them is `icewmbg`.
This part takes care of bacground setup. Therefore if you want IceWM to
take care of desktop background you have to start `icewmbg` at
IceWM startup. The proper way is to start "icewm-session" in your
X startup instead of just icewm.
See "Configuration".

### Icon tray does not work


Problem is nearly same as with background. There is `icewmtray`
you need to start to activate tray functions. This should implement some docking
standard used by other applications.

### IceWM does not respect my font settings


IceWM uses two ways of font handling - corefonts OR fonts provided by xfreetype library.


These fonts can be specified in `preferences` or theme `default.theme`.

For X server provided fonts (configure --enable-corefonts option) the definition looks like this:

```
    ActiveButtonFontName = "-artwiz-snap-regular-r-normal-sans-10-*-*-*-*-*-*-*"
```

For Xft (xfreetype) library (used by default, disable using option --disable-xfreetype),
then specification is like this:

```
    ActiveButtonFontNameXft = "Snap:size=10,sans-serif:size=12:bold"
```


To provide correct fonts to Xft you have to specify them in `/etc/fonts/fonts.conf`.
X server font are either provided by X server itself e.g. `/etc/X11/XF86Config` - Section "Files",
or by XFS (X Font Server) defined in. `/etc/X11/fs/config`.


### Sources of information


This section lists sources of information on the IceWM window
manager. X applications to use with IceWM have their own section (see
*Tools for IceWM*).

Additions to the lists are welcome!

**Important Note:** This section is presently being worked on.
It's not finished and may be rather incomplete. FIXME

### web pages


### License


This document is released under the terms of the GNU Library General Public License.

### Recent Changes to this document


This section keeps you informed what parts of this document changed
recently.


	pridat jak udelat backtrace, kompilace s debug apod.
- Adam Pribyl, menuprogreload, runonce, win95 key usage, MFAQ about WM_CLASS, removed some refs to icewm.moal.ch, xrandr (thnx Tomas Linden), taskbar can only be increased (fix), how to disable alt+mouse
- Marko Macek, updates to icewm-session / startup / icewmbg (2005-05-24)
- Adam Pribyl, alt+drag, winoption .workspace (thnx Oliver Kosmann and Christophe Badoit), font defs explain better, some udates regarding 1.2.14 (2004/06/15)
- Adam Pribyl, translation howto, Vadims idesk lnk maker add, minor correction. (2004/03/01)
- Adam Pribyl, font handling problem question and answer. (2004/02/10)
- Adam Pribyl, startup script section improvements, corrected path in example section (thx to Michael Dipperstein), MFAQ add showdestop
- Adam Pribyl, added icewm-session to most FAQ; Fulltext advice made more visible;
    Section Example configuration A-Z added - this is preliminary version - comments welcomed. (2003/10/14)
- Adam Pribyl, added idesk and dfm links to tools section. icewm-session
    and prefoverride added. Some small improvements. (2003/09/14)
- Adam Pribyl, updated Howto prevent IceWM from grabbing keystrokes, with text sent by Marco Molteni.
    Some more hyperlinking. (2003/09/11)
- Adam Pribyl, updates to reflect latest icewm development (icewmtray, icewmbg,
    .icewm/theme). License note add. MenuMaker add. Minor hyperlink and some answers updates. (2003/08/25)
- Adam Pribyl makes some answers more accurate, added IceMC, bigger icons answer.
    (2003/05/10)
- Adam Pribyl updated FAQs to fit nowadays needs, put them on
    the website and added few new things. (2003/03/29)
- New maintainer. Markus Ackermann took over and reorganized much of the
    FAQ. I've even renamed it to "IceWM FAQ and Howto", since that's what it's already
    been. Moved homepage of the English version.
    (2001/07/25).
- Revision of FAQ because some formats (Postscript for example)
    weren't OK (2000/01/08).
- Added sections *"Switching Desktop using keyboard"* and
    *"Moving windows between desktops using keyboard"*
    (2000/01/08).
- IceWM homepage has moved, update URL (1999/12/26).
- This section has been added (1999/10/10).
- The themes.org site  is up now. This information has been
    added to "IceWM related web pages"
    section (1999/10/10).
- Contact mail address has been changed.  (1999/10/10).



