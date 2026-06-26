# Users and Groups in Linux 
## What is a User?
A user is an account that can log in to a Linux system and perform actions based on assigned permissions.
Each user has :
- A username
- A unique User Id (UID)
- A home directory
- A default shell

Example:
```bash
whoami
id
```

---
# What is a Group?

A group is a collection of users.
Groups make permissions management easier by allowing administrators to assign permissions to multiple users at once.
Each group has:
- A unique group name 
- A unique group Id (GID)

Example:

``bash
groups
id
```

---
## Types of Users
### Root User 
The root user is the superuser in Linux.
Charcteristics:
- UID = 0
- Has unrestricted access to the system
- Can modify any file or configuration

Example:
```bash
sudo su-
whoami
```

---

## Regular User
A regular user is created for daily tasks and has limited privileges.

Example:
```bash
useradd zahrahh
passwd zahrah
```

---

### System User
System users are used by services and applications.

Example:
- ngnix
- sshd
- mysql

These accounts cannot log in interactively.

---

## Important Files
## /etc/passwd
Stores user accounts information.
View:
```bash
cat /etc/passwd
```

Example entry:
```text
zahrah:x:1001:1001:Zahrah:/home/zahrah:/bin/bash
```

Fields:
1. Username
2. Password placeholder
3. UID
4. GID
5. Comment field
6. Home directory
7. Login Shell

---

### /etc/group
Stores group information.

View:
```bash
cat /etc/group
```

Example entry:

```text
developers:x:1002:user1,user2
```

---

## Useful Commands
Display current user:
```bash
whoami
```

Display UID and GID:
```bash
id
```

Display user groups:
```bash
groups
```

Display logged-in users:
```bash
who
```

Display login history:

```bash
last
```

---

## Why Users and Groups Matter

Users and groups provide:

- Security

- Access control

- Accountability

- Resource management

They help ensure that users can only access the files and resources they are authorized to use
