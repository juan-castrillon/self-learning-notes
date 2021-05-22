---
title: GUI
parent: Linux
has_children: true
nav_order: 4
---
# GUI

## X Windows System

- Loaded as one of the final steps in the boot process.
- Often just called X.
- A service called the Display Manager keeps track of the displays being provided and loads the X server (so-called, because it provides graphical services to applications, sometimes called X clients). The display manager also handles graphical logins and starts the appropriate desktop environment after a user logs in.
- Old, being replaced by simpler version like Wayland

### Desktop Environment

- A session manager (starts and maintains the components of the graphical session)
- Window manager (controls the placement and movement of windows, window title-bars, and controls).
- Set of utilities
- GNOME is a popular desktop environment (Alternatives include for example KDE)

### GNOME

- Desktop Environment (default in Red Hat Enterprise Linux (RHEL), Fedora, CentOS, SUSE Linux Enterprise, Ubuntu and Debian)
- The default display manager for GNOME is called `gdm`
- Can be customized using Settings and tools like `gnome-tweaks`

## Nautilus (File Manager)

 - Is used to navigate the file system
 - Lets you access different locations on your computer and the network
 - Can be opened from terminal (`nautilus`)
 - When a file is double-clicked is opened with a text editor (The default text editor in GNOME is `gedit`) (This can be changed in the configuration)
 - Deleting files sends them to `.local/share/Trash/files/`
 - A file can also be permanently deleted (`shift` + `delete`) and the trash can be emptied.
