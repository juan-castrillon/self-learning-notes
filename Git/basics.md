---
title: Basics
parent: Git
nav_order: 1
---

Version control system  
    Tracks and manages changes over time

What does it do?
    Track changes
    Compare version
    TIme travel to old version (or revert)
    COmbine changes and collaborate
    

# Basics

What is a git repo

Workspace
Has its own history
Watches changes in a given folder

## Commit
Checkpoints
Has a message that describes it
multi step process
1. Add the changes that I want to have in the commit

`git add`

2. Commit the added changes (staged) into a commit

`git commit`
    - It will promt for a commit message using the default editor
    - Can be changed with `git config --global core.editor`
      - Reference in the book
    - with `-m` message can be passed directly
    - https://git-scm.com/docs/git-commit
  

# log
`git log` retrieves a list of commits
with `--oneline` output is compacted
