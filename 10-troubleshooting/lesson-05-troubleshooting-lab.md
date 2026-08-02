# Lesson 05 - Troubleshooting Lab

> **Estimated time:** 90–120 minutes
>
> **Prerequisites:**
> - Module 10 – Troubleshooting
> - Lesson 01 – Linux Troubleshooting Fundamentals
> - Lesson 02 – Systemd and Service Troubleshooting
> - Lesson 03 – Network Troubleshooting
> - Lesson 04 – Performance Troubleshooting
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

This practical lab brings together the troubleshooting skills learned throughout this module.

Real-world Linux administration involves investigating problems where the cause is not immediately obvious.

This lab focuses on:

- Gathering evidence
- Identifying root causes
- Applying fixes
- Verifying recovery
- Documenting solutions

---

# Troubleshooting Process

Use this approach for every scenario:

```text
Identify Problem

        |

Gather Evidence

        |

Analyse Information

        |

Find Root Cause

        |

Apply Fix

        |

Verify Recovery

        |

Document Result
```

---

# Lab Environment

You will need:

- Linux system
- sudo access
- Terminal access

Check your system:

```bash
hostname

uname -a

cat /etc/os-release
```

---

# Scenario 1 - Failed Service

## Problem

A user reports:

```text
The SSH service is unavailable.
```

---

## Investigation

Check service status:

```bash
systemctl status ssh
```

Check logs:

```bash
journalctl -u ssh
```

Check if the service is running:

```bash
systemctl is-active ssh
```

---

## Possible Causes

Investigate:

- Service stopped
- Configuration error
- Port conflict
- Permission issue

---

## Resolution

Start the service:

```bash
sudo systemctl start ssh
```

Verify:

```bash
systemctl status ssh
```

---

# Scenario 2 - Disk Space Problem

## Problem

A server reports:

```text
Applications are failing.

Logs cannot be written.
```

---

## Investigation

Check disk usage:

```bash
df -h
```

Find large directories:

```bash
du -sh /*
```

Check log usage:

```bash
du -sh /var/log/*
```

---

## Possible Causes

Examples:

- Large log files
- Application data growth
- Temporary files

---

## Resolution

Possible actions:

- Remove unnecessary files
- Rotate logs
- Increase storage capacity

Verify:

```bash
df -h
```

---

# Scenario 3 - Network Connectivity Failure

## Problem

A server cannot access the internet.

---

## Investigation

Check interfaces:

```bash
ip address
```

Check routes:

```bash
ip route
```

Test gateway:

```bash
ping gateway-address
```

Test external connectivity:

```bash
ping 8.8.8.8
```

---

## DNS Test

Test name resolution:

```bash
nslookup google.com
```

---

## Possible Causes

Examples:

- Missing IP address
- Incorrect gateway
- DNS failure
- Firewall restriction

---

## Resolution

Correct:

- Network configuration
- DNS settings
- Firewall rules

Verify:

```bash
ping google.com
```

---

# Scenario 4 - High CPU Usage

## Problem

A server is running slowly.

---

## Investigation

Check load:

```bash
uptime
```

View processes:

```bash
top
```

Find CPU intensive processes:

```bash
ps aux --sort=-%cpu
```

---

## Possible Causes

Examples:

- Runaway process
- Application bug
- Excessive workload

---

## Resolution

Possible actions:

Stop process:

```bash
kill PID
```

Restart service:

```bash
sudo systemctl restart service-name
```

Verify:

```bash
top
```

---

# Scenario 5 - High Memory Usage

## Problem

Applications are crashing.

---

## Investigation

Check memory:

```bash
free -h
```

Find memory users:

```bash
ps aux --sort=-%mem
```

Check swap:

```bash
swapon --show
```

---

## Possible Causes

Examples:

- Memory leak
- Too many applications
- Insufficient RAM

---

## Resolution

Possible actions:

- Restart application
- Adjust memory limits
- Increase available memory

---

# Scenario 6 - Container Troubleshooting

## Problem

A Docker application is unavailable.

---

## Investigation

List containers:

```bash
docker ps
```

Check stopped containers:

```bash
docker ps -a
```

View logs:

```bash
docker logs container-name
```

Check resources:

```bash
docker stats
```

---

## Possible Causes

Examples:

- Container stopped
- Application crash
- Resource exhaustion
- Port conflict

---

## Resolution

Restart container:

```bash
docker restart container-name
```

Review configuration:

```bash
docker inspect container-name
```

---

# Troubleshooting Documentation Exercise

Document one problem using:

```text
Problem:

Impact:

Evidence Collected:

Investigation Performed:

Root Cause:

Resolution:

Verification:
```

Example:

```text
Problem:

Web service unavailable

Impact:

Users cannot access website

Evidence:

Service stopped

Root Cause:

Configuration error

Resolution:

Fixed configuration

Verification:

Website accessible
```

---

# Final Challenge

A Linux server has multiple issues:

```text
Users cannot access the website

CPU usage is high

Disk usage is 95%

A Docker container keeps restarting
```

Create a troubleshooting plan.

Investigate:

1. System resources

```text
CPU

Memory

Disk
```

2. Services

```text
systemctl

journalctl
```

3. Network

```text
ip

ss

ping
```

4. Containers

```text
docker ps

docker logs

docker stats
```

Explain:

- What information you collected
- How you identified the causes
- What fixes you applied

---

# Review Questions

## Question 1

What command shows failed systemd services?

```text
Answer:
```

---

## Question 2

What command shows disk usage?

```text
Answer:
```

---

## Question 3

What command displays listening network ports?

```text
Answer:
```

---

## Question 4

What command displays service logs?

```text
Answer:
```

---

## Question 5

Why should troubleshooting be evidence based?

```text
Answer:
```

---

# Summary

In this module you learned:

- How to troubleshoot Linux systematically
- How to investigate services
- How to diagnose network problems
- How to analyse performance issues
- How to troubleshoot containers
- How to document solutions

You have now completed:

```text
Module 10 - Troubleshooting
```

Next module:

```text
Module 11 - Automation and DevOps Fundamentals
```
