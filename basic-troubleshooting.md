# Basic Linux Troubleshooting

Troubleshooting is the process of identifying, diagnosing, and resolving issues in a Linux system.

## Troubleshooting Mindset

Before running commands, ask:

1. What is the problem?
2. What changed recently?
3. Is the service running?
4. Are there any error logs?
5. Is the system running out of resources?
6. Are permissions configured correctly?

---

## Scenario 1: Website Is Not Accessible

### Step 1: Check Service Status
```bash
systemctl status nginx
```

### Step 2: Check Service Logs
```bash
journalctl -u nginx
```

### Step 3: Check Listening Ports
```bash
ss -tulpn
```

### Step 4: Test Locally
```bash
curl localhost
```

---

## Scenario 2: Service Fails to Start

### Check Status
```bash
systemctl status nginx
```

### Check Detailed Logs
```bash
journalctl -xe
```

### Check Service-Specific Logs
```bash
journalctl -u nginx
```

---

## Scenario 3: Permission Denied Error

### Check Permissions
```bash
ls -l file.txt
```

### Check Ownership
```bash
ls -ld directory/
```

### Fix Permissions
```bash
chmod 755 file.txt
```

### Fix Ownership
```bash
chown user:group file.txt
```

---

## Scenario 4: User Cannot Access a Resource

### Check User Information
```bash
id username
```

### Check Group Membership
```bash
groups username
```

### Add User to Group
```bash
usermod -aG developers username
```

---

## Scenario 5: System Running Out of Disk Space

### Check Disk Usage
```bash
df -h
```

### Check Directory Sizes
```bash
du -sh *
```

---

## Common Troubleshooting Commands

| Purpose |	Command |
|----------|----------|
| Check service status | systemctl status service |
| View service logs |	journalctl -u service |
| View recent logs |	journalctl -n 20 |
| Check open ports | ss -tulpn|
| Test local service | curl localhost |
| Check disk usage | df -h |
| Check permissions | ls -l |
| Check ownership | ls -ld |
| Check user groups | id username |

---

## Key Principle

Always investigate before fixing.

Gather information, identify the root cause, and then apply a solution instead of randomly running commands.