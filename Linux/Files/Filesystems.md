---
title:  Filesystems
parent: Files
grand_parent: Linux
---
# Filesystems

Linux considers everything in the system (including devices, disks, etc.) as files, this simplifies I/O operations.

A filesystem is the embodiment of a method of storing and organizing data in a human-usable form. In other words, is how to find and store data (files) in a hard disk(partition)

In linux the file system is hierarchical and starts in the root directory `/` (Not to be confused with `/root` (Directory of the super/root user)).

Filesystems can be of different types
    - Linux specific like ext3, ext4
    - Others like ntfs, vfat, etc.

It is often the case that more than one filesystem type is used on a machine, based on considerations such as the size of files, how often they are modified, what kind of hardware they sit on and what kind of access speed is needed, etc. 

In linux each filesystem occupies a disk partition. These are "logical drives" inside a single (or more) real drives, but appear as different drives to the OS. Data is stored into different partitions for many reasons, including security or backup. 

 > A **partition** is s a section of the hard drive that is separated from other segments. Partitions enable users to divide a physical disk into logical sections. Although they are normally not, they are treated like separate physical devices.

> `gparted` can be used to check out the partitions in a system

# Mount

Filesystems are mounted on the filesystem tree. The mount points are just directories in which the new filesystem will live.

To mount a filesystem, `mount` is used. 

The filesystem can be local in the computer or in a network
For example
```sh
sudo mount /dev/sda5 /home #Mounts the filesystem in the sda5 device(partition) in /home
sudo umount /home #Unmounts the filesystem 
```
Editing `/etc/fstab` results in adding a filesystem to be available from the beginning. This file defines pre-configured filesystems. `man fstab` shows how to use it

> Executing `mount` without any arguments will show all presently mounted filesystems.Same with `df -Th` (disk-free) which will display information about mounted filesystems, including the filesystem type, and usage statistics about currently used and available space.

## NFS

Filesystems can also be network filesystems. This means they have all of the data in one computer in a network or distributed in different filesystems in more than one node. 

A network filesystem can be mounted on computers to allow for example different users to always access their data (remote `/home` mounted on a server), even accessing from a different PC.


NFS has a server and client side

- On the server, nfs runs a a daemon, and allows to share a directory in the server's filesystem via NFS (with a network address)
```sh
sudo systemctl start nfs # Starts the NFS daemon
```
On the `/etc/exports` file, the directories that are going to be shared are typed in. For example `/projects *.example.com(rw)` means that the `/projects`directory in the server will be shared (with read and write accesses), and clients under the `example.com` domain can access it.

> Using `exportfs -av` notifies Linux of the changes. The NFS daemon can also be reset, and set to start on boot.

- On the client, the filesystem is mounted like any other (Is also possible to modify `fstab` to boot with the filesystem mounted)
```sh
sudo mount servername:/projects /mnt/nfs/projects
```