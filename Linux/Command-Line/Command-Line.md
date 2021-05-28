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
## `sudo`

- Is a program that allows users to have admin rights and perform certain operations
- In some systems it may be needed to configure it before using

## Shutdown or reset

- Command `shutdown` is preferred (Clean shutdown)
- Accepts also time parameter to execute after a given time
- The `halt` and `poweroff` commands issue `shutdown -h` to halt the system
- `reboot` issues `shutdown -r`

## Pipes

- Linux aims to have many simple commands instead of one very complicated
- For this, pipelines can be used: They allow for the output of a command to be redirected as the input for the next command in the pipeline
- ALlows for efficiency (no intermediate files required) and concurrency (commands in the pipeline don't have to wait for the previous ones to finish)
- Is done like `command1 | command2 | command3`




# Virtual Terminal

Virtual Terminals (VT) are console sessions that use the entire display and keyboard outside of a graphical environment. 

They run at the same time as the GUI and can help in cases where the GUI is frozen for example

One virtual terminal (usually number one or seven) is reserved for the graphical environment, and text logins are enabled on the unused VTs. 

To navigate through this terminals the combination
`CTLR` + `ALT` + `FN` + `F1-7` 

is used

> To turn off the GUI, the service is called `gdm`. So `sudo systemctl stop gdm` and `sudo systemctl start gdm` are used from a terminal (emulated and virtual).