---
title: Applications
parent: Command Line Operations
grand_parent: Linux
has_children: true
---

From the command line, application (packages) can be found, installed, upgraded and removed, among many other operations.

# Locating Applications
- In general, executable programs and scripts should live in `/bin`, `/usr/bin`, `/sbin`, `/usr/sbin`, or somewhere under `/opt`
- Tools like `which` and `whereis` can be used to obtain the location.

# Installing and Removing Software

The core parts of a Linux distribution and most of its add-on software are installed via the Package Management System. 

Each package contains the files and other instructions needed to make one software component work well and cooperate with the other components that comprise the entire system

All linux distros have a low level and a high level package manager:
- The low level, is in charge of installing single packages correctly. 
- The high level usually calls the low level one and additionally, is in charge of searching for dependencies

![image](https://user-images.githubusercontent.com/64461123/119973603-fa0ae000-bfb3-11eb-998f-0d9fe57e614f.png)

## In Ubuntu (all Debian-based OS)

### Low Level: `dpkg`

```bash
dpkg --list # List all packages 
dpkg --listfiles package # Lists files inside the package
sudo dpkg --remove package # Removes packages (checks for dependencies)
```

### High Level : `apt-get` and `apt-cache`

In addition, ubuntu provides `apt`. This provides a high-level commandline interface for the package management system. It is intended as an end user interface and
enables to easily use the most common options of `apt-get` and `apt-cache`. For more details see [here](https://itsfoss.com/apt-vs-apt-get-difference/)

```bash
sudo apt-cache search package # Search for packages in the configured repositories
sudo apt-get install package # Installs the package (and dependencies)
sudo apt-get remove package # Removes the package (and dependencies)
```