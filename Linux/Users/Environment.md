---
title: Environment
parent: User Environment
grand_parent: Linux
---

# Starting up the Environment

The command shell uses startup files to set up the user environment
This includes
    - PATH    
    - Custom Prompts
    - Aliases
    - Default text editor
    - etc.

Files located in `/etc` are for system-wide configuration while files in the user's home directory override this ones with particular ones for each user

When first logging in the order is
1. `/etc/profile`
2. If exists (uses first found and ignores the rest)
   1. `~/.bash_profile`
   2. `~/.bash_login`
   3. `~/.profile`

Every time a new terminal is opened (not first login), `~/.bashrc` is loaded. This is also normally included in one of the three user owned startup files. This file is normally configured by the user

## Aliases

- Aliases can be created for commands
- In `.bashrc` or a separate `.bash_aliases` file
- The format is `alias waa="some command"`
- To list all available use `alias`

# Environment Variables

Environment variables are quantities that have specific values which may be utilized by the command shell, such as bash, or other utilities and applications

- They can be seen with `env`, or `export` or `set`
- To see an specific one `echo $NAME`

## Setting environment variables

To set an env variable:
```bash
export NAME=value
```
This sets the variable only for the current shell (and child processes).


To set it permanently, has to be added to:

  - `.bashrc` or `.profile` (better as not only applies to bash) as `export NAME=value`
  - `/etc/environment` for system wide configuration, just added as `NAME=value`

After this, the file has to be sourced (`source .bashrc` or `. .bashrc`) or a new shell has to be opened

A third option, sets a variable to be fed as one shot to a command
```bash
NAME=value command
```

## Some default variables
- `$HOME` Home directory for current user
- `$PATH` List of directories where executable binaries can be found
    - Each separated by `:`
    - new ones can be temporarly added with `export PATH=new/bin:$PATH`
- `$SHELL` Fullpath to user's default shell
- `$PS1` Used to customize the prompt in the shell (e.g `jpcr@machine: ~`)


# Command history

Bash keeps a history of the commands used
    - With up and down arrows can be navigated
    - To see the most recent ones use `history`
    - The complete info is stored in `~/.bash_history`
    - <kbd>Ctrl</kbd> + <kbd>r</kbd> allows for a reverse search in the commands
    
Certain env variables control the saving process
- `$HISTFILE`: The location of the history file.
- `$HISTFILESIZE`: The maximum number of lines in the history file (default 500).
- `$HISTSIZE`: The maximum number of commands in the history file.
- `$HISTCONTROL`: How commands are stored.
- `$HISTIGNORE`: Which command lines can be unsaved.