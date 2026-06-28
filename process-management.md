# Process Management in Linux

## What is a Process?

A process is a program that is currently running on the system.

Examples:
- Web server (nginx)
- SSH service
- Bash shell
- Firefox browser

Each process is assigned a unique Process ID (PID).

---

## Viewing Running Processes

### ps

Displays information about active processes.

```bash
ps
```

View all running processes:

```bash
ps aux
```

Example:

```bash
ps aux | grep ssh
```

---

### top

Displays real-time information about system processes and resource usage.

```bash
top
```

Press `q` to quit.

---

### htop

An improved version of top with a more user-friendly interface.

Install:

```bash
sudo apt install htop
```

Run:

```bash
htop
```

---

## Finding Processes

### pgrep

Search for a process by name.

```bash
pgrep nginx
```

### pidof

Displays the PID of a running program.

```bash
pidof sshd
```

---

## Stopping Processes

### kill

Terminate a process using its PID.

```bash
kill PID
```

Example:

```bash
kill 1234
```

### kill -9

Forcefully terminate a process.

```bash
kill -9 1234
```

---

### pkill

Terminate processes by name.

```bash
pkill nginx
```

### killall

Stop all processes with the specified name.

```bash
killall nginx
```

---

## Background Processes

Run a command in the background:

```bash
sleep 100 &
```

View background jobs:

```bash
jobs
```

Bring a job to the foreground:

```bash
fg %1
```

Move a stopped job to the background:

```bash
bg
```

---

## Process Priorities

### nice

Start a process with a specific priority.

```bash
nice -n 10 command
```

Example:

```bash
nice -n 10 tar -czf backup.tar.gz /data
```

### renice

Change the priority of an existing process.

```bash
sudo renice 5 PID
```

---

## Useful Commands

```bash
ps aux
top
htop
pgrep
pidof
kill
kill -9
pkill
killall
jobs
fg
bg
nice
renice
```

---

