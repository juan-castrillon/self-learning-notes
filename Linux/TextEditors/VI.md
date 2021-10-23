---
title: Vim (Vi)
parent: Text Editors
grand_parent: Linux
---

# `vi`

- Defacto command-line-based text editor in Linux
- GUI versions are available for easier user (In GNOME `gvim` or `kvim` in KDE)
- Installed by default in most linux distributions (one almost always has access to it)
- When using `vi` or `vim`, all commands are entered through the keyboard. There is no need for the mouse
- A tutorial can be followed to learn the basics `vimtutor`


## Modes

Vi has 3 possible modes. In each, the keys do completely different things:

**Command Mode**
- Default mode of `vi`
- Each key is a command to the editor

**Insert Mode**
- From the command mode, typing <kbd>i</kbd> (among others)
- Allows to edit the text in the file
- Indicated by `? INSERT ?` in the bottom
- To go back to command mode, press <kbd>esc</kbd>

**Line Mode**
- From the command mode, typing <kbd>:</kbd>
- Each key is an external command (write to file, exit, etc.)
- To go back to command mode, press <kbd>esc</kbd>


# Commands

## Basics

|    Command   |                          Function                          |
|:------------:|:----------------------------------------------------------:|
| `vi myfile`    | Start the editor and edit `myfile`                           |
| `vi -r myfile` | Start and edit `myfile` in recovery mode from a system crash |
| `:r` `file2`     | Read in `file2` and insert at current position               |
| `:w`           | Write to the file                                          |
| `:w``myfile`    | Write out to `myfile`                                        |
| `:w!` `file2`    | Overwrite `file2`                                            |
| `:x` or `:wq`   | Exit and write out modified file                           |
| `:q`           | Quit                                                       |
| `:q!`          | Quit even though modifications have not been saved         |
| `:set number`  | Show line numbers on editor                                |

## Moving the cursor

|       Command       |                        Action                        |
|:-------------------:|:----------------------------------------------------:|
| arrow keys          | To move up, down, left and right                     |
| <kbd>j</kbd> or <kbd>return</kbd>         | To move one line down                                |
| <kbd>k</kbd>                   | To move one line up                                  |
| <kbd>h</kbd> or <kbd>Backspace</kbd>      | To move one character left                           |
| <kbd>l</kbd> or <kbd>Space</kbd>          | To move one character right                          |
| <kbd>%</kbd>                   | (When located in a "([{}])") Finds the matching sign |
| <kbd>\\</kbd> + <kbd>*</kbd>                  | Find next occurence of current word (Find next ones with more <kbd>*</kbd>)                  |
| <kbd>\\</kbd> + <kbd>#</kbd>                  | FInd previous occurence of current word              |
| <kbd>0</kbd>                   | To move to beginning of line                         |
| <kbd>$</kbd>                   | To move to end of line                               |
| <kbd>w</kbd>                   | To move to beginning of next word                    |
| `:0` or `1G`            | To move to beginning of file                         |
| `:n` or `nG`            | To move to line n                                    |
| `:$` or <kbd>G</kbd>             | To move to last line in file                         |
| <kbd>CTRL</kbd> + <kbd>F</kbd> or <kbd>Page Down</kbd> | To move forward one page                             |
| <kbd>CTRL</kbd> + <kbd>B</kbd> or <kbd>Page Up</kbd>   | To move backward one page                            |
| `^l`                  | To refresh and center screen                         |

## Search

| Command | Action |
|:---:|:---:|
| <kbd>f</kbd> | Search first occurence of character (`fo` finds the first 'o' after the cursor) (Can be combined with a number, e.g `3fo` finds the third 'o') |
| `/pattern` | Search forward for pattern |
| `?pattern` | Search backward for pattern |
| <kbd>n</kbd> | Move to next occurrence of search pattern |
| <kbd>N</kbd> | Move to previous occurrence of search pattern |

## Modifying Text

| Command | Action |
|:---:|:---:|
| <kbd>a</kbd> | Append text after cursor; stop upon Escape key |
| <kbd>A</kbd> | Append text at end of current line; stop upon Escape key |
| <kbd>i</kbd> | Insert text before cursor; stop upon Escape key (If type a number before, text is repeated) |
| <kbd>I</kbd> | Insert text at beginning of current line; stop upon Escape key |
| <kbd>o</kbd> | Start a new line below current line, insert text there; stop upon Escape key |
| <kbd>O</kbd> | Start a new line above current line, insert text there; stop upon Escape key |
| <kbd>r</kbd> | Replace character at current position |
| <kbd>R</kbd> | Replace text starting with current position; stop upon Escape key |
| <kbd>x</kbd> | Delete character at current position |
| `Nx` | Delete N characters, starting at current position |
| `dw` | Delete the word at the current position |
| `cw` | Replace word at current position |
| <kbd>D</kbd> | Delete the rest of the current line |
| `dd` | Delete the current line |
| `Ndd` or `dNd` | Delete N lines |
| <kbd>u</kbd> | Undo the previous operation |
| `yy` | Yank (copy) the current line and put it in buffer |
| `Nyy` or `yNy` | Yank (copy) N lines and put it in buffer |
| <kbd>p</kbd> | Paste at the current position the yanked line or lines from the buffer |

## External Commands

Typing `:sh` opens an "external command" shell.
- After logging out, the editor is back

Type `:!` to execute a command (command goes after !)
- The placeholder `%` represents the file currently being edited
- For example `! wc %` executes word count on the file 