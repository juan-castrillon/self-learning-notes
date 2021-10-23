---
title:  User Environment
parent: Linux
nav_order: 10
has_children: true
---

# Accounts users and groups

## Current user

To identify who is currently using the terminal, `whoami` is used.

To see all users currently logged in `who` or `who -a` for more details.

# Sarting up the Environment

The command shell uses startup files to set up the user environment
This includes
    PATH    
    Custom Prompts
    Aliases
    Default text editor
    etc.

Files located in `/etc` are for system-wide configuration while files in the user's home directory override this ones with particular ones for each user

When first logging in the order is
1. `/etc/profile`
2. If exists (uses first found and ignores the rest)
   1. `~/.bash_profile`
   2. `~/.bash_login`
   3. `~/.profile`

Everytime a new terminal is opened (not first login), `~/.bashrc` is loaded. This is also normally included in one of the three user owned startup files. This file is normally configured by the user

## ALiases

Aliases can be created for commands
In `.bashrc` or a separate `.bash_aliases` file
The format is `alias waa="some command"`
To list all available use `alias`

## Users

All users have a unique user ide UID (greater than 1000)
Groups are used to organize users and give a shared set of permission and accesses. `/etc/group` shows groups and their members
Groups also have GID group ids
Typing `id` gives information about users and groups they belong to

## Adding and removing

Users can be added and deleted in CL, only by a root user
To add, `sudo useradd benito`. This will 
    create a user
    set its home directory in `/home/benito`
    populate it with the files from `/etc/skel/`
    Set the default shell to `bash`
    All according to `/etc/default/useradd`
To delete `sudo userdel benito`
    This will leave the home directory (temporal inactivation)
    TO remove everrything `userdel -r benito`

Groups can also be created, modified and removed
To create a new group use `groupadd name`
To delete it `groupdel name`
To add an user to an existing group use `usermod -aG group_name username`
    `-a` Is used to append, and not delete other group memberships
    `-G` is used to list all groups that the user belongs to
    Information can be verified with `groups username` or `id username`
To delete an user from a group, the `usermod` command is used in a trick
    `usermod -G username username` makes that the user only has a membership in his default group

# Root user

In linux called the superuser
Has access to everything in the system
Is very dangerous and often not justified to grant root access to a user
One can use `sudo` to execute some tasks with root permissions on a temporary basis
    Granted in a peruser basis
    Configuration is stored in `/etc/sudoers` file and `/etc/sudoers.d` directory
    Recommended is to use the `visudo` tool
Other less recommended option is to use `su` which allows to substitute another user (in this case the root)


# Environment Variables

Environment variables are quantities that have specific values which may be utilized by the command shell, such as bash, or other utilities and applications

They can be seen with `env`, or `export` or `set`

To see an specific one `echo $NAME`

## Setting env variables

To set an env variable
```bash
export NAME=value
```
This sets the variable only for the current shell (and child processes)
To set it permanently, has to be added to
    `.bashrc` or `.profile` (better as not only applies to bash) as `export NAME=value`
    `/etc/environment` for system wide configuration, just added as `NAME=value`
After this, the file has to be sourced (`source .bashrc` or `. .bashrc`) or a new shell has to be opened

A third option, sets a variable to be fed as one shot to a command
```bash
NAME=value command
```

## Some default variables
`$HOME` Home directory for current user
`$PATH` List of directories where executable binaries can be found
    Each separated by `:`
    new ones can be temporarly added with `export PATH=new/bin:$PATH`
`$SHELL` Fullpath to user's default shell
`$PS1` Used to customize the prompt in the shell (e.g `jpcr@machine: ~`)


# Command history

Bash keeps a history of the commands used
    With up and down arrows can be navigated
    To see the most recent ones use `history`
    The complete info is stored in `~/.bash_history`
    <kbd>Ctrl</kbd> + <kbd>r</kbd> allows for a reverse search in the commands
    
Certain env variables control the saving process
- `$HISTFILE`: The location of the history file.
- `$HISTFILESIZE`: The maximum number of lines in the history file (default 500).
- `$HISTSIZE`: The maximum number of commands in the history file.
- `$HISTCONTROL`: How commands are stored.
- `$HISTIGNORE`: Which command lines can be unsaved.