---
title: Emacs
parent: Text Editors
grand_parent: Linux
---

# `emacs`


- Does not work with modes
- Uses the <kbd>Ctlr</kbd> and meta (<kbd>Alt</kbd> or <kbd>esc</kbd>) for sepcial commands (instead of modes)

emacs myfile	Start emacs and edit myfile
CTRL-x i	Insert prompted for file at current position
CTRL-x s	Save all files
CTRL-x CTRL-w	Write to the file giving a new name when prompted
CTRL-x CTRL-s	Saves the current file
CTRL-x CTRL-c	Exit after being prompted to save any modified files

Changing cursor

arrow keys	Use the arrow keys for up, down, left and right
CTRL-n	One line down
CTRL-p	One line up
CTRL-f	One character forward/right
CTRL-b	One character back/left
CTRL-a	Move to beginning of line
CTRL-e	Move to end of line
Meta-f	Move to beginning of next word
Meta-b	Move back to beginning of preceding word
Meta-<	Move to beginning of file
Meta-g-g-n	Move to line n (can also use 'Esc-x Goto-line n')
Meta->	Move to end of file
CTRL-v or Page Down	Move forward one page
Meta-v or Page Up	Move backward one page
CTRL-l	Refresh and center screen

Search
CTRL-s	Search forward for prompted pattern, or for next pattern
CTRL-r	Search backwards for prompted pattern, or for next pattern


EDit text
CTRL-o	Insert a blank line
CTRL-d	Delete character at current position
CTRL-k	Delete the rest of the current line
CTRL-_	Undo the previous operation
CTRL- (space or CTRL-@)	Mark the beginning of the selected region. The end will be at the cursor position
CTRL-w	Delete the current marked text and write it to the buffer
CTRL-y	Insert at current cursor location whatever was most recently deleted


