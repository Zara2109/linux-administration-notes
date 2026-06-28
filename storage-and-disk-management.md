# Storage and Disk Management in Linux

## Introduction

Storage and disk management involves monitoring, organizing, and maintaining storage devices and file systems on a Linux system.

System administrators use these tools to:
- Check disk usage
- Manage partitions
- Mount file systems
- Monitor available space
- Troubleshoot storage issues

---

## Viewing Disk Usage

### df

Displays available and used disk space.

```bash
df -h
```

Options:
- `-h` : Human-readable format

Example Output:

```text
Filesystem      Size  Used Avail Use%
/dev/sda1        50G   20G   28G  42%
```

---

## Checking Directory Size

### du

Displays disk usage of files and directories.

```bash
du -sh /home
```

Options:
- `-s` : Summary
- `-h` : Human-readable

View size of all directories:

```bash
du -h --max-depth=1
```

---

## Listing Block Devices

### lsblk

Displays information about storage devices and partitions.

```bash
lsblk
```

Example Output:

```text
NAME   SIZE TYPE MOUNTPOINT
sda    100G disk
├─sda1  50G part /
└─sda2  50G part /home
```

---

## Viewing Disk Partitions

### fdisk

List partition information:

```bash
sudo fdisk -l
```

Used for creating and managing disk partitions.

---

## Mounting File Systems

### mount

Mount a storage device:

```bash
sudo mount /dev/sdb1 /mnt
```

View mounted file systems:

```bash
mount
```

---

## Unmounting File Systems

### umount

Unmount a storage device:

```bash
sudo umount /mnt
```

or

```bash
sudo umount /dev/sdb1
```

---

## File System Information

### blkid

Display UUID and file system information:

```bash
sudo blkid
```

---

## Persistent Mounts

The `/etc/fstab` file is used to automatically mount file systems during system boot.

View file:

```bash
cat /etc/fstab
```

Example Entry:

```text
UUID=xxxx-xxxx /data ext4 defaults 0 2
```

---

## Checking File System Usage

### find Large Files

```bash
find / -type f -size +100M
```

Finds files larger than 100 MB.

---

## Useful Commands

```bash
df -h
du -sh
lsblk
fdisk -l
mount
umount
blkid
cat /etc/fstab
```

---
