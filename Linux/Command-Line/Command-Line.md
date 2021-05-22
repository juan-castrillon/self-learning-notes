---
title: Command Line Operations
parent: Linux
has_children: true
nav_order: 5
---

Operating from the command line brings many benefits:
- No GUI overhead is incurred
- Scripts can be implemented for tasks
- Access to some tools is easier (no menus)
- Mostly equal in all linux distros

This can be done via a **terminal emulator** program. This program emulates (simulates) a standalone terminal within a window on the desktop. 

It behaves essentially as if you were logging into the machine at a pure text terminal with no running graphical interface.


# Command Basics

Most commands have three parts:

- Command: Name of the program being executed
- Options (Flags): That modify the behavior
- Arguments: Values that the program operates on

For example:
```
grep -P "something"
```

# Basic Utils

- `cat`: used to type out a file (or combine files)
- `head`: used to show the first few lines of a file
- `tail`: used to show the last few lines of a file
- `man`: used to view documentation.

# sudo

- Is a program that allows users to have admin rights and perform certain operations
- In some systems it may be needed to configure it before using


# Virtual Terminal

Virtual Terminals (VT) are console sessions that use the entire display and keyboard outside of a graphical environment. 

They run at the same time as the GUI and can help in cases where the GUI is frozen for example

One virtual terminal (usually number one or seven) is reserved for the graphical environment, and text logins are enabled on the unused VTs. 

To navigate through this terminals the combination
`CTLR` + `ALT` + `FN` + `F1-7` 

is used

> To turn off the GUI, the service is called `gdm`. So `sudo systemctl stop gdm` and `sudo systemctl start gdm` are used from a terminal (emulated and virtual)



