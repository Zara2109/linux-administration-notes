# Networking Basics

## What is Networking?

Networking allows computers and devices to communicate with each other. Linux provides several tools to view network settings, test connectivity, troubleshoot issues, and monitor network services.

---

# Check IP Address

## Command

```bash
ip addr show
```

## Purpose

Displays network interfaces and their assigned IP addresses.

## Example Use Case

Use this command when you need to identify the IP address of your Linux system.

---

# Check Routing Table

## Command

```bash
ip route
```

## Purpose

Displays routing information and the default gateway used to reach external networks.

## Example Use Case

Useful when troubleshooting internet connectivity issues.

---

# Test Network Connectivity

## Command

```bash
ping google.com
```

## Purpose

Tests whether a remote host is reachable and measures response time.

## Example Use Case

Verify that the system has internet access.

---

# View Open Ports and Listening Services

## Command

```bash
ss -tulnp
```

## Purpose

Displays active listening ports and the services using them.

## Example Use Case

Check whether a service such as SSH or Nginx is listening on the expected port.

---

# DNS Lookup

## Commands

```bash
nslookup google.com
```

```bash
dig google.com
```

## Purpose

Resolves domain names into IP addresses.

## Example Use Case

Troubleshoot DNS-related issues when websites cannot be reached by name.

---

# Fetch Web Content

## Using curl

```bash
curl https://example.com
```

### Purpose

Retrieves data from a URL and displays the response.

---

## Using wget

```bash
wget https://example.com/file.txt
```

### Purpose

Downloads files from the internet.

---

# Common Networking Troubleshooting Steps

### Website Not Loading

1. Check internet connectivity.

```bash
ping google.com
```

2. Verify the website can be reached.

```bash
ping website.com
```

3. Check DNS resolution.

```bash
nslookup website.com
```

4. Check listening ports.

```bash
ss -tulnp
```

5. Verify web server status.

```bash
systemctl status nginx
```

6. Review service logs.

```bash
journalctl -u nginx
```

---

# Practice Tasks

1. Find your system's IP address.
2. Identify the default gateway.
3. Ping a public website.
4. View listening ports and services.
5. Resolve a domain name using nslookup.
6. Download a sample file using wget.

---

# Key Commands Summary

| Command      | Purpose             |
| ------------ | ------------------- |
| ip addr show | View IP addresses   |
| ip route     | View routing table  |
| ping         | Test connectivity   |
| ss -tulnp    | View open ports     |
| nslookup     | DNS lookup          |
| dig          | Advanced DNS lookup |
| curl         | Fetch web content   |
| wget         | Download files      |

```
```
