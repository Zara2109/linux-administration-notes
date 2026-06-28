# Systemctl Commands

systemctl is used to manage services and the systemd init system in Linux

## Check Service Status 

```bash
systemctl status nginx
```

Displays whether a service is running, stopped, enabled, or has encountered errors.

---

## Start a Service

```bash
systemctl start nginx
```

Starts a service immediately

---

## Stop a Service  

```bash
systemctl stop nginx
```

Stops a running service

---

## Restart a Service 

```bash
systemctl restart nginx
```

Stops and Starts a service again.

---

## Reload a Service

```bash
systemctl reload nginx
```

Reloads the service configuration without fully restarting the service.

---

## Enable a Service 

```bash
systemctl enable nginx
```

Configures the service to start automatically during system boot.

---

## Disable a Service

```bash
systemctl disable nginx
```

Prevents the service from starting automatically after a reboot.

---

## Check if a Service is Active

```bash
systemctl is-active nginx
```

Returns the current state of the service.

Example ouputs:

```plain text
active 
inactive
failed
```

---

## Check if a Service is Enabled

```bash
systemctl is-enabled nginx
```

Checks if the sservice is configured to start automatically at boot.

---

## View Failed Services

```bash
systemctl --failed
```

Displays all services currently in a failed state.

---

## Difference between Start and Enable 

| Command | Purpose |
|----------|----------|
|`systemctl start nginx` | Starts the service immediately |
|`systemctl enable nginx` | Starts the service automatically after every boot |

Using enable does not start the service immediately, and using start does not make it persistent across reboots.

---

## Common Troubleshooting Workflow 

1. Check service status

```bash
systemctl status nginx
```

2. Check logs

```bash
journalctl -u nginx
```

3. Restart the service

```bash
systemctl restart nginx
```

4. Verify the service is active.

```bash
systemctl is-active nginx
```

---

## Summary

systemctl is the primary tool used to manage services in Linux systems that use systemd. It allows administrators to start, stop, restart, reload, enable, disable, and troubleshoot services efficiently.