---
title: Git Basic Commands
parent: Git
nav_order: 1
---
# Basic GIT Commands

## `git init`

Initializes a git repository in the current directory. This is done by creating a hidden `.git` directory.

If used with a name as an argument like 
```bash
git init example
```
It will first create a folder called `example` and inside this folder initialize the repo.

> To make a directory not a git repository anymore, just delete the hidden `.git` folder.

## `git status`

Shows the current state of the files according to the basic workflow (un-tracked, staged).

## `git add filename`

Add a file to staging. This is done before committing because only staged files (or changes) are added to the commit

If used like
```bash
git add -A
```
```bash
git add .
```
Adds all the files that have been modified