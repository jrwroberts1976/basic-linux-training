# Module 00 - Introduction to Linux

## Overview

Linux is one of the most widely used operating systems in the world.

It powers:

- Web servers
- Cloud platforms
- Network devices
- Supercomputers
- Mobile devices
- Embedded systems
- Enterprise applications

This module introduces the Linux operating system, its history, common distributions, and the basic concepts required before beginning Linux administration.

---

# Learning Objectives

By the end of this module, you should understand:

- What Linux is
- How Linux differs from other operating systems
- The history of Linux
- What Linux distributions are
- The difference between Linux desktop and server environments
- Common Linux terminology
- How Linux is used in modern IT environments

---

# What is Linux?

Linux is an open-source operating system based on the Linux kernel.

An operating system provides the interface between:

```
+----------------------+
|   Applications       |
+----------------------+
|   Operating System   |
+----------------------+
|   Hardware           |
+----------------------+
```

Linux manages:

- CPU resources
- Memory
- Storage
- Network interfaces
- User accounts
- Security controls
- Running applications

---

# Linux Components

A Linux system is made up of several key components.

```
+--------------------------------+
| Applications                   |
+--------------------------------+
| Shell / Command Line           |
+--------------------------------+
| System Libraries               |
+--------------------------------+
| Linux Kernel                   |
+--------------------------------+
| Hardware                       |
+--------------------------------+
```

## Kernel

The kernel is the core of Linux.

It manages communication between software and hardware.

Examples:

- CPU scheduling
- Memory management
- Device drivers
- Network communication

Check your kernel version:

```bash
uname -r
```

Example output:

```
6.18.34+rpt-rpi-v8
```

---

# Linux History

## UNIX

Linux has its roots in UNIX.

UNIX was developed in the 1970s and introduced many concepts still used today:

- Multi-user systems
- File permissions
- Command-line administration
- Small tools working together

---

## GNU Project

The GNU project began in 1983 with the goal of creating a free UNIX-like operating system.

Many Linux systems use GNU tools, including:

- Bash
- Core utilities
- Compilers
- System libraries

---

## Linux Kernel

In 1991, Linus Torvalds created the first Linux kernel.

The project grew rapidly because:

- The source code was freely available
- Developers worldwide contributed
- Organisations adopted Linux

Today Linux is maintained by thousands of contributors.

---

# What is a Linux Distribution?

A Linux distribution combines:

- Linux kernel
- System tools
- Package manager
- Applications
- Configuration tools

into a complete operating system.

Examples:

| Distribution | Common Use |
|---|---|
| Ubuntu | Servers, cloud, desktop |
| Debian | Stable servers |
| Rocky Linux | Enterprise systems |
| Fedora | Development/testing |
| Arch Linux | Advanced users |

---

# Popular Linux Families

## Debian Family

Examples:

- Debian
- Ubuntu
- Linux Mint

Package manager:

```bash
apt
```

Example:

```bash
sudo apt update
sudo apt install nginx
```

---

## Red Hat Family

Examples:

- Red Hat Enterprise Linux
- Rocky Linux
- AlmaLinux

Package manager:

```bash
dnf
```

Example:

```bash
sudo dnf install nginx
```

---

# Linux Server vs Desktop

Linux can be used as:

## Desktop Operating System

Used for:

- Web browsing
- Office applications
- Development
- Personal computing

Examples:

- Ubuntu Desktop
- Fedora Workstation

---

## Server Operating System

Used for:

- Websites
- Databases
- Cloud workloads
- Virtualisation
- Containers

Servers often:

- Have no graphical interface
- Are managed remotely
- Run continuously
- Are automated

Example:

```
Administrator Laptop

       |
       | SSH
       |
       v

Linux Server

+----------------+
| Web Server     |
| Database       |
| Applications   |
+----------------+
```

---

# The Linux Command Line

Most Linux administration is performed using the terminal.

The command line allows administrators to:

- Manage files
- Configure systems
- Troubleshoot problems
- Automate tasks

Example:

```bash
ls
```

Lists files in a directory.

Example:

```bash
df -h
```

Shows disk usage.

Example:

```bash
systemctl status ssh
```

Checks whether the SSH service is running.

---

# Linux Users

Linux is designed as a multi-user operating system.

Every action happens as a user.

Common accounts:

## Root User

The root user is the system administrator.

Root can:

- Install software
- Change configuration
- Manage users
- Access all files

Because root has unlimited access, administrators normally use:

```bash
sudo
```

instead.

---

# Linux Filesystem Basics

Linux stores everything in a single directory structure.

Unlike Windows:

```
C:
D:
E:
```

Linux starts at:

```
/
```

Known as the root directory.

Example:

```
/
├── bin
├── etc
├── home
├── var
├── usr
└── tmp
```

Common directories:

| Directory | Purpose |
|-|-|
| /home | User files |
| /etc | Configuration |
| /var | Logs and changing data |
| /tmp | Temporary files |
| /usr | Applications |

---

# Why Linux is Important in Modern IT

Linux skills are essential because Linux runs:

## Cloud Platforms

Examples:

- AWS
- Azure
- Google Cloud

## Containers

Examples:

- Docker
- Kubernetes

## Automation

Examples:

- Ansible
- Terraform workflows

## Enterprise Systems

Examples:

- Web servers
- Databases
- Monitoring systems

---

# Practical Exercise

## Task 1 - Identify Your System

Run:

```bash
hostname
```

Record:

```
Hostname:
```

---

Run:

```bash
uname -a
```

Record:

```
Kernel:
```

---

Run:

```bash
cat /etc/os-release
```

Record:

```
Distribution:
```

---

## Task 2 - Explore the Filesystem

Run:

```bash
ls /
```

Identify:

- Where user files are stored
- Where configuration files are stored
- Where logs are stored

---

## Task 3 - Check System Resources

Run:

```bash
free -h
```

Record:

```
Memory:
```

Run:

```bash
df -h
```

Record:

```
Disk usage:
```

---

# Knowledge Check

1. What part of Linux communicates with hardware?

2. What command shows the Linux kernel version?

3. What directory contains system configuration files?

4. What is the difference between Linux and a Linux distribution?

5. Why should administrators avoid logging in directly as root?

---

# Summary

In this module you learned:

✓ Linux is an open-source operating system  
✓ The kernel manages hardware resources  
✓ Linux distributions package the kernel with tools and applications  
✓ Linux is widely used in servers and cloud platforms  
✓ Most administration is performed from the command line  
✓ Linux uses a structured filesystem and user permission model  

Next module:

**Module 01 - Command Line Fundamentals**
