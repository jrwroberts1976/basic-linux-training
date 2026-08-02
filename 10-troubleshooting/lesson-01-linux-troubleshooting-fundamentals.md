# Lesson 01 - Linux Troubleshooting Fundamentals

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 04 – Processes and Services
> - Module 06 – Networking Fundamentals
> - Module 07 – Storage Management
> - Module 09 – Security
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Troubleshooting is a core skill for Linux administrators.

A Linux system can experience problems involving:

- Services
- Applications
- Hardware
- Storage
- Networking
- Security
- Performance

Effective troubleshooting requires a structured approach rather than guessing.

A good administrator uses evidence from:

- Logs
- System information
- Monitoring tools
- Configuration files
- Command output

to identify the root cause of problems.

---

# Learning Objectives

By completing this lesson you will understand:

- A structured troubleshooting process
- How to identify problems
- How to collect system information
- How to analyse logs
- Common Linux diagnostic commands
- How to document troubleshooting activities

---

# What Is Troubleshooting?

Troubleshooting is the process of:

```text
Identifying a problem

        |

Finding the cause

        |

Applying a solution

        |

Confirming recovery
```

The goal is not just to fix the issue, but to understand why it happened.

---

# Troubleshooting Methodology

A structured approach helps avoid unnecessary changes.

The troubleshooting process:

```text
1. Identify the problem

2. Gather information

3. Analyse evidence

4. Create a theory

5. Test the theory

6. Apply a fix

7. Verify the solution

8. Document the outcome
```

---

# Step 1 - Identify the Problem

Before making changes, understand the issue.

Questions to ask:

- What is failing?
- When did it start?
- Who is affected?
- Is it always failing?
- Has anything changed?

Example:

```text
Application is unavailable

Started:

10:30

Affected:

All users
```

---

# Step 2 - Gather Information

Collect facts before making changes.

Useful information:

- Operating system version
- Running services
- Recent changes
- Error messages
- Logs
- Resource usage

---

# System Information Commands

View operating system information:

```bash
cat /etc/os-release
```

Example:

```text
Debian GNU/Linux
```

---

View kernel information:

```bash
uname -a
```

Example:

```text
Linux server 6.x.x
```

---

View hostname:

```bash
hostname
```

---

# Checking System Health

Basic health checks:

---

## Uptime

Shows how long the system has been running.

```bash
uptime
```

Example:

```text
up 15 days
```

---

## Memory Usage

Check RAM usage:

```bash
free -h
```

Example:

```text
total

used

available
```

---

## Disk Usage

Check filesystem space:

```bash
df -h
```

Example:

```text
Filesystem

Size

Used

Available
```

---

# Process Investigation

Processes are a common source of problems.

View running processes:

```bash
ps aux
```

---

Interactive process view:

```bash
top
```

or:

```bash
htop
```

Look for:

- High CPU usage
- High memory usage
- Stuck processes

---

# Checking Services

Many Linux problems involve failed services.

View service status:

```bash
systemctl status service-name
```

Example:

```bash
systemctl status ssh
```

---

List failed services:

```bash
systemctl --failed
```

---

# Logs and Troubleshooting

Logs provide evidence about what happened.

Linux uses:

```text
systemd journal
```

View logs:

```bash
journalctl
```

---

View recent errors:

```bash
journalctl -p err
```

---

View logs for a service:

```bash
journalctl -u ssh
```

---

# Kernel Messages

The kernel records hardware and system events.

View kernel messages:

```bash
dmesg
```

Search for errors:

```bash
dmesg | grep error
```

---

# Common Linux Problems

---

# Disk Full

Symptoms:

- Applications fail
- Logs cannot be written
- System becomes unstable

Check:

```bash
df -h
```

Find large directories:

```bash
du -sh /*
```

---

# High CPU Usage

Symptoms:

- Slow system
- Applications respond slowly

Check:

```bash
top
```

Look for:

- Processes using high CPU
- Runaway applications

---

# High Memory Usage

Symptoms:

- Applications crash
- System becomes slow

Check:

```bash
free -h
```

Find memory users:

```bash
ps aux --sort=-%mem
```

---

# Service Failure

Symptoms:

- Application unavailable
- Connection failures

Check:

```bash
systemctl status service-name
```

Review logs:

```bash
journalctl -u service-name
```

---

# Network Problems

Symptoms:

- Cannot reach systems
- Applications cannot connect

Check IP configuration:

```bash
ip address
```

Test connectivity:

```bash
ping 8.8.8.8
```

Check routes:

```bash
ip route
```

---

# Documentation During Troubleshooting

Good documentation should record:

```text
Problem:

Evidence:

Investigation:

Root Cause:

Fix:

Verification:
```

Example:

```text
Problem:

Web service unavailable

Evidence:

Apache service stopped

Root Cause:

Configuration error

Fix:

Corrected configuration

Verification:

Website accessible
```

---

# Practical Lab

The objective of this lab is to practise basic troubleshooting.

Tasks:

- Gather system information
- Check resources
- Review logs
- Investigate services

---

# Lab 1 - Collect System Information

Run:

```bash
hostname

uname -a

cat /etc/os-release
```

Record:

- Hostname
- Kernel version
- Operating system

---

# Lab 2 - Check System Resources

Run:

```bash
uptime

free -h

df -h
```

Identify:

- CPU load
- Memory usage
- Disk availability

---

# Lab 3 - Review Failed Services

Run:

```bash
systemctl --failed
```

Investigate any failures.

---

# Lab 4 - Review Logs

Run:

```bash
journalctl -p err
```

Identify:

- Errors
- Warnings
- Failed services

---

# Lab Challenge

A Linux server is reported as "slow".

Create a troubleshooting plan.

Check:

1. CPU usage
2. Memory usage
3. Disk space
4. Running processes
5. Failed services
6. System logs

Explain how you would identify the root cause.

---

# Summary

In this lesson you learned:

- A structured troubleshooting process
- How to collect system information
- How to check system resources
- How to investigate processes
- How to use logs
- How to document troubleshooting

The next lesson covers:

```text
Lesson 02 - Systemd and Service Troubleshooting
```
