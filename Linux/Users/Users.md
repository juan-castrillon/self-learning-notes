---
title: Users
parent: User Environment
grand_parent: Linux
---

# Users and groups

Linux is a multi-user system.

All users have a unique user id UID (greater than 1000). THis is used to identify them in the system.

Groups:
- are used to organize users and give a shared set of permission and accesses. 
- `/etc/group` shows groups and their members. 
- Groups also have GID group ids.

Typing `id` gives information about users and groups they belong to

## Current user

To identify who is currently using the terminal, `whoami` is used.

To see all users currently logged in `who` or `who -a` for more details.


## Adding and removing Users

Users can be added and deleted in the command line, only by a root user.

To add, `sudo useradd benito`. This will 
    - create a user
    - set its home directory in `/home/benito`
    - populate it with the files from `/etc/skel/`
    - Set the default shell to `bash`
    - All according to `/etc/default/useradd`

To delete `sudo userdel benito`
    - This will leave the home directory (temporal inactivation)
    - To remove everything `userdel -r benito`

## Modifying Groups

Groups can also be created, modified and removed.

To create a new group use `groupadd name`.

To delete it `groupdel name`.

To add an user to an existing group use `usermod -aG group_name username`
    - `-a` Is used to append, and not delete other group memberships
    - `-G` is used to list all groups that the user belongs to
    - Information can be verified with `groups username` or `id username`

To delete an user from a group, the `usermod` command is used in a trick:
`usermod -G username username` makes that the user only has a membership in his default group

# Root user

In linux, the root user is also called the superuser.Has access to everything in the system

**Is very dangerous and often not justified to grant root access to a user**

One can use `sudo` to execute some tasks with root permissions on a temporary basis
    - Granted in a peruser basis
    - Configuration is stored in `/etc/sudoers` file and `/etc/sudoers.d` directory
    - Recommended is to use the `visudo` tool

Other less recommended option is to use `su` which allows to substitute another user (in this case the root)