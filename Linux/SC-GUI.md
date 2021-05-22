---
title: System Configuration
parent: GUI
grand_parent: Linux
nav_order: 1
---

# System Configuration Using the GUI

- The System Settings menu, allows to perform basic configuration
- `gnome-tweaks` allows for selecting a theme, configuring extensions, control fonts, and set which programs start when you login (among others).

## Displays

- Can be accessed in the settings menu
- Allows to configure display (resolution, orientation, etc.) 
- Configure multiple screens

## Date and Time

- Linux uses Universal Coordinated Time (UTC) for its own internal time keeping.
- It uses NTP (Network time protocol) to sync the time
- More detailed configuration is possible by editing the standard NTP configuration file `/etc/ntp.conf`

## Networks

- For this, the **Network Manager** is used.
- For *Wired Connections* : The Manager sets everything via DHCP. For static networks (no dynamic IP) setup can also be done. In the manager (if supported) even the MAC address can be changed
- For *Wireless Connections*: Are not connected by default, the manager allows to see the available ones
- VPN connections are also supported, including native IPSec, Cisco OpenConnect, Microsoft PPTP, OpenVPN

## Installing and Updating Software

- Software in Linux comes in form of packages.
- They can depend on one another
- All systems have a lower-level utility which handles the details of unpacking a package and putting the pieces in the right places. ANd a a higher-level utility which knows how to download packages from the Internet and can manage dependencies and groups.

### Debian Family

- `dpkg` (low level): 
  - Install, remove, and build packages
  - No downloading or dependencies

- `apt` (high level) :
  - Each debian distro has its own interface on top (apt, apt-get, aptitude, synaptic, Ubuntu Software Center, Update Manager, etc)

### RHEL Family

- `rpm` (low level): Used by  RH but also SUSE/penSUSE, Mageia, CentOS, Oracle Linux, a.o
- `yum`, `dnf` (high level)

### Open SUSE Family

Uses `rpm` through YAST(Yet Another Setup Tool) which is a graphical interface.
