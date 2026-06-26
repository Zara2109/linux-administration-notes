# Linux Permissions

Linux permissions control who can read, modify, or execute files and directories. They are one of the most important parts of Linux security and system administration.

## 1. Permission Basics

Every file and directory has three permission groups:

| Group | Meaning |
| --- | --- |
| User | The owner of the file |
| Group | Users who belong to the file's group |
| Others | Everyone else on the system |

Each group can have three permission types:

| Permission | Symbol | File Meaning | Directory Meaning |
| --- | --- | --- | --- |
| Read | `r` | View file contents | List directory contents |
| Write | `w` | Modify file contents | Create, delete, or rename files inside |
| Execute | `x` | Run the file as a program/script | Enter or access the directory |

## 2. Viewing Permissions

Use `ls -l` to view permissions:

```bash
ls -l
```

Example output:

```bash
-rw-r--r-- 1 alice developers 1200 Jun 27  notes.txt
drwxr-xr-x 2 alice developers 4096 Jun 27  scripts
```

Permission breakdown:

```text
-rw-r--r--
```

| Part | Meaning |
| --- | --- |
| `-` | File type. `-` means regular file, `d` means directory |
| `rw-` | User permissions |
| `r--` | Group permissions |
| `r--` | Others permissions |

So `-rw-r--r--` means:

- Owner can read and write.
- Group can only read.
- Others can only read.

## 3. File Types

The first character in `ls -l` output shows the file type:

| Symbol | Type |
| --- | --- |
| `-` | Regular file |
| `d` | Directory |
| `l` | Symbolic link |
| `c` | Character device |
| `b` | Block device |
| `s` | Socket |
| `p` | Named pipe |

## 4. Numeric Permissions

Permissions can also be written as numbers:

| Permission | Value |
| --- | --- |
| Read | `4` |
| Write | `2` |
| Execute | `1` |

Add the values together:

| Number | Meaning |
| --- | --- |
| `7` | Read, write, execute |
| `6` | Read, write |
| `5` | Read, execute |
| `4` | Read only |
| `3` | Write, execute |
| `2` | Write only |
| `1` | Execute only |
| `0` | No permissions |

Common examples:

| Mode | Symbolic Form | Meaning |
| --- | --- | --- |
| `777` | `rwxrwxrwx` | Everyone has full access |
| `755` | `rwxr-xr-x` | Owner full access, others can read and execute |
| `700` | `rwx------` | Only owner has full access |
| `644` | `rw-r--r--` | Owner can edit, others can read |
| `600` | `rw-------` | Only owner can read and write |

## 5. Changing Permissions with `chmod`

The `chmod` command changes file or directory permissions.

Numeric method:

```bash
chmod 644 file.txt
chmod 755 script.sh
chmod 700 private-folder
```

Symbolic method:

```bash
chmod u+x script.sh
chmod g+w shared-file.txt
chmod o-r secret.txt
chmod a+r public.txt
```

Symbol meanings:

| Symbol | Meaning |
| --- | --- |
| `u` | User/owner |
| `g` | Group |
| `o` | Others |
| `a` | All users |
| `+` | Add permission |
| `-` | Remove permission |
| `=` | Set exact permission |

Examples:

```bash
chmod u+x backup.sh
chmod go-rw private.txt
chmod a=r public-readonly.txt
```

## 6. Changing Ownership with `chown`

The `chown` command changes the owner of a file or directory.

```bash
sudo chown user file.txt
```

Change both owner and group:

```bash
sudo chown user:group file.txt
```

Example:

```bash
sudo chown alice:developers app.log
```

Change ownership recursively:

```bash
sudo chown -R alice:developers /var/www/html
```

Use recursive ownership changes carefully because they affect everything inside the directory.

## 7. Changing Group with `chgrp`

The `chgrp` command changes only the group owner:

```bash
sudo chgrp developers project.txt
```

Recursive example:

```bash
sudo chgrp -R developers /srv/project
```

## 8. Directory Permissions

Directory permissions behave differently from file permissions.

| Permission | Directory Effect |
| --- | --- |
| Read | Allows listing files with `ls` |
| Write | Allows creating, deleting, and renaming files |
| Execute | Allows entering the directory with `cd` and accessing files inside |

Important example:

```bash
chmod 600 mydir
```

This is usually a mistake for directories because without execute permission, users cannot enter the directory.

Common directory permissions:

```bash
chmod 755 /path/to/directory
chmod 700 /path/to/private-directory
```

## 9. Default Permissions and `umask`

The `umask` value controls default permissions for new files and directories.

Check current `umask`:

```bash
umask
```

Common value:

```bash
0022
```

With `umask 022`, default permissions are usually:

| Type | Default Permission |
| --- | --- |
| File | `644` |
| Directory | `755` |

Set a temporary `umask`:

```bash
umask 027
```

This makes new files and directories more private.

## 10. Special Permissions

Linux has three special permission bits:

| Permission | Symbol | Meaning |
| --- | --- | --- |
| Setuid | `s` on user execute bit | File runs as the file owner |
| Setgid | `s` on group execute bit | File runs as group, or directory inherits group ownership |
| Sticky bit | `t` on others execute bit | Only file owner, directory owner, or root can delete files |

### Setuid

Example:

```bash
ls -l /usr/bin/passwd
```

You may see:

```bash
-rwsr-xr-x
```

The `s` means setuid is enabled.

### Setgid

Setgid on a directory is useful for shared team folders:

```bash
chmod g+s /srv/shared
```

New files created inside inherit the directory's group.

### Sticky Bit

The sticky bit is commonly used on `/tmp`:

```bash
ls -ld /tmp
```

Example:

```bash
drwxrwxrwt
```

The `t` means users can create files there, but they cannot delete files owned by other users.

Set sticky bit:

```bash
chmod +t /shared/tmp
```

## 11. Access Control Lists

Standard Linux permissions are sometimes not flexible enough. Access Control Lists, or ACLs, allow more specific permissions.

View ACLs:

```bash
getfacl file.txt
```

Give a user read and write access:

```bash
setfacl -m u:bob:rw file.txt
```

Give a group read access:

```bash
setfacl -m g:developers:r file.txt
```

Remove ACL entry:

```bash
setfacl -x u:bob file.txt
```

Remove all ACLs:

```bash
setfacl -b file.txt
```

## 12. Common Permission Problems

### Permission denied when running a script

Problem:

```bash
./script.sh
bash: ./script.sh: Permission denied
```

Fix:

```bash
chmod +x script.sh
./script.sh
```

You can also run it directly with Bash:

```bash
bash script.sh
```

### Cannot enter a directory

Problem:

```bash
cd project
bash: cd: project: Permission denied
```

Fix:

```bash
chmod u+x project
```

### Cannot edit a file

Check ownership and permissions:

```bash
ls -l file.txt
```

If you own the file:

```bash
chmod u+w file.txt
```

If the wrong user owns the file:

```bash
sudo chown youruser file.txt
```

## 13. Security Best Practices

- Avoid using `chmod 777` unless it is temporary and absolutely necessary.
- Use the least permission required.
- Use `600` for private files such as SSH keys.
- Use `700` for private directories.
- Use `755` for normal executable directories.
- Use `644` for normal readable files.
- Use groups for team access instead of giving access to everyone.
- Be careful with recursive commands like `chmod -R` and `chown -R`.

## 14. Quick Reference

View permissions:

```bash
ls -l
```

Change permissions:

```bash
chmod 755 file
```

Change owner:

```bash
sudo chown user file
```

Change owner and group:

```bash
sudo chown user:group file
```

Change group:

```bash
sudo chgrp group file
```

View default permission mask:

```bash
umask
```

View ACLs:

```bash
getfacl file
```

Set ACL:

```bash
setfacl -m u:user:rw file
```

## 15. Practice Commands

Create a test file and directory:

```bash
touch testfile
mkdir testdir
```

Try different permissions:

```bash
chmod 644 testfile
chmod 600 testfile
chmod 755 testdir
chmod 700 testdir
```

Check results:

```bash
ls -l
ls -ld testdir
```

Clean up:

```bash
rm testfile
rmdir testdir
```

