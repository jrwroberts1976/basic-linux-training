# Lesson 02 - Systemd and Service Troubleshooting

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 04 – Processes and Services
> - Module 10 – Troubleshooting Fundamentals
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Linux systems rely on services to provide essential functionality.

Examples:

- SSH access
- Web servers
- Databases
- Monitoring agents
- Container platforms

When a service fails, administrators need to identify:

- What failed
- Why it failed
- How to restore operation

Modern Linux distributions use **systemd** to manage services and system startup.

This lesson covers service troubleshooting, system logs, and recovery techniques.

---

# Learning Objectives

By completing this lesson you will understand:

- How systemd manages services
- How to check service status
- How to start and stop services
- How to investigate failed services
- How to use journalctl for troubleshooting
- How to troubleshoot boot problems
- How to recover failed services

---

# What Is systemd?

systemd is the service manager used by many modern Linux distributions.

It manages:

- System startup
- Services
- Background processes
- Logging
- Dependencies

Example:

```text
System Boot

    |

systemd

    |

Services Start

    |

System Ready
```

---

# Checking systemd Version

View systemd information:

```bash
systemctl --version
```

Example:

```text
systemd 255
```

---

# Understanding Services

A service is a background process that provides functionality.

Examples:

| Service | Purpose |
|---|---|
| ssh | Remote access |
| nginx | Web server |
| docker | Container management |
| cron | Scheduled tasks |

---

# Viewing Service Status

Check a service:

```bash
systemctl status service-name
```

Example:

```bash
systemctl status ssh
```

Output includes:

```text
Active:

running
```

or:

```text
failed
```

---

# Service States

Common states:

| State | Meaning |
|---|---|
| active | Running |
| inactive | Stopped |
| failed | Error occurred |
| activating | Starting |
| deactivating | Stopping |

---

# Starting Services

Start a service:

```bash
sudo systemctl start service-name
```

Example:

```bash
sudo systemctl start ssh
```

---

# Stopping Services

Stop a service:

```bash
sudo systemctl stop service-name
```

Example:

```bash
sudo systemctl stop ssh
```

---

# Restarting Services

Restart a service:

```bash
sudo systemctl restart service-name
```

Common after:

- Configuration changes
- Updates
- Troubleshooting fixes

---

# Reloading Services

Some services can reload configuration without restarting.

Example:

```bash
sudo systemctl reload nginx
```

---

# Enable Services at Boot

Enable automatic startup:

```bash
sudo systemctl enable service-name
```

Example:

```bash
sudo systemctl enable docker
```

---

# Disable Services at Boot

Disable startup:

```bash
sudo systemctl disable service-name
```

---

# Listing Services

List running services:

```bash
systemctl list-units --type=service
```

---

List failed services:

```bash
systemctl --failed
```

---

# Investigating Failed Services

When a service fails:

Start with:

```bash
systemctl status service-name
```

Look for:

- Error messages
- Exit codes
- Configuration problems
- Missing files

---

# Viewing Service Logs

systemd stores service logs using journald.

View service logs:

```bash
journalctl -u service-name
```

Example:

```bash
journalctl -u ssh
```

---

# Viewing Recent Logs

Show recent entries:

```bash
journalctl -u service-name -n 50
```

Example:

```bash
journalctl -u docker -n 100
```

---

# Following Live Logs

Watch logs as they appear:

```bash
journalctl -u service-name -f
```

Useful when:

- Restarting services
- Testing changes
- Watching errors

---

# Common Service Failures

---

# Configuration Errors

Symptoms:

```text
Service fails immediately
```

Check:

- Configuration syntax
- Recent changes
- Log messages

Example:

```bash
nginx -t
```

---

# Port Already in Use

Symptoms:

```text
Cannot start service
```

Check ports:

```bash
ss -tulnp
```

Example:

```text
Port 8080 already used
```

---

# Missing Files

Symptoms:

```text
Service starts then stops
```

Check:

```bash
journalctl -u service-name
```

---

# Permission Problems

Symptoms:

```text
Access denied
```

Check:

- File ownership
- Permissions
- Service user

Example:

```bash
ls -l /path/to/file
```

---

# Dependency Problems

Some services require other services.

View dependencies:

```bash
systemctl list-dependencies service-name
```

Example:

```bash
systemctl list-dependencies docker
```

---

# Boot Troubleshooting

If Linux fails during startup:

Check previous boot logs:

```bash
journalctl -b -1
```

View current boot:

```bash
journalctl -b
```

---

# Checking Boot Performance

View startup time:

```bash
systemd-analyze
```

Example:

```text
Startup finished in 8s
```

---

View slow services:

```bash
systemd-analyze blame
```

---

# Recovery Mode

Linux provides recovery options.

Examples:

- Single user mode
- Emergency mode
- Rescue mode

Useful for:

- Password recovery
- Repairing systems
- Fixing failed services

---

# Practical Lab

The objective of this lab is to troubleshoot Linux services.

Tasks:

- Check service status
- Review logs
- Restart services
- Investigate failures

---

# Lab 1 - Check SSH Service

Run:

```bash
systemctl status ssh
```

Identify:

- Current state
- Process ID
- Recent messages

---

# Lab 2 - Review Service Logs

Run:

```bash
journalctl -u ssh -n 50
```

Identify:

- Service events
- Errors

---

# Lab 3 - Find Failed Services

Run:

```bash
systemctl --failed
```

Investigate any failures.

---

# Lab 4 - Analyse Boot Performance

Run:

```bash
systemd-analyze
```

Then:

```bash
systemd-analyze blame
```

Identify:

- Slow services
- Startup delays

---

# Lab Challenge

A web server fails to start after a configuration change.

Troubleshoot:

1. Check service status

```text
systemctl status nginx
```

2. Review logs

```text
journalctl -u nginx
```

3. Check configuration

```text
nginx -t
```

4. Identify the cause

5. Apply the fix

6. Verify the service is running

---

# Summary

In this lesson you learned:

- How systemd manages services
- How to check service status
- How to start and stop services
- How to analyse service failures
- How to use journalctl
- How to troubleshoot boot issues

The next lesson covers:

```text
Lesson 03 - Network Troubleshooting
```
