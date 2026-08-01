# Module 04 - Processes and Services

> **Estimated time:** 4–5 hours  
>
> **Prerequisites:**
> - Module 00 – Introduction to Linux
> - Module 01 – Command Line Fundamentals
> - Module 02 – Linux Filesystem Administration
> - Module 03 – Users and Groups
>
> **Difficulty:** Beginner to Intermediate
>
> **Hands-on exercises:** Yes

---

# Overview

A Linux system is constantly running processes and services.

Every application, command, background task and system component runs as a process. Understanding how Linux manages these processes is essential for system administration, monitoring and troubleshooting.

This module introduces Linux process management, service management using systemd, and the tools administrators use to investigate system behaviour.

---

# Learning Objectives

By completing this module you will be able to:

- Understand what a Linux process is
- Identify running processes
- Understand process IDs (PID)
- Understand parent and child processes
- Monitor CPU and memory usage
- Manage running processes
- Understand Linux services
- Use systemd to manage services
- Review system and service logs
- Troubleshoot common service problems

---

# Lessons

| Lesson | Topic | Status |
|---|---|---|
| 01 | Understanding Linux Processes | 🚧 In Progress |
| 02 | Managing Linux Processes | ☐ Planned |
| 03 | Systemd and Service Management | ☐ Planned |
| 04 | Logs and journalctl | ☐ Planned |
| 05 | Processes and Services Administration Lab | ☐ Planned |

---

# Topics Covered

## Understanding Linux Processes

Topics:

- What is a process?
- Programs vs processes
- Process IDs (PID)
- Parent processes
- Child processes
- Process states
- Background processes
- Daemons

Commands:

```bash
ps
pstree
pgrep
top
```

Managing Linux Processes

Topics:

Viewing running processes
Starting processes
Stopping processes
Process signals
Background jobs
Foreground jobs

Commands:
```bash
kill
pkill
jobs
bg
fg
```

Systemd and Service Management

Topics:

Understanding systemd
Service units
Starting services
Stopping services
Restarting services
Enabling services at boot
Checking service status

Command:

systemctl
Logs and Troubleshooting

Topics:

Linux logging
Service logs
System events
Troubleshooting service failures

Commands:
```bash
journalctl
dmesg
```
Practical Lab

The module concludes with a practical administration exercise covering:

Identifying running processes
Monitoring CPU and memory usage
Managing processes
Starting and stopping services
Investigating failed services
Reviewing system logs
Troubleshooting common problems
Summary

By the end of this module you should understand:

How Linux runs applications and services
How to identify and monitor processes
How to manage running processes safely
How systemd manages services
How to investigate service problems using logs
Module Progress

Status:

🚧 In Progress

Next Module

Module 05 – Package Management