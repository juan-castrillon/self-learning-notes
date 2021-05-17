---
title: FileSystems
parent: System Startup
grand_parent: Linux
nav_order: 1
---

# Filesystems

 A filesystem is the embodiment of a method of storing and organizing data in a human-usable form. In other words, is how to find and store data (files) in a hard disk(partition)

 > A **partition** is s a section of the hard drive that is separated from other segments. Partitions enable users to divide a physical disk into logical sections. Although they are normally not, they are treated like separate physical devices.

## Filesystem Hierarchy Standard

- Linux uses the ‘/’ character to separate paths (unlike Windows, which uses ‘\’), and does not have drive letters. 
- Multiple drives and/or partitions are mounted as directories filesystem. 
- Removable media such as USB drives and CDs and DVDs will show up as mounted at `/run/media/yourusername/disklabel` 
- Many distributions distinguish between core utilities needed for proper system operation and other programs, and place the latter in directories under `/usr`.

![fhs](https://courses.edx.org/assets/courseware/v1/66def40e2774fd96011565107706da2d/asset-v1:LinuxFoundationX+LFS101x+1T2020+type@asset+block/dirtree.jpg)
