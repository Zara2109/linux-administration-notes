# Package Management in Linux

## What is Package Management?

Package management is the process of installing, updating, removing, and managing software on a Linux system.

Different Linux distributions use different package managers.

Examples:
- Debian/Ubuntu → APT
- RHEL/CentOS/Rocky Linux → DNF/YUM

---

## APT (Advanced Package Tool)

Used in Debian-based distributions such as Ubuntu.

### Update Package List

```bash
sudo apt update
```

Downloads the latest package information from repositories.

---

### Upgrade Installed Packages

```bash
sudo apt upgrade
```

Upgrades installed packages to newer versions.

---

### Install a Package

```bash
sudo apt install package_name
```

Example:

```bash
sudo apt install nginx
```

---

### Remove a Package

```bash
sudo apt remove package_name
```

Example:

```bash
sudo apt remove nginx
```

---

### Remove Package and Configuration Files

```bash
sudo apt purge package_name
```

---

### Search for a Package

```bash
apt search package_name
```

Example:

```bash
apt search nginx
```

---

### Show Package Information

```bash
apt show package_name
```

Example:

```bash
apt show nginx
```

---

## DNF

Used in modern RHEL, Rocky Linux, AlmaLinux, and Fedora systems.

### Install a Package

```bash
sudo dnf install nginx
```

### Update Packages

```bash
sudo dnf update
```

### Remove a Package

```bash
sudo dnf remove nginx
```

### Search for a Package

```bash
dnf search nginx
```

### Show Package Information

```bash
dnf info nginx
```

---

## YUM

Older package manager used in CentOS and older RHEL versions.

### Install a Package

```bash
sudo yum install nginx
```

### Update Packages

```bash
sudo yum update
```

### Remove a Package

```bash
sudo yum remove nginx
```

---

## Package Repositories

Repositories are online sources that store software packages.

Package managers download software from configured repositories.

Repository configuration files are commonly located in:

```bash
/etc/apt/
/etc/yum.repos.d/
```

---

## Listing Installed Packages

APT:

```bash
apt list --installed
```

DNF:

```bash
dnf list installed
```

---

## Checking if a Package is Installed

APT:

```bash
dpkg -l | grep nginx
```

DNF:

```bash
rpm -qa | grep nginx
```

---

## Useful Commands

```bash
sudo apt update
sudo apt upgrade
sudo apt install
sudo apt remove
apt search
apt show

sudo dnf install
sudo dnf update
sudo dnf remove
dnf search
dnf info
```

---

## Common Interview Questions

### What is a package manager?

A package manager is a tool used to install, update, remove, and manage software packages.

### Which package manager is used in Ubuntu?

APT.

### Which package manager is used in RHEL and Rocky Linux?

DNF.

### What does apt update do?

It refreshes the package list from repositories.

### What is the difference between apt remove and apt purge?

- `apt remove` removes the package.
- `apt purge` removes the package and its configuration files.

### What is a repository?

A repository is a storage location from which software packages are downloaded and installed.