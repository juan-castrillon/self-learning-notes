`git diff`

- View changes between commits, branches, files, working directory, etc.
- Normally used with `git status` and `git log`

No options, shows all changes in the wd that are not staged.

## Read a diff

Example:

```
diff --git a/rainbow.txt b/rainbow.txt
index 0b75516..26ec8e7 100644
--- a/rainbow.txt
+++ b/rainbow.txt
@@ -3,4 +3,5 @@ orange
 yellow
 green
 blue
-purple
\ No newline at end of file
+indigo
+violet
```

First line `diff --git a/rainbow.txt b/rainbow.txt` shows which two files is comparing. Is normally the same file but can be set up to be different. Original is going to be A and new is B

```
--- a/rainbow.txt
+++ b/rainbow.txt
```
`-` will be used for changes in file a, and `+` for changes in file b

### Chunks
- git diff will only show the modified lines, with some context (some lines before and after)
- Chucnk header `@@ -3,4 +3,5 @@ ` mean:
  - From file a, 4 lines are extracted starting from line 3 (in the chunk)
  - From file b, 5 lines are extracted starting from line 3 (in the chunk)


### Changes
- THings in the chunk with `-` or `+`

## Different ways to use it

`git diff` Changes in wd that are not in the staging area (what we could tell git to add to staging)

`git diff HEAD` compare HEAD and wd. Changes in the wd since the last commit. DIfferent to above it will show staged and unstaged changes



`git diff --staged` or `git diff --cached`. Show only staged changes, what will be commited

- `git diff <OPTIONS> file` shows changes for a specific file
- `git diff <OPTIONS> branch1..branch2`, `git diff <OPTIONS> branch1 branch2` to compare changes between two branches
  - Order matters to see that is a and b
- `git diff commit1..commit2` to compare changes between two commits

