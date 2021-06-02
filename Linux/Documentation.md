---
title: Documentation
parent: Linux
nav_order: 6
---

The man pages (short for manual pages)
GNU Info
The help command and --help option
Other documentation sources, e.g. Gentoo Handbook or Ubuntu Documentation.

# man pages

- The `man` program is in charge of searching and showing documentation.
- A given topic may have multiple pages associated with it and there is a default order determining which one is displayed when no options or section number is specified (in `/etc/man_db.conf`)
- The man pages are divided into chapters numbered 1 through 9

```sh
man command #Shows the manual entry for the command
man -f command #Lists all entries (can be more than one) for the command
whatis command #Same as above
man -k command #List all entries where the command is mentioned (can be from other commands)
apropos command #Same as above
man -a command #display all "command" pages in all chapters, one after the other
```

# GNU Info

- Similar to `man` but works with subsections and links
- Accessible through `info` tool.
 
To navigate:
Action | Key
---|---
Move | Arrows
Next Page | `Page Up`
Previous Page | `Page Down`
Select menu item | `Enter`
Quit | `q`
Help | `h`
Go to next | `n`
Go to previous | `p`
Move one node up in the index | `u`

# `--help` and `help`

- `--help` :Most commands provide a short way to get some reference passing the `--help` flag.
- `help` Is a program that can be used inside bash shells to get help about commands that run especially built-in bash versions. A list of these commands is shown using `help`

# Other sources

Include: 

- Desktop help system: All Linux desktop systems have a graphical help application. This contains desktop specific help as well as some rendered `man` and `info` pages. Can be runned from GUI or CLI (For example, for GNOME `gnome-help` or `yelp`)
- Package documentation: Linux documentation is also available as part of the package management system. Usually, this documentation is directly pulled from the upstream source code, but it can also contain information about how the distribution packaged and set up the software. Normally available in `/usr/share/doc`
- Online resources: Include forums, and doc pages. Also ebooks, like [this one](http://linuxcommand.org/tlcl.php)
