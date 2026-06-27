# Journalctl Commands

jouranlctl is used to view and analyze logs collected by systemd.

## View All Logs

```bash
journalctl
```

Displays all logs stored in the systemd journal.

---

## View Logs for a Specific Service

```bash
journalctl -u nginx
```

Shows logs related to a specific service.

---

## Follow Logs in Real Time.

```bash
journalctl -f
```

Continuously displays new log entries as they are generated.

---

## View Logs from Current Boot

```bash
journalctl -b
```
Shows logs generated since the last system boot.

---

## View Recent Log Entries

```bash
journalctl -n 20
```

Displays the last 20 log entries.

---

## View Logs with Explanation

```bash
journalctl -xe
```

Shows detailed logs and additional context that can help diagnose issues.

---

## View Logs for a Service Since Boot

```bash
journalctl -u nginx -b
```

Displays logs for a specific service from the current boot.

---

## Common Troubleshooting Workflow 

### Check Service Status
```bash
systemctl status nginx
```

### Check Service Logs
```bash
journalctl -u nginx
```

### Follow Logs While Testing
```bash
jornalctl -f
```

### Restart Service
```bash
systemctl restart nginx
```

### Verify Service Status
```bash
systemctl is-actice nginx
```

---

## Common Use Cases

| Situation | Command |
|------------|------------|
| View all logs | journalctl |
| Check ngnix logs | journalctl -u nginx |
| Follow logs live | journalctl -f |
| Check current boot logs | journalctl -b |
| View recent entries | journalctl -n 20 |
| Investigate errors | journalctl -xe |

---

## Summary
journalctl is an essential troubleshooting tool in Linux. It helps administrators inspect system logs, service logs, boot logs, and real-time events to diagnose and resolve issues.