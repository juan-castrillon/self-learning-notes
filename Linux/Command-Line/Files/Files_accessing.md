---
title: Accessing Files and Directories
parent: Files
grand_parent: Command Line Operations
---
# Accessing Files and Directories

## Absolute and relative paths

Files and directories can be accessed using pathnames.

- Absolute pathname: An absolute pathname begins with the `root` directory and follows the tree, branch by branch, until it reaches the desired directory or file. Absolute paths always start with `/`.
- Relative pathname: A relative pathname starts from the present working directory. Relative paths never start with `/`.

## Showing filesystem
- `ls` can be used to show directories and files (many different options, `ls -a` shows hidden files as well)
- Another option is `tree`

## Access directories
- `pwd` shows current directory
- `cd` is change directory (`cd ~` goes to home, `cd ..` goes to parent directory, `cd -` goes to previous dir)
- Another option that saves history of the visited directories is using `pushd`, this pushes the directory into a LIFO stack, which can return elements using `popd`. 

## Hard (and soft) Links

- The `ln` utility is used to create hard links and (with the `-s` option) soft links, also known as symbolic links or symlinks( with the `-s` flag). These two kinds of links are very useful in UNIX-based operating systems.
- A link connects two files. In a hardlink, a "clone" is made in the sense that if the original is deleted, the copy still exists and has the content. Also modifying one, modifies the other. In soft links, is just a pointer.
- Adding the `-i` (and the `-l`) flag in `ls` allows to inspect the unique number for each file in the filesystem (inode number)
- Unlike hard links, soft links can point to objects even on different filesystems, partitions, and/or disks and other media,  which may or may not be currently available or even exist. 