---
title: Basic File Operations
parent: Files
grand_parent: Linux
---

Basic Operations include:
- Creation
- Removal
- Move and Rename
- View contents
- Search


# Creating files and directories

- For creating files, `touch` is used. This tool is also used to change the timestamp of the file (or reset it). For example with the `-t` flag `touch -t 12092018  myfile` sets the date of `myfile` to the 9/12/2018
- Directories are created with `mkdir`


# Removing
- Removing a directory is done with `rmdir`. The directory must be empty
- To remove a directory and all of its contents `rm -rf`.
- `rm` Removes a file (Also accepts patterns). Has additional options, for example `–f`	to forcefully remove a file or `–i` to interactively remove it(prompt every time)

# Moving and renaming
For files and directories both can be done with the `mv` command.
- `mv file other_file` changes the file name
- `mv file dir/dir/` moves the file
- `mv file dir/dir/other_file` moves the file and changes the name


# Viewing files 

- `cat` Prints file content to screen 
- `tac` Same as `cat` but starts from the bottom up
- `less` Used to view larger files because it is a paging program (Add scrolling). Special options can be used to search for patterns (`/` for forward and `?` backwards)
- `tail` Print the last 10 lines of a file (with the -n flag or -15 the number can be changed)
- `head` Print the first 10 lines of a file (with the -n flag or -15 the number can be changed)

# Search files

## Wildcards

Basic search commands (and `ls`, among others) allow for the use of wildcards to search for files:
- `?` Matches any character
- `*` Matches any string (E.g `*.doc` would match all .doc files)
- `[abc]` Matches any character inside the brackets (`-` can be used for ranges)
- `[!abc` MAtches any character except the ones in brackets 

## `locate`

- Performs a search taking advantage of a previously constructed database of files and directories on your system. 
- Matches all entries that contain a specified character string.
- The database is constructed with `updatedb`. (Automatic in most linux distros once a day, can be run manually).
- Can be piped with `grep` to further filter the results
- Does not come in Ubuntu 19+ by default

## `find`

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
  - `size nU` Size of the file, `n` is the size (can also be `+n` o `-n`) and `U` is the unit (by default 512 bytes blocks, `k` for kilobytes, `M` for megabytes, `G` for gigabytes).