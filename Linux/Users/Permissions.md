---
title: File Permissions
parent: User Environment
grand_parent: Linux
---

# File Permissions

In Linux files are associated with an owner (user) and with a group that has permissions on the file (read, write, execute)

Commands to change this are:
- `chown` to change ownership. THe owner can manipulate the file, for example delete it
- `chgroup` to change group ownership
- `chmod` to change the permissions for a file (can be done for owner, group and other)

## Changing permissions

Permissions in a file can be of three types:
- write(**w**)
- read(**r**)
- execute(**x**)

These 3 types fall into three categories:
- user/owner (**u**)
- group (**g**)
- others (**o**)

WIth this logic, permissions can be given in particular 
```bash
ls -l somefile
-rw-rw-r-- 1 student student 1601 Mar 9 15:04 somefile
chmod uo+x,g-w somefile #User and others execute, remove write from group
ls -l somefile
-rwxr--r-x 1 student student 1601 Mar 9 15:04 somefile
```

The command can be simplified using a simple replacement for numbers:
- 4 for read permissions
- 2 for write permissions
- 1 for execute

For example `chmod 755 file` gives the owner all permissions, and the other two read and execute