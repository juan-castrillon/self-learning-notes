---
title:  Comparing Files
parent: Files
grand_parent: Linux
---

# Knowing the type

In linux, extensions of file dont help the system determine what they are (A `.txt` file could be an executable)

`file` can be used to list the type

# Listing differences in files

For this `diff` is used (Or `diff3`)

It can compare two files(normally text files, for binary files use `cmp`)

Can be used to generate a "patch" file that describes all changes to a file(s):
```bash
diff -Nur file1 file2 > patchFile
```
Has multiple options to tune the comparison (See `man diff`)

# Applying Patches

Once the patch files are generated, `patch` can be used to apply a patch to a file or directory

Is easier (and smaller) to distribute patches to change files and configs.

```bash
patch -p1 < patchfile ## Can be used to patch entire directories
patch originalfile patchfile
```