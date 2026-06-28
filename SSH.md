# SSH Basics

## What is SSH?

SSH (Secure Shell) is a secure protocol used to connect to remote Linux systems over a network.

It allows administrators to:

* Manage remote servers
* Transfer files securely
* Execute commands remotely
* Perform system administration tasks

---

# Check SSH Service Status

## Command

```bash
systemctl status ssh
```

## Purpose

Checks whether the SSH service is running.

---

# Start SSH Service

## Command

```bash
sudo systemctl start ssh
```

## Purpose

Starts the SSH service immediately.

---

# Stop SSH Service

## Command

```bash
sudo systemctl stop ssh
```

## Purpose

Stops the SSH service.

---

# Enable SSH at Boot

## Command

```bash
sudo systemctl enable ssh
```

## Purpose

Ensures SSH starts automatically when the system boots.

---

# Disable SSH at Boot

## Command

```bash
sudo systemctl disable ssh
```

## Purpose

Prevents SSH from starting automatically after a reboot.

---

# Connect to a Remote Server

## Command

```bash
ssh username@server_ip
```

## Example

```bash
ssh admin@192.168.1.10
```

## Purpose

Connects securely to a remote Linux machine.

---

# Connect Using a Custom Port

## Command

```bash
ssh -p 2222 username@server_ip
```

## Purpose

Connects to an SSH service running on a non-default port.

---

# Generate SSH Keys

## Command

```bash
ssh-keygen
```

## Purpose

Creates a public/private key pair for passwordless authentication.

---

# Copy SSH Key to Remote Server

## Command

```bash
ssh-copy-id username@server_ip
```

## Purpose

Copies your public key to a remote server.

This enables passwordless login.

---

# Login Using SSH Key

## Command

```bash
ssh username@server_ip
```

## Purpose

Logs in using key-based authentication if configured.

---

# Transfer Files with SCP

## Copy File to Remote Server

```bash
scp file.txt username@server_ip:/home/user/
```

## Copy File from Remote Server

```bash
scp username@server_ip:/home/user/file.txt .
```

## Purpose

Securely transfers files between systems.

---

# View SSH Logs

## Command

```bash
journalctl -u ssh
```

## Purpose

Displays SSH service logs.

Useful for troubleshooting connection issues.

---

# Common SSH Troubleshooting

### Cannot Connect to Server

1. Check SSH service status

```bash
systemctl status ssh
```

2. Verify SSH is listening

```bash
ss -tulnp | grep ssh
```

3. Check firewall rules

```bash
sudo ufw status
```

4. Review SSH logs

```bash
journalctl -u ssh
```

---

# Practice Tasks

1. Check whether SSH is running.
2. Start and stop the SSH service.
3. Enable SSH to start at boot.
4. Generate an SSH key pair.
5. Connect to another Linux machine using SSH.
6. Transfer a file using SCP.
7. View SSH logs using journalctl.

---

# Key Commands Summary

| Command              | Purpose                   |
| -------------------- | ------------------------- |
| systemctl status ssh | Check SSH status          |
| systemctl start ssh  | Start SSH                 |
| systemctl stop ssh   | Stop SSH                  |
| systemctl enable ssh | Enable SSH at boot        |
| ssh user@ip          | Connect to remote server  |
| ssh -p port user@ip  | Connect using custom port |
| ssh-keygen           | Generate SSH keys         |
| ssh-copy-id          | Copy SSH key              |
| scp                  | Transfer files securely   |
| journalctl -u ssh    | View SSH logs             |

---