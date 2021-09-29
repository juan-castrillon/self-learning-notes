---
title:  Text Editors
parent: Linux
nav_order: 9
has_children: true
---

# Text Editors

# `nano`

Terminal based
Very Simple
Provides help in the lower part of screen

# `gedit`

Similar to notepad
Graphical editor


Both vi and emacs have a basic purely text-based form that can run in a non-graphical environment. They also have one or more graphical interface forms with extended capabilities; these may be friendlier for a less experienced user.

# `vi`

In order to facilitate using `vi` or `vim`:
- There are GUIs for it (In GNOME `gvim` or `kvim` in KDE)
- A tutorial can be followed to learn the basics `vimtutor`

When using vi, all commands are entered through the keyboard. There is no need for the mouse

## Modes

Vi has 3 possible modes. In each, the keys do completely different things:

**Command Mode**
- Default mode of vi
- Each key is a command to the editor

**Insert Mode**
- From the command mode, typing <kbd>i</kbd>
- Allows to edit the text in the file
- Indicated by `? INSERT ?' in the bottom
- To go back to command mode, press <kbd>esc</kbd>

**Line Mode**
- From the command mode, typing <kbd>:</kbd>
- Each key is an external command (write to file, exit, etc.)
- To go back to command mode, press <kbd>esc</kbd>


vi myfile	Start the editor and edit myfile
vi -r myfile	Start and edit myfile in recovery mode from a system crash
:r file2	Read in file2 and insert at current position
:w	Write to the file
:w myfile	Write out to myfile
:w! file2	Overwrite file2
:x or :wq	Exit and write out modified file
:q	Quit
:q!	Quit even though modifications have not been saved

Changing the cursor

arrow keys	To move up, down, left and right
j or <ret>	To move one line down
k	To move one line up
h or Backspace	To move one character left
l or Space	To move one character right
0	To move to beginning of line
$	To move to end of line
w	To move to beginning of next word
:0 or 1G	To move to beginning of file
:n or nG	To move to line n
:$ or G	To move to last line in file
CTRL-F or Page Down	To move forward one page
CTRL-B or Page Up	To move backward one page
^l	To refresh and center screen

Search

/pattern	Search forward for pattern
?pattern	Search backward for pattern
n	Move to next occurrence of search pattern
N	Move to previous occurrence of search pattern

Modifying Text

a	Append text after cursor; stop upon Escape key
A	Append text at end of current line; stop upon Escape key
i	Insert text before cursor; stop upon Escape key
I	Insert text at beginning of current line; stop upon Escape key
o	Start a new line below current line, insert text there; stop upon Escape key
O	Start a new line above current line, insert text there; stop upon Escape key
r	Replace character at current position
R	Replace text starting with current position; stop upon Escape key
x	Delete character at current position
Nx	Delete N characters, starting at current position
dw	Delete the word at the current position
D	Delete the rest of the current line
dd	Delete the current line
Ndd or dNd	Delete N lines
u	Undo the previous operation
yy	Yank (copy) the current line and put it in buffer
Nyy or yNy	Yank (copy) N lines and put it in buffer
p	Paste at the current position the yanked line or lines from the buffer

External Commands

Typing `:sh` opens an "external command" shell.
- After logging out, the editor is back

Type `:!` to execute a command (command goes after !)
- The placeholder `%` represents the file currently being edited
- For example `! wc %` executes word count on the file 




