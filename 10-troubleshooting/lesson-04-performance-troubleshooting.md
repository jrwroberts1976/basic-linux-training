# Lesson 04 - Performance Troubleshooting

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 04 – Processes and Services
> - Module 07 – Storage Management
> - Module 10 – Linux Troubleshooting Fundamentals
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Performance problems are common in Linux environments.

A system may become slow because of:

- High CPU usage
- Memory pressure
- Disk problems
- Excessive processes
- Resource-hungry applications
- Poor configuration

Performance troubleshooting requires identifying which resource is causing the problem.

The main areas to investigate are:

```text
CPU

Memory

Disk

Network

Processes
```

---

# Learning Objectives

By completing this lesson you will understand:

- How to investigate system performance
- How to analyse CPU usage
- How to troubleshoot memory problems
- How to identify disk issues
- How to investigate processes
- How to use Linux monitoring tools

---

# Performance Troubleshooting Methodology

A structured approach:

```text
Identify Slow System

        |

Check Resources

        |

Find Bottleneck

        |

Investigate Cause

        |

Apply Fix

        |

Verify Improvement
```

---

# System Load

Linux tracks system load.

View load:

```bash
uptime
```

Example:

```text
load average:

0.25 0.40 0.35
```

The three values represent:

```text
1 minute

5 minutes

15 minutes
```

---

# Understanding Load Average

A high load does not always mean high CPU usage.

Load can be caused by:

- CPU processes
- Disk waits
- Resource contention

Example:

```text
CPU:

20%

Load:

10
```

This may indicate processes waiting on another resource.

---

# CPU Troubleshooting

High CPU usage can cause:

- Slow applications
- Delayed responses
- Increased latency

---

# Viewing CPU Usage

Use:

```bash
top
```

or:

```bash
htop
```

Look for:

- Processes using CPU
- Number of running tasks
- Load average

---

# Finding CPU Intensive Processes

Sort processes:

```bash
ps aux --sort=-%cpu
```

Example:

```text
USER

PID

CPU%

COMMAND
```

---

# CPU Troubleshooting Questions

Ask:

- Is one process consuming CPU?
- Is CPU usage consistently high?
- Did a recent change cause the issue?
- Is the application expected to use CPU?

---

# Memory Troubleshooting

Insufficient memory can cause:

- Slow applications
- System freezes
- Processes being terminated

---

# Checking Memory Usage

Run:

```bash
free -h
```

Example:

```text
total

used

free

available
```

---

# Understanding Linux Memory

Linux uses available memory efficiently.

Memory may be used for:

- Applications
- Cache
- Buffers

High cache usage is not necessarily a problem.

---

# Finding Memory Heavy Processes

Run:

```bash
ps aux --sort=-%mem
```

Look for:

- Large applications
- Memory leaks
- Unexpected processes

---

# Swap Usage

Check swap:

```bash
swapon --show
```

or:

```bash
free -h
```

High swap usage can indicate:

- Memory pressure
- Insufficient RAM
- Poor application behaviour

---

# Disk Troubleshooting

Disk problems can affect:

- Application performance
- Boot times
- Logging
- Databases

---

# Checking Disk Space

View filesystem usage:

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

# Finding Large Files

Find large directories:

```bash
du -sh /*
```

Example:

```text
/var

20G
```

---

# Checking Disk Performance

Install tools:

```bash
sudo apt install sysstat
```

Use:

```bash
iostat
```

Look for:

- High utilisation
- High wait times
- Slow storage

---

# Inode Problems

A filesystem can run out of inodes even with free space available.

Check:

```bash
df -i
```

Symptoms:

- Cannot create files
- Applications fail to write data

---

# Process Troubleshooting

Processes can cause many performance issues.

View processes:

```bash
ps aux
```

---

# Process States

Common states:

| State | Meaning |
|---|---|
| R | Running |
| S | Sleeping |
| D | Waiting for I/O |
| Z | Zombie process |

---

# Finding Stuck Processes

View process tree:

```bash
pstree
```

Find process details:

```bash
ps -fp PID
```

---

# Stopping Processes

Terminate a process:

```bash
kill PID
```

Force stop:

```bash
kill -9 PID
```

Use carefully.

---

# Monitoring Tools

Common Linux monitoring tools:

| Tool | Purpose |
|---|---|
| top | Process monitoring |
| htop | Interactive monitoring |
| vmstat | System statistics |
| iostat | Disk performance |
| free | Memory usage |
| df | Disk space |
| sar | Historical performance |

---

# Application Performance

Applications can become slow because of:

- Database problems
- Configuration issues
- Resource limits
- Network delays

Always check:

- Application logs
- Service status
- System resources

---

# Containers and Performance

Containers can also consume excessive resources.

View containers:

```bash
docker ps
```

View resource usage:

```bash
docker stats
```

Look for:

- High CPU containers
- Memory limits
- Restarting containers

---

# Practical Lab

The objective of this lab is to investigate system performance.

Tasks:

- Check CPU usage
- Check memory usage
- Check disk space
- Investigate processes

---

# Lab 1 - Check System Load

Run:

```bash
uptime
```

Record:

- Load average
- System uptime

---

# Lab 2 - Investigate CPU Usage

Run:

```bash
top
```

Identify:

- Highest CPU process
- CPU utilisation

---

# Lab 3 - Check Memory

Run:

```bash
free -h
```

Identify:

- Available memory
- Swap usage

---

# Lab 4 - Check Disk Space

Run:

```bash
df -h
```

Identify:

- Full filesystems
- Available space

---

# Lab 5 - Check Docker Resources

If Docker is installed:

```bash
docker stats
```

Identify:

- High resource containers

---

# Lab Challenge

A Linux server has become very slow.

Initial checks show:

```text
CPU: 20%

Memory: 95%

Disk: 60%
```

Determine:

1. Which resource is most likely the issue?
2. What commands would you run next?
3. How would you identify the cause?
4. What actions could resolve the problem?

---

# Summary

In this lesson you learned:

- How to investigate performance problems
- How to analyse CPU usage
- How to troubleshoot memory issues
- How to investigate disk problems
- How to analyse processes
- How to monitor Linux systems

The next lesson covers:

```text
Lesson 05 - Troubleshooting Lab
```
