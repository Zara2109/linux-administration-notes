# Cron Jobs in Linux

## What is a Cron Job?

A cron job is a scheduled task that runs automatically at specified times or intervals.

Cron jobs are commonly used for:
- Backups
- Log cleanup
- System maintenance
- Monitoring scripts
- Automated reports

---

## Cron Service

The cron service runs in the background and executes scheduled tasks.

Check service status:

```bash
systemctl status cron
```

On some distributions:

```bash
systemctl status crond
```

---

## Crontab

Crontab (Cron Table) is a file that contains scheduled tasks.

View current user's cron jobs:

```bash
crontab -l
```

Edit cron jobs:

```bash
crontab -e
```

Remove all cron jobs:

```bash
crontab -r
```

---

## Cron Job Format

```text
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of Week (0-7)
│ │ │ └──── Month (1-12)
│ │ └────── Day of Month (1-31)
│ └──────── Hour (0-23)
└────────── Minute (0-59)
```

---

## Examples

### Run Every Minute

```bash
* * * * * /home/user/script.sh
```

---

### Run Every Day at Midnight

```bash
0 0 * * * /home/user/backup.sh
```

---

### Run Every Day at 2:30 AM

```bash
30 2 * * * /home/user/script.sh
```

---

### Run Every Sunday

```bash
0 8 * * 0 /home/user/report.sh
```

Runs every Sunday at 8:00 AM.

---

### Run Every 5 Minutes

```bash
*/5 * * * * /home/user/script.sh
```

---

## Special Strings

Run tasks using shortcuts:

```bash
@reboot
```

Runs when the system starts.

```bash
@daily
```

Runs once per day.

```bash
@weekly
```

Runs once per week.

```bash
@monthly
```

Runs once per month.

```bash
@yearly
```

Runs once per year.

---

## Logging Cron Output

Save command output to a log file:

```bash
0 0 * * * /home/user/backup.sh >> /var/log/backup.log 2>&1
```

---

## Common Cron Directories

System-wide cron files may be found in:

```bash
/etc/crontab
/etc/cron.d/
/etc/cron.daily/
/etc/cron.weekly/
/etc/cron.monthly/
```

---

## Useful Commands

```bash
crontab -l
crontab -e
crontab -r
systemctl status cron
systemctl status crond
```

---
