# Linux Notes 📘

Linux notes — Covers fundamentals, the file system, users & permissions, process management, networking, and security basics, with extra interview-prep material at the end.

---

## 📑 Table of Contents

1. [Linux Fundamentals](#1-linux-fundamentals)
2. [Linux History & Architecture](#2-linux-history--architecture)
3. [Shell & Command Prompt](#3-shell--command-prompt)
4. [Basic Linux Commands](#4-basic-linux-commands)
5. [Vim Editor](#5-vim-editor)
6. [Helping Commands](#6-helping-commands)
7. [File & Directory Operations (cp, mv)](#7-file--directory-operations-cp-mv)
8. [Absolute vs Relative Path](#8-absolute-vs-relative-path)
9. [Linux Users](#9-linux-users)
10. [Linux Directory Structure (19 Directories)](#10-linux-directory-structure-19-directories)
11. [User & Group Management](#11-user--group-management)
12. [Account Locking & Expiration (chage)](#12-account-locking--expiration-chage)
13. [sudo & su](#13-sudo--su)
14. [File Permissions & umask](#14-file-permissions--umask)
15. [Link Count & Inodes](#15-link-count--inodes)
16. [Hard Link vs Soft Link](#16-hard-link-vs-soft-link)
17. [Archiving & Compression](#17-archiving--compression)
18. [Crontab](#18-crontab)
19. [Search & Filter Utilities](#19-search--filter-utilities)
20. [Linux Process Management](#20-linux-process-management)
21. [Linux Networking Fundamentals](#21-linux-networking-fundamentals)
22. [Extra / Miscellaneous Commands](#22-extra--miscellaneous-commands)
23. [Advanced Permissions: umask, Sticky Bit, ACL](#23-advanced-permissions-umask-sticky-bit-acl)
24. [Network Monitoring Tools](#24-network-monitoring-tools)
25. [🚀 Interview Prep / Advanced Topics (Added)](#25-interview-prep--advanced-topics-added)

---

## 1. Linux Fundamentals

### What is Linux?
linux is a kernel

Linux is an open-source, kernel based operating system widely used in server and cloud environments. It provides a platform to run applications and allows us to manage hardware resources, files, processors, users, networking, and security.

Technically Linux is the kernel, which manages system resources such as CPU, memory, processes, storage and hardware devices.

### What is Kernel?
Kernel is core component/part of an Operating System that acts as a bridge between hardware and software. It manages resources such as CPU, Memory, processes, devices and files.

kernel directly communicate with hardware like CPU, RAM, MEMORY, DEVICE DRIVERS etc…
- manage processes
- control memory
- handles device drivers

### What is an Operating System?
- OS is complete system S/W that manages computer hardware and software & provides a user interface
- Act as a bridge between User and Hardware
- An OS is backbone of any computer and manages Computers Hardware + Software resources
- An OS is a mediator between user and computer hardware, we can say it is a translator who converts high level (human lang) lang into low level (binary language) and vise versa
- OS performs task, function given by the user
- OS controls H/w (CPU, Memory, Disk)
- Runs application/prog
- Manages files & processes
- Provides an interface (CLI – Command line Interface and GUI – Graphical User Interface)

### Linux OS
Linux OS is an Open Source OS, which means it allow users to change It's source code according to their req.
Anybody can change Linux program and can edit it to create new OS.

**Features**
- More Secure
- Open source
- Fast & lightweight
- Used everywhere

**Analogy**
- Kernel – engine of the car
- OS – Whole car

**Different types of OS**
- Desktop OS – Windows, macOS, Linux
- Server OS – Linux (Ubuntu Server, CentOS), Windows Server
- Mobile OS – Android, iOS
- Embedded OS – designed for specific devices (IoT, routers)

### Difference between Linux and Windows

| Linux | Windows |
|---|---|
| Open-source | Proprietary/closed-source |
| Mostly free | Requires a license for many editions |
| Highly customizable | Less customizable |
| Commonly uses CLI | Commonly uses GUI |
| More commonly used for servers | Commonly used for desktops |
| More lightweight | Generally more resource-intensive |
| Uses package managers like apt, yum, dnf | Uses installers and tools like Microsoft Store/winget |
| Strong file permissions and security | Uses ACLs and other Windows security mechanisms |
| Popular in DevOps and cloud environments | Popular for desktop applications and enterprise workloads |

Linux is an open-source, highly customizable operating system commonly used for servers and DevOps, while Windows is a proprietary operating system commonly used for desktops and enterprise applications.
Linux is mainly CLI-oriented, whereas Windows provides a user-friendly GUI.

### Shell
Shell is a Command Line Interface (CLI) that allows users to interact with the Operating System by executing commands.
It acts as an interface between user and operating system.

Ex. Bash, Zsh, Fish, PowerShell

It allows User to gives command to the system.

---

## 2. Linux History & Architecture

### History
- Linux is a kernel created by **Linus Torvalds** (Computer Science Student from Helsinki University, Finland) in 1991
- He started Linux as a personal project to create a free OS kernel
- On 25th Aug 1991, Linus Torvalds announced Linux on the internet
- In Sep 1991, Linux kernel 0.01 was released
- In Mar 1994, Linux kernel 1.0 stable was released

### Linux Architecture

**Architecture Flow:**
```
User -> Application -> Shell -> Kernel -> Hardware
```

### GNU
- GNU is a free and open source OS project started to create S/W that anyone can use, modify & share freely
- GNU stands for **"GNU's Not UNIX"**
- GNU was started by **Richard Stallman** at the Free Software Foundation in 1983
- The goal of GNU was to develop a complete free OS similar to UNIX, but without restriction
- GNU tools + Linux Kernel = Linux OS

### What is a Server?
Server is a system which provides services, resources, data to other computers (clients).
- Server = machine that provides / hosts our application
- Server = computer that provides a service
- Client = computer that sends a request

### How the Internet Works
All continents in the world are connected with each other via optical fibre cables.
These optical fibre cables are laid through the sea.
Data travels through that optical fibre from source to destination.

---

## 3. Shell & Command Prompt

The Linux command prompt is a powerful interface for interacting with your operating system. It allows users to execute commands, manage files, and perform administrative tasks effectively.

The prompt typically looks like this: `username@hostname:~$`

- **Username** = your current user account
- **Hostname** = the name of the computer
- **Prompt symbol** `$` = represents standard/local/regular/common user, `#` = represents root user

---

## 4. Basic Linux Commands

| # | Command | Description |
|---|---|---|
| 1 | `ls` | list directories |
| 2 | `ls -l` | long list |
| 3 | `ll` | long list |
| 4 | `ls -lh` | long list, human readable |
| 5 | `ls -a` | show hidden files |
| 6 | `ls -al` | all files including hidden |
| 7 | `ls -alt` | all files including hidden, sorted by time |
| 8 | `ls -a /etc/skel/` | find destination (skel files) |
| 9 | `ls .ssh` | authorized file |
| 10 | `cd` | change directories |
| 11 | `touch` | create an empty file / update timestamps |
| 12 | `touch file1.txt file2.txt` | create multiple files with different names |
| 13 | `touch file{1..10}.txt` | creates files 1–10 |
| 14 | `mkdir` | create an empty directory |
| 15 | `mkdir -p dir-name` | for multiple/nested directory |
| 16 | `mkdir -p dir{1..10}` | creates 10 directories with same base name |
| 17 | `rm` | delete file |
| 18 | `rmdir` | delete empty directory |
| 19 | `rm -r` | delete directory recursively (with contents) |
| 20 | `rm -rf` | delete directories forcefully |
| 21 | `rm ./*` | delete all files |
| 22 | `./` | go to current/home directory |
| 23 | `../` | go 1 step back to previous directory |
| 24 | `cp` | copy files |
| 25 | `cp -r` | copy directories |
| 26 | `mv` | rename/move file/directories |
| 27 | `cat file.txt` | read the file's content |
| 28 | `cat file.txt file2.txt` | read multiple files at a time |
| 29 | `cat > file-name` | edit file content (`>` = overwrite) |
| 30 | `cat >> file-name` | show previous + new content (`>>` = append) |
| 31 | `zcat` | read/show the content from a zip file |
| 32 | `clear` | clear the terminal (`Ctrl + L` = shortcut) |
| 33 | `history` | show history of commands on terminal |
| 34 | `head` | show first 10 lines of file |
| 35 | `tail` | show last 10 lines of file |
| 36 | `less` | show content in page format (small pages) |
| 37 | `more` | show content of file in page format (large pages) |
| 38 | `tree` | list directory in tree diagram / shows file/dir in tree-like structure |
| 39 | `~` | tilde — go to home directory |
| 40 | `stat filename` | show full info |
| 41 | `alias` | make shortcuts of commands |
| 42 | `var` | changing continuously |
| 43 | `sort file-name` | sort the data of a file into alphabetical order |
| 44 | hardlink | create a shortcut of a file, also used for saving critical data |
| 45 | softlink | shortcut path |
| 46 | `vim` | edit text file (vi, vim, nano, pico = 4 editors) |
| 47 | `nano` | text editor |
| 48 | `whoami` | identify current user |
| 49 | `hostname` | show machine name |
| 50 | `uname -a` | display system information |

---

## 5. Vim Editor

### What is Vim?
Vim (Vi IMproved) is a powerful and versatile text editor widely used in the Linux ecosystem.
Originating from the Vi editor, Vim offers enhanced features such as syntax highlighting, plugins, and an extensive set of commands.

**Installation:**
```bash
sudo apt install vim
vim --version   # check vim version
```

Vim editor has 4 modes:

| Command Mode | Insert Mode | Execution Mode | Visual Mode |
|---|---|---|---|
| By default mode | Editing mode | Save/quit file mode | Shows content visually |
| Key shortcut = `esc` | Key shortcut = `i` | Key shortcut = `:wq` or `:wq!` (forcefully save/quit) | Key shortcut = `v` |

### Shortcuts of Command Mode
```
i        = enter into insert mode
esc      = return to command mode
yy       = copy the line
x        = delete character
dd       = delete the line
p        = paste the line
yw       = copy word
dw       = delete word
u        = undo
ctrl+r   = redo
h        = left
l        = right
k        = up
j        = down
G        = go to last / bottom
gg       = go to top
0        = jump to beginning of a line
$        = jump to end of a line
/word    = search particular word
:set nu    = set line numbers
:set nonu  = remove line numbers
:10        = jump to 10th line
<no>yy     = copy multiple lines
```

### Shortcuts of Insert Mode
```
i        = enter into insert mode
I        = enter insert mode at the beginning of the line
Ctrl+a   = jump to beginning of the line
Ctrl+e   = jump to end of the line
Esc      = exit from insert mode
```

### Shortcuts of Execute Mode
```
:w    = save file
:q    = quit/exit the file
:wq   = save and exit from file
:wq!  = save and exit forcefully
x     = alternative for file saving
zz    = alternative for file saving
```

### Shortcuts of Visual Mode
Visual mode shows content in visual mode and allows selecting a particular section by cursor. We can copy/delete lines/words by selecting it.

```
v        = character-wise selection
V        = line-wise selection
Ctrl+v   = block selection
y        = copy the line
d        = delete line
p        = paste text
```

### Key Shortcuts of nano
```
Ctrl+O = overwrite the file / save
Ctrl+X = exit from file
```

---

## 6. Helping Commands

4 helping commands:

| Command | Description |
|---|---|
| `man` | shows manual of file/dir (an interface to the system reference manuals) |
| `whatis` | shows 1-line description of file/dir |
| `--help` | helps understand file/command usage |
| `info` | shows info of the file/dir |

---

## 7. File & Directory Operations (cp, mv)

### cp — Copy Files
```bash
cp file1.txt file2.txt                        # file1.txt copied to file2.txt
cp file1.txt /home/user/documents/             # file copied to documents folder
cp file1.txt file2.txt file3.txt /home/user/documents/   # copy multiple files
```

### Copy Directory (`-r` = recursively)
```bash
cp -r dir-name destination
cp -r dir1 /home/user/backup/     # dir1 copied to backup folder
```
`cp` copies the file or directory and pastes it to the new location, but the file also remains at its old location. Same applies for directories.

### mv — Move Files
`mv` moves/renames files or directories from an old location to a new location — it removes the file/dir from its old location.

**Move** — if the destination is a directory, Linux moves the file (this happens when the new directory already exists):
```bash
mv file1.txt /home/user/documents/    # file1.txt moved to documents
mv dir /home/user/documents/          # dir moved to documents folder
mv file1.txt file2.txt folder/        # multiple files moved to folder
```

**Rename** — if the destination is just a new name, Linux renames the file:
```bash
mv file1.txt file2.txt   # rename file1.txt -> file2.txt
mv dir1 dir2              # rename dir1 -> dir2
```

**Slash (`/`) meanings**
- `/` at front means root user path: `/home/user/dir-name/`
- `/` at back means folder: `folder/`
- `/` between words shows path hierarchy: `/home/sahil/documents` = root → home → sahil → documents

**Move + Rename together:**
```bash
mv file1.txt documents/newfile.txt
```
This moves `file1.txt` to `documents` and renames it to `newfile.txt`.

### Creating an alias
```bash
cp -r /etc/skel/.* ./     # copying all hidden files (use for creating alias)
vim .bashrc
# go to alias section – add alias
:wq!
source .bashrc
# Finally alias created
```

---

## 8. Absolute vs Relative Path

### Absolute Path
Starts from `/root` (e.g. `/root/sahil/sahil.txt`) — starts from `/`.

When copying/moving a file from any directory **to** the current/home directory:
```bash
cp /root/sahil/sahil.txt ./
mv /root/sahil/sahil.txt ./
```

When copying/moving a file **from** the current/home directory into another directory:
```bash
cp file-name /root/sahil/
mv file-name /root/sahil/
```

### Relative Path
Starts from the current directory (e.g. `sahil/test.txt`); same commands apply.
```bash
cd ../etc/   # relative path (from current dir)
```

### Absolute Path vs Relative Path

**Absolute Path**
1. Starts from the root directory `/`.
2. Gives the complete location of a file/directory.
3. Does not depend on the current working directory.
4. Always points to the same location.
5. Example: `/home/sahil/Documents/file.txt`

**Relative Path**
1. Starts from the current working directory.
2. Gives the location relative to the current directory.
3. Depends on where you are currently located.
4. Usually does not start with `/`.
5. Example: `Documents/file.txt`

> **Remember:** Absolute = complete path, Relative = path from current location.

---

## 9. Linux Users

There are 3 users in a Linux system:

| Root User | Local User | System User |
|---|---|---|
| Also known as 'super user, root user, system administrator' | Also known as normal, regular, common user | Also known as system, server user |
| Denoted by `#` | Denoted by `$` | |
| Home dir: `/root` | Home dir: `/home/<user>` | |
| No change in root user name | Name can be suggested and unique | |
| Created by default when installing | Created by command (`useradd`) | Created by OS during installation |
| UID = 0 | UID = 1000–65536 (65536+ users) | UID = 1–999 |

---

## 10. Linux Directory Structure (19 Directories)

> Reference: [Linux File Hierarchy Structure – GeeksforGeeks](https://www.geeksforgeeks.org/linux-unix/linux-file-hierarchy-structure)

| Directory | Meaning / Use |
|---|---|
| `/` | Root directory – the top level of the Linux file system. |
| `/bin` | Essential binary commands used by all users (like `ls`, `cp`, `cat`). |
| `/boot` | Files needed to boot the system (kernel, bootloader files). GRUB = GRand Unified Bootloader. |
| `/dev` | Device files (hardware devices like disk, USB, printer). |
| `/etc` | System configuration files. |
| `/home` | Personal directories of users. |
| `/lib` | Shared libraries needed by programs in `/bin` and `/sbin`. |
| `/media` | Mount point for removable devices (USB, CD). |
| `/mnt` | Temporary mount point for file systems. |
| `/opt` | Optional software or third-party applications. |
| `/proc` | Virtual directory showing process and system information. |
| `/root` | Home directory of the root user (administrator). |
| `/run` | Runtime system information (temporary system files). |
| `/sbin` | System binary commands used by the administrator. |
| `/srv` | Data for services provided by the system (like web server data). |
| `/sys` | System hardware information and kernel data. |
| `/tmp` | Temporary files created by programs. |
| `/usr` | User programs and utilities (applications installed for users). |
| `/var` | Variable files like logs, cache, mail. |

**Simple way to remember directories**
- User related: `/home`, `/usr`
- System files: `/bin`, `/sbin`, `/lib`
- Configuration: `/etc`
- Boot: `/boot`
- Temporary: `/tmp`
- Logs: `/var`
- Devices: `/dev`

### Difference: `/bin` vs `/sbin`

**/bin**
1. Contains essential user commands.
2. Commands can be used by normal users.
3. Used for common file and system operations.
4. Examples: `ls`, `cp`, `mv`, `cat`.
5. bin = Binary/user commands.

**/sbin**
1. Contains essential system administration commands.
2. Mainly used by root/administrators.
3. Used for system management and configuration.
4. Examples: `fdisk`, `reboot`, `mount`.
5. sbin = System Binary commands.

### Difference: `/mnt` vs `/media`

**/mnt**
1. Used for temporarily mounting filesystems.
2. Usually used for manual mounts.
3. Commonly used by system administrators.
4. Can be used to mount disks, partitions, or network filesystems.
5. Example: mounting a partition at `/mnt/data`.

**/media**
1. Used for removable media.
2. Commonly used for USB drives.
3. Also used for CDs/DVDs and other removable devices.
4. Desktop Linux systems often mount removable devices here automatically.
5. Example: USB mounted at `/media/user/USB`.

---

## 11. User & Group Management

**Why do we create a user?**
We create the user to reduce/decrease conflict/complexity of the system / for separation.

```bash
sudo -i            # switch to root user
su user-name       # switch to local user
# Ctrl+D           # log out from current user
```
System users work in the `sh` shell.

- `useradd` – create a user (a low-level utility for adding users)
- `adduser` – create a user (a more user-friendly script that uses `useradd` in the background)

**How to create a user with bash shell using `useradd`?**

`useradd user-name` creates a user but with the `sh` shell.
(Linux system works on the bash shell, not the sh shell / a user with sh shell does not have a home dir and cannot work with it.)

To create a user with the bash shell using `useradd`:
```bash
useradd -m -s /bin/bash user-name
```
- `-m` = create home directory for the user
- `-s` = specify the default shell

```bash
passwd user-name   # set password
```

`adduser user-name` creates a user with bash shell, and it has a home dir — the user can work in it.

### `adduser` vs `useradd`

| useradd | adduser |
|---|---|
| Low-level Linux command | High-level/perl script |
| Creates a user with basic options | Provides an interactive user-creation process |
| Does not create home directory | Creates home directory |
| Less user-friendly | More user-friendly |
| Commonly available on most Linux systems | Mainly available on Debian/Ubuntu |
| Does not need password | Must assign password |
| Creates user with sh shell | Creates user with bash shell |

```bash
userdel <user-name>       # delete the user
deluser <user-name>       # delete the user
userdel -r <user-name>    # delete user and their home directory
```

### Password Security
Passwords are the 1st line of defence for user accounts. Weak passwords can lead to unauthorized access and compromise system security. Ensure users set complex passwords and follow password policies.

**Key Practices:**
- Use at least 8 characters with a mix of upper/lower case letters, numbers, and special characters.
- Periodically change passwords to minimize exposure risk.
- Avoid sharing passwords.

The `passwd` command is used to change a user's password and manage password-related settings.

```bash
passwd                 # change current user's password
passwd user-name       # set password for the user
passwd -l user-name    # lock the user's account
passwd -u user-name    # unlock the user's account
passwd -e user-name    # expire a user's password to force a reset on next login
```

```bash
tail -n 5 /etc/passwd
tail -n 5 /etc/shadow
tail -n 5 /etc/group
tail -n 5 /etc/gshadow
```
These commands show the last 5 lines of the file.

```bash
cat /etc/passwd    # view all users (7 fields)
cat /etc/shadow    # view all users' shadow info (9 fields)
cat /etc/group     # view all groups (4 fields)
cat /etc/gshadow   # view all group shadow info (4 fields)
```
These are files to check whether a local user has been created or not (whenever a new user is added, these files get an entry for that user).

**`/etc/passwd` — 7 fields:**
1. Username
2. Password
3. UID (User ID)
4. GID (Group ID)
5. User ID info
6. Home directory
7. Login shell

**`/etc/group` — 4 fields:**
```
Group-name : x : GID : members
     |         |    |       |
  Name of   password    group ID   list of
   group   placeholder            group members
```

**`/etc/gshadow` — 4 fields:**
```
Group_name : password : admin_users : members
     |           |            |            |
 Group name  encrypted    group admin   group member
                pass
```

### Group Commands
```bash
groupadd                              # create a new group
groupdel                              # delete the group
usermod -aG group-name user-name      # add user(s)/members to the group
gpasswd -d user-name group-name       # remove the user from group
groupmod -n newgroup oldgroup         # change group name
groupmod -g new-GID group-name        # change GID
gpasswd -A group-name user-name       # add group's admin
gpasswd group-name                    # add password to group

# viewing users and groups
cat /etc/passwd                       # view all users
cat /etc/group                        # view all groups
chgrp group-name file-name            # change the group of the file
groups username                       # view group memberships
groupmems -g group_name -l            # view group details
```

---

## 12. Account Locking & Expiration (chage)

```bash
chage -l username               # check current policy
chage -M 90 username            # set maximum password validity to 90 days
chage -E 2026-10-15 username    # set account expiry date; after this date, user cannot log in (even with correct password)
chage -d 0 username             # force password change at next login
```

### Understanding `/etc/shadow` Fields

| Field | Description |
|---|---|
| Username | Account name |
| Password | Encrypted password |
| Last change | Days since 1970 |
| Min | Min days |
| Max | Max days |
| Warn | Warning |
| Inactive | Inactive days |
| Expire | Expiry date |

### Using `chage`
`chage` stands for "**ch**ange **age**." It manages password aging settings per user.

**View current aging info:**
```bash
sudo chage -l username
```
Output example:
```
Last password change: Jan 01, 2024
Password expires: Apr 01, 2024
Password inactive: May 01, 2024
Account expires: never
Minimum number of days between changes: 0
Maximum number of days between changes: 90
Number of days of warning before expiry: 7
```

### Common `chage` Flags

| Command | What it does |
|---|---|
| `chage -l username` | List all aging info |
| `chage -M 90 username` | Set max password age to 90 days |
| `chage -m 5 username` | Set min days before change to 5 |
| `chage -W 7 username` | Warn 7 days before expiry |
| `chage -I 30 username` | Lock account 30 days after expiry |
| `chage -E 2025-06-01 username` | Set account expiry date |
| `chage -E -1 username` | Remove account expiry |
| `chage username` | Interactive mode (prompts for each value) |

**Quick Example:**
```bash
# Set a full policy for user spiderman
sudo chage -M 90 -m 5 -W 7 -I 30 spiderman

# Force spiderman to change password on next login
sudo chage -d 0 spiderman
```

---

## 13. sudo & su

The `sudo` command allows a permitted user to execute a command as the superuser or another user, as specified by the security policy.
It is commonly used to perform administrative tasks that require elevated privileges. It provides limited and controlled privilege escalation.

**Why use sudo?**
- Prevent accidental system damage by restricting root access.
- Provides an audit trail of user activities.
- Offers flexibility for assigning specific command permissions.

```bash
sudo -i          # switch to root user
su user-name     # switch to local user
```

**How to create a sudo user:**
- Log in as root user (root user has access to all 19 directories)
- Make changes in the `/etc/sudoers` file of the root user
- `vim /etc/sudoers`
- Add an entry for the local user under admin:
```
username ALL=(ALL) ALL
```

We can switch from the root user to a local user (`su user-name`), but we **cannot** switch from any local user to the root user unless it has `sudoers` permission (`vim /etc/sudoers`). We can switch local user to local user (`su user-name`).

`su` = **s**witch **u**ser. The `su` command is used to switch to another user account in a Linux system. By default, it switches to the root user if no username is provided. It prompts for the target user's password.

### Difference between Regular User and Sudo User

**Regular User:**
- Has limited permissions and can only perform actions allowed by the system administrator.
- Cannot execute commands that require elevated privileges.

**Sudo User:**
- Has the ability to execute commands with superuser privileges using the `sudo` command.
- Can perform administrative tasks as permitted by the system administrator.

Example: `sudo` → execute command with superuser privileges.

---

## 14. File Permissions & umask

### umask
`umask` = user file creation mode mask.

```
umask: root user  = 022
       local user = 002
```
`umask` is used for checking a file's default permission.

```
file full permission = 666
directory full permission = 777
```

**Permission numbers:**
- read (r) = 4
- write (w) = 2
- execute (x) = 1

### File Permissions

- **read (r) (4):** Read permission allows a user to open and read the contents of a file. For a directory, read permission allows a user to list the contents of the directory.
- **write (w) (2):** Write permission allows a user to modify or delete the contents of a file. For a directory, write permission allows a user to add, delete, or rename files within the directory.
- **execute (x) (1):** Execute permission allows a user to run a file as a program or script. For a directory, execute permission allows a user to access files and subdirectories within the directory.

Execute (x) permission is very important to enter into a directory / write anything in it.

**File:** A file only has `rw-` (read write) permission by default; it does not have execute permission, because if a file had execution permission by default, it would be risky since any file could execute without proper control.
- Local user default permission = 664
- Root user default permission = 644

```
-    rw-   rw-    rw-
1     2      3      4
```
Where: 1 = file type (`-` = simple file), 2 = owner/user permission, 3 = group permission, 4 = other's permission.

**Directory:** A directory has read, write, and execute permission (rwx). Any directory just needs write and execute permission to edit content.
- Local user default permission = 775
- Root user default permission = 755

```
d   rwx    rwx    rwx
1     2      3      4
```
Where: 1 = file type (`d` = directory), 2 = owner/user permission, 3 = group permission, 4 = other's permission.

### Reading an `ls -l` output

```
-     rw-     r--       r--     1    root    root     0    Apr  2 18:38      sahil.txt
|       |       |          |         |         |          |        |               |                |
1       2       3          4         5         6          7        8               9               10
```

1. File type (`-` = regular file, `d` = directory, `l` = symbolic link)
2. Owner Permissions
3. Group Permissions
4. Other User Permission
5. Link Count
6. Owner of file/directory
7. Group Owner of File or Directory
8. File Size
9. Creation Date and Time
10. File/Directory Name

### File Types Displayed by `ls -l`
- Regular File (`-`): Normal files containing data or text.
- Directory (`d`): Container for other files or directories.
- Symbolic Link (`l`): Shortcut pointing to another file.
- Socket (`s`): Enables inter-process communication.
- Pipe (`p`): Allows data flow between processes.
- Block Device (`b`): Represents a block hardware device (e.g., hard drives).
- Character Device (`c`): Represents a character hardware device (e.g., keyboard).

### System Defined File Types
System-defined file types are pre-configured by Linux to manage system functionality:
- Configuration Files: Located in `/etc` (e.g., `/etc/passwd`).
- Libraries: Shared code used by applications (e.g., `/lib`).
- Logs: System and application logs (e.g., `/var/log`).

1. Regular files
2. Directories
3. Symbolic links
4. Device files (block and character)
5. Pipes and sockets

### User Defined File Types
User-defined file types are created by users for specific purposes, such as:
- Text Files: Configuration, log, or documentation files.
- Scripts: Automating tasks (e.g., shell scripts).
- Executables: Compiled programs or binaries.

1. Custom file extensions (e.g., `.txt`, `.jpg`, `.exe`)
2. Configuration files (e.g., `.conf`, `.ini`)

### `chmod`
```bash
chmod ugo+/-/=rwx file-name   # change the file permission
chmod 000 file-name           # advanced level / file has no permission
chmod 777 dir-name            # dir has all permission (u/g/o = read/write/execute)
chmod 666 file-name           # file has u/g/o = read/write permission
```

Where:
```
r = read = 4
w = write = 2
x = execute = 1

u = user
g = group
o = other

+ = add
- = remove
= = at least this level
```

---

## 15. Link Count & Inodes

### Link Count
Link count indicates the number of hard links associated with a file or directory.
In Linux, link count tells how many names (links) point/are connected to the same file or directory.

Link count = number of directory entries that refer to the same inode (file).

- Link count of a File = 1
- Link count of a Directory = 2

**Link Count for Directories**
1. **Base Count:** A directory always starts with at least two links: `.` (itself) and `..` (parent).
2. **Subdirectories:** Each subdirectory increases the parent directory's link count by 1.

### What is an Inode in Linux?
inode = Index Node.

It is a data structure used by the Linux file system to store information about a file.
An inode is like an ID card of a file that stores all its details except the filename.

An inode stores metadata (info about the file) such as: file type, file size, file permission, file owner, group, link count, timestamps, disk block location, etc.

Linux does not find/access data of a file by its name — it finds file data by index node.

```
Dir entry -> sahil.txt -> inode (ex. 12345) -> data blocks (actual content)
```

An inode is a data structure in Linux that stores metadata about a file and points to the location of the file data on disk.

```bash
ls -i    # find the inode number of a file
ls -li   # detailed view
df -i    # shows total inode info of disk
```

### What is an Inode Number?
An inode number is a unique number assigned to every file and directory in a Linux filesystem.

inode number = unique ID of a file. Linux actually identifies files using the inode number, not the filename.

An inode number is a unique identifier assigned to every file and directory in a Linux filesystem that stores metadata and points to the file's data blocks.

---

## 16. Hard Link vs Soft Link

**Hardlink** – A hard link is an additional name for an existing file on the filesystem.
- Points directly to the same inode of a file.
- Cannot span across different file systems.
- If the original file is deleted, the hard link still retains access to the data.
- Cannot link to a directory.
- Command: `ln file-name.txt hardlink`

- Hard links share the same inode.
- Two files with the same inode = hard link.
- Two files with different inodes = separate files.

**Soft Link (Symbolic Link):**
- Acts as a pointer to the original file.
- Can span across different file systems.
- If the original file is deleted, the soft link becomes a broken link and no longer points to valid data.
- Can link to a directory.
- Command: `ln -s file_name softlink`

---

## 17. Archiving & Compression

Archiving is the process of combining/compiling multiple files into 1 single file.
This is especially useful for backups, data transfer, and organization.

**Common use cases:**
1. **Backups:** safeguard data by creating archives that can be stored securely.
2. **Data transfer:** simplify sharing by bundling multiple files into a single archive.
3. **Organization:** group related files for better management.

### Commands
```bash
tar -cvf archive-name ./(path)   # archive files from current/home dir into archive-name
tar -xvf archive-name ./(path)   # unarchive (extract) files from archive-name into current/home dir
tar -tvf archive-name ./(path)   # show content of an archive file
```

Where:
- `c`: Create an archive.
- `v`: Verbose output (show progress).
- `f`: Specify the file name.

**Extract a Compressed tar Archive:**
```bash
tar -xzvf backup.tar.gz
tar -xjvf backup.tar.bz2
tar -xJvf backup.tar.xz
```
Where `-x` = extract an archive.

### Compression
Compression is used to reduce the file size. It reduces file sizes by encoding data efficiently, helping save storage and speed up data transfer.

**Compression and Decompression** — 3 utilities:
- `gzip` = good compression and widely used (reliable)
- `bzip2` = better compression than gzip but slower
- `xz` = best compression but slowest (efficient)

```bash
gzip file-name          # compress the file (file-name.gz)
gunzip file-name.gz     # decompress the file

bzip2 file-name         # compress the file (file-name.bz2)
bunzip2 file-name.bz2   # decompress the file

xz file-name            # compress the file (file-name.xz)
unxz file-name.xz       # decompress the file
```

### Combining Archiving + Compression Together
```bash
tar -czvf backup.tar.gz ./(path)   # archive and compress at the same time
tar -cjvf backup.tar.bz2 ./(path)  # same, with bzip2
tar -cJvf backup.tar.xz ./(path)   # same, with xz
```

---

## 18. Crontab

Crontab allows scheduling of recurring tasks such as backups, system updates, and cleanup scripts.

### Cron Job Fields
```
 *          *          *            *            *
Minute   Hour     Day of month   Month     Day of week
(0-59)   (0-23)   (1-31)         (1-12)    (0-7, where 0/7 = Sunday)
```

```bash
sudo apt update -y          # update the server (-y = yes)
sudo apt install cron       # install crontab
service cron start          # start cron service
```

```bash
crontab -e         # edit the crontab file for the current user
crontab -l         # list the current user's crontab entries
crontab -r         # delete the crontab
sudo crontab -e    # edit the crontab file for the root user
sudo crontab -l    # list the root user's crontab entries
```

Example cron job to run a script every day at 2am:
```
* * * * * command (mkdir/touch/tar etc.)
```

**To change the editor used by crontab**, make changes in the `.bashrc` file:
```bash
vim ~/.bashrc
# Set default editor
export EDITOR=vim
export VISUAL=vim
source ~/.bashrc
```
Then the crontab editor will open in vim.

---

## 19. Search & Filter Utilities

Linux provides powerful utilities to search and filter data efficiently, streamlining tasks like file management, data parsing, and text processing.

**Importance of searching and filtering data in Linux:**
- Save time by automating data retrieval and organization.
- Essential for managing large datasets and directory structures.
- Integral to scripting and system administration.

### grep
`grep` = **g**lobal **r**egular **e**xpression **p**rint. Used to search for a specific pattern in files or input streams.

```bash
grep -r 'error' /var/log   # find all lines containing 'error' in the log dir
```
It should be used with the `sort` command.

**Common options:**
- `-i` = case-insensitive search
- `-v` = invert match, show lines that do NOT match the pattern
- `-n` = show line numbers with matches
- `-r` = recursively search directories

### cat — Concatenate and Display Files
Used to read file content and display it in the terminal.
```bash
cat example.txt
```

### sort — Sort Lines in Files
Used to sort lines in text files or input streams.

**Common options:**
- `-r` = reverse the sort order
- `-n` = sort numerically
- `-k` = specify a key for sorting

```bash
sort file-name | grep specific-name   # finds only specific name/data from that file
cat file.txt | sort -n                # sort file numerically
```

### uniq — Filter Unique Lines
`uniq` shows only unique words (removes duplicate words). It should be used with the `sort` command.

**Common options:**
- `-c` = count occurrences of each line
- `-d` = show only duplicate lines

```bash
sort file-name | uniq   # removes duplicate words and shows only unique names
```

### find
`find` = find files (from anywhere/everywhere). It's a robust tool for locating files and directories based on various criteria.

**Common Options:**
- `-name`: Search by file name (case-sensitive)
- `-iname`: Search by file name (case-insensitive)
- `-type`: Specify file type (`f` for files, `d` for directories)
- `-size`: Search by file size (e.g., `+100k` for files larger than 100KB)
- `-mtime`: Search by modification time (e.g., `-1` for files modified in the last day)

```bash
find /root -name "*sahil.txt"        # find file sahil.txt

# Find all .txt files in the current directory:
find -name "*.txt"

# Find files larger than 1MB:
find /home -size +1M

# Find files modified in the last 7 days:
find /var/log -mtime -7

find / -name "*xyz.txt"      # find the file wherever it is present, e.g. /mnt/.../sahil/xyz.txt
find /mnt -name "*.txt"      # find the file within /mnt
```

---

## 20. Linux Process Management

**Introduction to Processes:** A process is a running instance of a program.
Every command executed in Linux becomes a process.

### Process Priority and Nice Values
Process priority determines the importance of a process relative to others in the system.
In Linux, the **nice value** is used to influence process scheduling by assigning a priority level.

**Key Points:**
- Nice value range: -20 (highest priority) to 19 (lowest priority)
- Default value: 0
- Negative nice values require root privileges

**Command to check priority:** Use `top` or `htop` to view running processes and their priorities.

**Changing nice values:**
- Use `nice` to start a process with a specific nice value.
- Use `renice` to change the nice value of an existing process.

```bash
nice -n 10 sleep 1000     # starts a sleep process with a nice value of 10
renice -5 -p <PID>        # adjusts the nice value of the process with the given PID to -5
```

### Finding Process IDs
Each running process in Linux is assigned a unique Process ID (PID).

```bash
ps -e                          # list all processes
pgrep <process_name>           # find specific process
ps -aux | grep <process_name>  # detailed information
```

### Sending Signals to Processes
Linux allows sending signals to control or terminate processes.

**Common Signals:**
- `SIGTERM (15)`: Graceful termination
- `SIGKILL (9)`: Forceful termination
- `SIGHUP (1)`: Reload configuration

```bash
kill -9 1234    # forcefully terminates process with PID 1234
kill 1234       # gracefully kills process 1234
```

### Killing Processes (Signals)

| Command | Signal | Meaning |
|---|---|---|
| `kill <pid>` | SIGTERM (15) | Gracefully terminate process |
| `kill -9 <pid>` | SIGKILL | Force kill immediately |
| `killall <processname>` | – | Kill all processes by name |
| `kill -1 <pid>` | SIGHUP | Reload process |
| `kill -2 <pid>` | SIGINT | Keyboard interrupt (Ctrl+C) |
| `kill -15 <pid>` | SIGTERM | Graceful termination |

**Monitor changes:** `top` — observe the updated priority in the PR and NI columns.

### Overview of Process States
- **R:** Running or runnable
- **S:** Sleeping (waiting for an event)
- **D:** Uninterruptible sleep (waiting for I/O)
- **Z:** Zombie (terminated but not cleaned up)
- **T:** Stopped or traced
- **Daemon process:** `systemd` / `nginx` = the 1st process run when the system started

### Job Types and States
Jobs represent processes managed by the shell. A job shows a process along with its state.

```bash
jobs              # list jobs
fg <job_id>       # foreground job
bg <job_id>       # background job
kill -TSTP <PID>  # stop job
```

```bash
top      # shows all processes of the system (real-time CPU, memory, running processes)
ps       # shows process IDs
jobs     # shows process states
pstree   # shows processes in tree-like structure
pstree -p  # same, with PIDs
```

---

## 21. Linux Networking Fundamentals

A network is a collection of computers, servers, or other devices connected together to share data, resources, and services.

Connected via wired (cables) or wireless (Wi-Fi) links, these systems use standard protocols to communicate, enabling activities like internet browsing, file sharing, and printing.

Networking enables communication between systems over a network using IP addresses, ports, and protocols.

Each system has:
- IP Address
- Subnet Mask
- Gateway → Router
- DNS Server → Domain Name Resolution

### Types of Networks

**LAN (Local Area Network)**
Computers connected to each other from a local area (e.g. 1 room) via cables or Wi-Fi.

**MAN (Metropolitan Area Network)**
The connection of devices within a city.
Ex. city-wide cable TV network, or a university campus with multiple interconnected buildings. Branches within a city connected together.

**WAN (Wide Area Network)**
Continents around the world connected together via fibre optical cable.
WAN = Global network.

### IP Addressing
IPv4 = 32 bits.

IPv4 addresses are divided into 5 classes: A, B, C, D & E.

**Public IP address ranges:**

| Class | Range | Format |
|---|---|---|
| A | 1–126 | N.H.H.H |
| B | 128–191 | N.N.H.H |
| C | 192–223 | N.N.N.H |
| D | 224–239 | Military research |
| E | 240–255 | Experimental (Govt access) |

8 bits = `1 1 1 1 1 1 1 1` → octet form.

- `0` = reserved
- `127` = loopback (localhost / used to check self server)

### Protocols

| Protocol | Purpose |
|---|---|
| TCP | Reliable communication |
| UDP | Fast but unreliable |
| HTTP/HTTPS | Web communication |
| FTP | File transfer |
| SSH | Secure remote access |
| ICMP | Network diagnostics |

**Common Ports:**
- HTTP – 80
- HTTPS – 443
- FTP – 21
- SSH – 22

### Topologies
There are 7 topologies:
1. **Point to point** – 2 devices communicate/connect with each other, sending and receiving data.
2. **Bus** – all devices are connected on a single cable.
3. **Star** – all devices are connected to a central computer.
4. **Ring** – all devices are connected to each other in a circular manner.
5. **Mesh** – all devices are connected to each other.
6. **Tree** – devices are connected to 1 central unit and other devices are also connected to those devices (parent-child connection).
7. **Hybrid** – combination of any 2 topologies (e.g. tree-star, star-ring).

### Networking Commands
```bash
curl                # fetching server / downloading a package
wget                # download files only
ifconfig            # find private IP
curl ifconfig.me    # find public IP
ping                # check internet connection of current server with others
nslookup google.com # find IP address and DNS and vice versa
dig google.com       # find IPv4 address
```
- `nslookup` is a program to query internet domain name servers.
- `dig` is a flexible tool for interrogating DNS name servers.
- `8.8.8.8` is a free, public recursive DNS (Domain Name System) server provided by Google.

---

## 22. Extra / Miscellaneous Commands

| # | Command | Description |
|---|---|---|
| 52 | `wc` | word count (can count words from multiple files – `wc sahil.txt sahil1.txt sahil2.txt`) |
| 53 | `free` | shows free space of system |
| 54 | `free -h` | shows free space in human-readable form |
| 55 | `uname` | shows which platform we are working on (Ubuntu, CentOS, Kali Linux = Linux) |
| 56 | `uptime` | tells how long the system has been running |
| 57 | `who` | tells which user is logged in and since when |
| 58 | `which file_name` | shows where a file/command is stored, its version, and from where it's executing |
| — | — | (if there's an error from any file of the system, `which` helps find that file, its version, its location, and from where it's executing) |
| 60 | `id` | shows ID of users/groups |
| 61–62 | `apt` | Advanced Package Tool for Linux — a CLI package manager used to install, update, remove, and manage software packages on Debian-based distributions like Ubuntu and Linux Mint |
| 63 | `yum` | package manager for CentOS |
| 64 | `dnf` | package manager for Fedora |
| 65 | `pacman` | package manager for Arch Linux |
| 66 | `portage` | package manager for ChromeOS, Gentoo |
| 67 | `rpm` | package manager for RedHat |
| 68 | `sudo apt install docker.io` | install docker.io (if the file/libraries are already present in the system) |
| 69 | `sudo apt-get install docker.io` | install docker.io from the internet (`-get` = internet) |
| 70 | `sudo apt-get update` | update package lists (system is not up to date) |
| 71 | `cut -b 1-5 cloud.txt` | cut a small part of a file (e.g. bytes 1–5) |
| 72 | `tee` | prints to terminal AND writes to a file at the same time |

**Example of `tee`:**
```bash
echo "sahil bhakare" | tee sahil.txt
```
Prints "sahil bhakare" on the terminal, and also creates `sahil.txt` with the same content.

### Disk Usage

| # | Command | Description |
|---|---|---|
| 73 | `df` | shows disk usage |
| 74 | `df -h` | shows disk usage in human-readable form |
| 75 | `ps` | displays information about a selection of active processes |
| 76 | `free` | shows free space of the system/disk |
| 77 | `free -h` | shows free space in human-readable form |
| 78 | `nohup command-name` | stores/saves output of a command (used to store daily logs) |
| 79 | `vmstat` | shows virtual memory statistics from RAM |
| 80 | `vmstat -a` | shows virtual memory stats in detail (active, inactive, etc.) |
| 81 | — | Coordinated Universal Time (UTC) is the primary time standard by which the world regulates clocks and time, acting as the modern successor to Greenwich Mean Time (GMT). |
| 82 | `shutdown` | shuts down the system |
| 83 | `reboot` | restarts the system |

> **To-do (from original notes):** write out all differences like hard link vs. soft link, `top` vs. `ps`, `useradd` vs. `adduser`, TCP vs. UDP, etc. Most of these differences have been added throughout this document above.

---

## 23. Advanced Permissions: umask, Sticky Bit, ACL

### 1. What is umask?
`umask` defines the default permission restrictions for newly created files and directories.
- Default base permission for files: 666
- Default base permission for directories: 777
- Example: `umask 022`
  - File → 644
  - Directory → 755

### 2. What is Sticky Bit?
Sticky bit is a special permission that allows only the file owner, directory owner, or root to delete or rename files inside a directory.
- Commonly used on `/tmp`.
- Permission symbol: `t`
- Command: `chmod +t directory`

### 3. What is ACL?
ACL (Access Control List) provides additional permissions for specific users or groups beyond the standard owner/group/others permissions.

### 4. Set ACL
`setfacl` is used to set or modify ACL permissions.
```bash
setfacl -m u:user1:rwx file.txt
```

### 5. Get ACL
`getfacl` is used to view the ACL permissions of a file or directory.
```bash
getfacl file.txt
```

> **Remember:** `setfacl` → Set/modify ACL, `getfacl` → Get/view ACL

---

## 24. Network Monitoring Tools

### 1. iptables
`iptables` is a Linux firewall utility used to control incoming, outgoing, and forwarded network traffic using rules.
- Used to allow or block traffic.
- Works with IP addresses, ports, and protocols.
- Commonly used for firewall configuration.
- Example: `iptables -L` → Lists firewall rules.

### 2. netstat
`netstat` is a command used to display network connections, listening ports, routing information, and network statistics.
- `netstat -tuln` → Shows listening TCP/UDP ports.
- `netstat -an` → Shows all connections.
- Useful for network troubleshooting.
- Note: `netstat` is considered deprecated on many modern Linux systems; `ss` is preferred.

### 3. ss -tulpn
`ss -tulpn` is used to display TCP/UDP sockets that are listening, along with their port numbers and associated process information.

**Meaning of options:**
- `-t` → TCP
- `-u` → UDP
- `-l` → Listening
- `-p` → Process information
- `-n` → Show numerical IP addresses and port numbers

> I use `ss -tulpn` to check which TCP/UDP ports are listening on a Linux server and which process is using those ports.

---

## 25. 🚀 Interview Prep / Advanced Topics (Added)

> This section is **added** content (not from the original notes) to help round out Linux/Cloud/DevOps interview preparation. Marked separately so my original notes stay untouched above.

### Frequently Asked Conceptual Differences

**`top` vs `ps`**
| top | ps |
|---|---|
| Real-time, continuously updating view of processes | Static, one-time snapshot of processes |
| Interactive (can kill/renice from within) | Not interactive |
| Shows CPU/memory usage live | Shows a fixed list at the time of running |

**TCP vs UDP**
| TCP | UDP |
|---|---|
| Connection-oriented | Connectionless |
| Reliable (acknowledgements, retransmission) | Unreliable (no guarantee of delivery) |
| Slower due to overhead | Faster, lower overhead |
| Used for web, email, file transfer (HTTP, FTP, SSH) | Used for streaming, DNS, VoIP, gaming |

**Process vs Thread**
| Process | Thread |
|---|---|
| Independent execution unit with its own memory space | Lightweight unit of execution within a process |
| Has its own PID | Shares memory with other threads in the same process |
| Communication is slower (IPC) | Communication is faster (shared memory) |

**Hard Link vs Soft Link (recap)**
| Hard Link | Soft Link |
|---|---|
| Points to same inode | Points to file path |
| Cannot link directories | Can link directories |
| Survives deletion of original | Becomes broken/dangling if original is deleted |
| Same filesystem only | Can cross filesystems |

### Systemd & Service Management (commonly asked)
Modern Linux distros use `systemd` as the init system (PID 1) instead of older SysV init scripts.

```bash
systemctl status <service>     # check status of a service
systemctl start <service>      # start a service
systemctl stop <service>       # stop a service
systemctl restart <service>    # restart a service
systemctl enable <service>     # enable service to start at boot
systemctl disable <service>    # disable service from starting at boot
systemctl daemon-reload        # reload systemd config after editing unit files
journalctl -u <service>        # view logs for a specific service
journalctl -xe                 # view recent system logs with explanations
```

### Disk & Partition Management
```bash
lsblk                # list block devices (disks/partitions)
fdisk -l             # list partitions (legacy tool)
parted -l            # list partitions (modern tool, supports GPT)
mount /dev/sdX /mnt  # mount a partition
umount /mnt          # unmount a partition
mkfs.ext4 /dev/sdX   # format a partition with ext4 filesystem
blkid                # show UUID and filesystem type of devices
```

### Environment Variables
```bash
env                    # list all environment variables
echo $PATH              # print value of PATH variable
export VAR=value        # set an environment variable for current session
unset VAR                # remove an environment variable
```
`/etc/environment`, `~/.bashrc`, and `~/.profile` are common places to set persistent environment variables.

### Log Files Worth Knowing
| Log File | Purpose |
|---|---|
| `/var/log/syslog` or `/var/log/messages` | General system logs |
| `/var/log/auth.log` or `/var/log/secure` | Authentication/login logs |
| `/var/log/dmesg` | Kernel ring buffer / boot messages |
| `/var/log/cron` | Cron job logs |

### SSH Basics (very common in DevOps interviews)
```bash
ssh user@hostname                       # connect to a remote server
ssh -i keyfile.pem user@hostname        # connect using a private key
ssh-keygen -t rsa -b 4096               # generate an SSH key pair
ssh-copy-id user@hostname               # copy public key to remote server for passwordless login
scp file.txt user@host:/path/           # securely copy a file to a remote server
rsync -avz source/ user@host:/dest/     # sync files/directories efficiently
```

### Load Average & Performance Basics
- `uptime` and `top` show **load average** (1, 5, 15 min averages) — represents the number of processes waiting for CPU time.
- A load average close to or above the number of CPU cores generally indicates the system is under heavy load.
- `iostat`, `vmstat`, `mpstat` (from the `sysstat` package) give deeper CPU/disk/memory performance insights.

### Common DevOps/Cloud Interview Questions to Prepare
- Explain the Linux boot process (BIOS/UEFI → Bootloader (GRUB) → Kernel → init/systemd → login).
- How would you troubleshoot a server with high CPU/memory usage?
- Difference between a container and a virtual machine.
- How do you check open ports and which process is using them? (`ss -tulpn`, `lsof -i`)
- How do you check disk space and find which directory is consuming the most space? (`df -h`, `du -sh *`)
- What is a zombie process and how do you handle it?
- How do you schedule a recurring job in Linux? (`cron`)
- How would you secure an SSH server? (disable root login, key-based auth, change default port, fail2ban)
- Explain file permission numbers (e.g., what does `chmod 755` mean?).
- What's the difference between a soft and hard restart of a service?

---
