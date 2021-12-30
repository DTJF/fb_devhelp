Welcome to project fb_devhelp, a FreeBASIC documentation book for the
[DevHelp](https://wiki.gnome.org/Apps/Devhelp) documentation browser.

On LINUX systems the package manager makes it easy to install a
library. In order to compile against that library, the `*-dev` package
of the library is necessary. Most packages recommend to additionaly
install the `*-doc` package, containing the documentation of the
library API in form of an indexed HTML tree. That tree is called a
`book`. Several books can get browsed and searched by the DevHelp
tool (off-line).

The folder `freebasic` in this repo contains the FreeBASIC
documentation in form of such a DevHelp book. The original [manual
pages](https://www.freebasic.net/wiki/FBWiki) are adapted for DevHelp
by

- adding the index file
- adapting the file `style.css`
- renaming `DocToc.html` to `00index.html`
- making all page logos (top right corner) link back to the index page

This project is the successor for [FB manual for Devhelp
(LINUX)](https://www.freebasic.net/forum/viewtopic.php?f=9&t=19607&sid=b1a2ff36f513a60fa80d1b9bbb843e54)
(DE: [FB-Befehlsreferenz für
Devhelp](https://www.freebasic-portal.de/downloads/referenzen/fb-befehlsreferenz-fuer-devhelp-en-0-23-0-227.html)
). It's up-dated and now [hosted on
GitHub](https://github.com/DTJF/fb_devhelp).


Licence:
========

Copyright &copy; 2012-2022 by `Thomas{ doT ]Freiherr[ At ]gmx[ DoT }net`

This project is free software; you can redistribute it and/or modify it
under the terms of the Lesser GNU General Public License version 2 as
published by the Free Software Foundation.

This program is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU Lesser
General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-
1301, USA. For further details please refer to:
http://www.gnu.org/licenses/lgpl-2.0.html


Usage
=====

First, pull the repository and jump in

    git clone https://github.com/DTJF/fb_devhelp
    cd fb_devhelp

In order to install the FreeBASIC manual book, just copy (or move) the
complete `freebasic` folder to a DevHelp inputs folder. That location
depends on your LINUX distribution, see the DevHelp documentation for
details.

On Debian-like systems (Ubuntu, Mint, Knoppix, ...) this is

    sudo cp -r freebasic /usr/share/gtk-doc/html/

to make the book available system-wide (after restarting DevHelp).

Alternatively the book can get installed for a single user usage

    cp -r freebasic ~/.devhelp/books


Up-Date
=======

In order to up-date your manual book, execute in the repository

    git pull

Then delete the old files and install the new ones

    sudo rm -r /usr/share/gtk-doc/html/freebasic/*
    sudo cp -r freebasic/* /usr/share/gtk-doc/html/freebasic/


Geany integration
=================

For context-sensitive help in Geany IDE set a context-action in menu
`Preferences -> Tools: Context action:`

    devhelp -s '%s'

When pressing the context-action key (defaults to F12) Geany makes
Devhelp showing the matching help page for the keyword under the text
cursor (or the marked text block, if any). If Devhelp isn't running
yet, a new instance will previously be started, otherwise the running
instance switches to that page.

DevHelp searches case sensitive if any upper case character is included
in the search string (marked text). If you want to search
case-insensitive you can convert the search string to lower case
characters. Therefor I use this script (ie in folder `~/bin`)

    #! /bin/bash
    # Starting devhelp lower case

    devhelp -s $(echo $@ | sed 's/[[:upper:]]/\L&/g')

named `calldevhelp` and made executable by

    chmod +x calldevhelp

The script gets installed in Geany by context command

    calldevhelp '%s'


Have fun!
