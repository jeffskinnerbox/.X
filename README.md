X Dotfiles
==========
The xinit program is used to start the X server and clients on systems that don't have, or use, a display login manager like GDM/KDM/XDM. When xinit is run without specific client options it looks for a file called .xinitrc in the user's home directory and runs it as a shell script. This configuration file/script is used to start up client programs.

Background
----------
A [window manager][05] is just one more application for X11, like netscape or gimp or xterm.
Many people new to X11 come to believe that X11 runs the window manager and the
window manager runs programs. But that's not true. If configured right, you can
run all your applications under X11, kill the window manager, and start another window manager up.

Starting an X session is typically done in one of two ways:

1. The X session is started via a display manager (like [LightDM][01] in Ubuntu Unity),
and the user logs in at a GUI screen.
2. The user starts X manually after logging in to a text console. The latter is
typically done with the [startx][02] command, which is a simple shell script
wrapper for [xinit][03].  If no client program is specified on the command line,
xinit will look for a [.xinitrc][04] file in the user's home directory, to run as a
shell script. If found, this then would in turn run whatever user specified
commands to set up the environment, or launch programs that the file contained.
If .xinitrc isn't present, then global xinitrc file (/etc/X11/xinit/xinitrc) will be used.

The .xsessionrc and .xinitrc files are used to set up a suitable X environment,
and to launch other programs, a.k.a "clients", that we may want available as
soon as X is started. You likely have a system wide xsessionrc and xinitrc to
start a predefined set off programs. To customize this, create your own in your
home directory. Name it .i.xsessionrc or xinitrc, make sure it is an executable
script, and chmod +x.

CustomXSession - https://wiki.ubuntu.com/CustomXSession

To debug your issues you should have a look in ~/.xsession-errors 

xsessionrc is sourced by 40x11-common_xsessionrc during the start of the X session. It is intended for setting session-wide environment variables that should apply to all apps, such as locale information.

If .xinitrc isn't present, then global xinitrc file /etc/X11/xinit/xinitrc will be used.
To debug your issues you should have a look in ~/.xsession-errors 

To Do
-----
* [Running X](http://www.tldp.org/HOWTO/XWindow-User-HOWTO/runningx.html)
* [The X Window User HOWTO](http://www.tldp.org/HOWTO/XWindow-User-HOWTO/)
* [example of a more complex .xinitrc file you can learn from](http://git.sysphere.org/dotfiles/tree/xinitrc)

Referances for .Xresources
--------------------------
* [Xterm Manual Page](http://www.x.org/archive/X11R6.8.1/doc/xterm.1.html)
* [Using the .Xdefaults file](https://engineering.purdue.edu/ECN/Support/KB/Docs/UsingTheXdefaultsFil)
* [Using Configuration Files to Customize Your Windows Environment](http://h30097.www3.hp.com/docs/base_doc/DOCUMENTATION/V40F_HTML/AQ917BTE/DOCU_012.HTM)
* [Post your .Xdefaults and terminal apps color schemes with screenshot](http://crunchbang.org/forums/viewtopic.php?id=9935)
* [256-Color XTerms in Ubuntu](http://push.cx/2008/256-color-xterms-in-ubuntu)


[01]:https://wiki.ubuntu.com/LightDM
[02]:http://linux.die.net/man/1/startx
[03]:http://www.x.org/archive/X11R6.8.1/doc/xinit.1.html
[04]:http://www.slackbook.org/html/x-window-system-xinitrc.html
[05]:http://en.wikipedia.org/wiki/X_window_manager
