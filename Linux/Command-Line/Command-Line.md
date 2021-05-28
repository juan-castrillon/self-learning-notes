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


# Shutdown

- Command `shutdown` is preferred (Clean shutdown)
- Accepts also time parameter to execute after a given time
- The `halt` and `poweroff` commands issue `shutdown -h` to halt the system
- `reboot` issues `shutdown -r`


# Locating Apps
- In general, executable programs and scripts should live in /bin, /usr/bin, /sbin, /usr/sbin, or somewhere under /opt
- Tools like `which` and `whereis` can be used to obtain the location








# Working with files

## Viewing files 

- `cat` Prints file content to screen 
- `tac` Same as `cat` but starts from the bottom up
- `less` # Used to view larger files because it is a paging program (Add scrolling). Special options can be used to search for patterns (`/` for forward and `?` backwards)
- `tail` Print the last 10 lines of a file (with the -n flag or -15 the number can be changed)
- `head` Print the first 10 lines of a file (with the -n flag or -15 the number can be changed)

## Creating files and directories

- For creating files, touch is used. This tool is also used to change the timestamp of the file (or reset it). For example with the -t flag `touch -t 12092018  myfile` sets the date of `myfile` to the 9/12/2018
- Directories are created with `mkdir`

## Removing
Removing a directory is done with rmdir. The directory must be empty
To remove a directory and all of its contents rm -rf.
rm	Remove a file (Also accepts patterns)
rm –f	Forcefully remove a file
rm –i	Interactively remove a file(prompt every time)

## Moving and renaming
For files and directories both can be done with the mv command.
- `mv file other_file` changes the file name
- `mv file dir/dir/` moves the file
- `mv file dir/dir/other_file` moves the file and changes the name

## Standard file streams

When commands are executed, by default there are three standard file streams (or descriptors) always open for use: standard input (standard in or stdin), standard output (standard out or stdout) and standard error (or stderr).

stdin is normally the keyboard, stdout the terminal and stderr to a log file

In Linux, all open files are represented internally by what are called file descriptors. Simply put, these are represented by numbers starting at zero. stdin is file descriptor 0, stdout is file descriptor 1, and stderr is file descriptor 2

### IO Redirection

These streams can be redirected to:
- Read input from a file instead of the keyboard
- Output to a file instead of the screen
- Redirect the error messages

To redirect the input

```bash
command < input_file
```

For the output (and the standard error), `>` can be used, in combination with the file descriptor:
```bash
command > output_file # Redirects stdout
command 1> output_file #Same but with file descriptor
command 2> log_file # Redirects stderr
command > all_output_file 2>&1 #Both stdout and stderr to the same file
command >& all_output_file #Same as above, only in BASH
```

### Pipes

- Linux aims to have many simple commands instead of one very complicated
- For this, pipelines can be used: They allow for the output of a command to be redirected as the input for the next command in the pipeline
- ALlows for efficiency (no intermediate files required) and concurrency (commands in the pipeline don't have to wait for the previous ones to finish)
- Is done like `command1 | command2 | command3`


## Search files

### Wildcards

Basic search commands (and `ls`, among others) allow for the use of wildcards to search for files:
- `?` Matches any character
- `*` Matches any string (E.g `*.doc` would match all .doc files)
- `[abc]` Matches any character inside the brackets (`-` can be used for ranges)
- `[!abc` MAtches any character except the ones in brackets 

### `locate`

- Performs a search taking advantage of a previously constructed database of files and directories on your system. 
- Matches all entries that contain a specified character string.
- The database is constructed with `updatedb`. (Automatic in most linux distros once a day, can be run manually).
- Can be piped with `grep` to further filter the results
- Does not come in Ubuntu 19+ by default

### `find`

- Recurses down the filesystem tree from any particular directory (or set of directories) and locates files that match specified conditions. 
- The default pathname is always the present working directory.
- Different flags can be used (See `man find`):
    ```bash
    find . -name wa #Finds files and directories named wa
    find . -iname wa #Ignore case in the name matching
    find . -type d -name wa #Only directories
    find . -type f -name wa #Only files
    ```
- Also allows to directly process the results using the `-exec` option. Uses `{}` as placeholder for the results. (`-ok` can also be used to prompt every operation)
    ```bash
    find -name "*.swp" -exec rm {} ';' #Finds and removes all .swp files  
    ```
- Other tests to match include
  - `ctime n` When the inode metadata last changed (When it was created) (`n` is the number of days, can also be `+n` for bigger than and `-n`)
  - `atime n` Accessed/Last Read time
  - `mtime n` Modified/Last Written time
  - `cmin` `amin` `mmin` Same but in minutes
  - `size nU` Size of the file, `n` is the size (can also be `+n` o `-n`) and `U` is the unit (by default 512 bytes blocks, `k` for kilobytes, `M` for megabytes, `G` for gigabytes) 


# Installing Software

The core parts of a Linux distribution and most of its add-on software are installed via the Package Management System. Each package contains the files and other instructions needed to make one software component work well and cooperate with the other components that comprise the entire system

All linux distros have a low level and a high level package manager. The low level, is in charge of installing single packages correctly. The high level usually calls the low level one and addtionally, is in charge of searching for dependencies

![image](https://user-images.githubusercontent.com/64461123/119973603-fa0ae000-bfb3-11eb-998f-0d9fe57e614f.png)

## Debian Low Level: `dpkg`

```bash
dpkg --list # List all packages 
dpkg --listfiles package # Lists files inside the package
sudo dpkg --remove package # Removes packages (checks for dependencies)
```

## Debian High Level : `apt-get` and `apt-cache`

In addition, ubuntu provides `apt`. This provides a high-level commandline interface for the package management system. It is intended as an end user interface and
enables to easily use the most common options of `apt-get` and `apt-cache`. For more details see [here](https://itsfoss.com/apt-vs-apt-get-difference/)

