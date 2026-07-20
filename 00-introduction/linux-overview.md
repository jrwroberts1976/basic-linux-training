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

## Learning Objectives

By the end of this module, you should understand:

- What Linux is
- How Linux differs from other operating systems
- The history of Linux
- What Linux distributions are
- The difference between Linux desktop and server environments
- Common Linux terminology
- How Linux is used in modern IT environments
- How to access a Linux system

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
|-|-|
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

Examples:

List files:

```bash
ls
```

Show disk usage:

```bash
df -h
```

Check a service:

```bash
systemctl status ssh
```

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

# Logging Into Linux

Before administering a Linux system, you need to access the system.

Linux systems can be accessed using:

- Local console login
- Remote SSH login
- Virtual machine console
- Cloud console access

---

## Local Console Login

A local login is performed directly on the Linux machine.

Example:

```
login:
password:
```

You provide:

- Username
- Password

After successful authentication, you are presented with a shell.

Example:

```
james@linux-server:~$
```

The prompt provides useful information:

```
username@hostname:directory
```

Example:

```
james@k3s-node-01:~$
```

| Component | Meaning |
|-|-|
| james | Logged-in user |
| k3s-node-01 | System hostname |
| ~ | Current home directory |

---

## Remote Login Using SSH

Most Linux servers are managed remotely using SSH.

SSH (Secure Shell) provides an encrypted connection to another Linux system.

The basic format:

```bash
ssh username@hostname
```

Example:

```bash
ssh james@server01
```

Using an IP address:

```bash
ssh james@192.168.1.50
```

---

## First SSH Connection

The first time you connect to a new server, you may see:

```
The authenticity of host 'server01' can't be established.

Are you sure you want to continue connecting?
```

Type:

```
yes
```

The server identity is then saved locally.

---

## Understanding the Linux Prompt

Example:

```bash
james@server01:~$
```

The format is:

```
user@hostname:location
```

Example:

```bash
james@server01:/etc$
```

Means:

- User: james
- Hostname: server01
- Current directory: /etc

---

## Checking Your Current User

Use:

```bash
whoami
```

Example:

```
james
```

---

## Checking Logged In Users

Linux allows multiple users to be logged in.

Use:

```bash
who
```

Example:

```
james    pts/0    09:15
admin    pts/1    09:20
```

---

## Logging Out

End your session:

```bash
exit
```

or:

```
CTRL + D
```

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

5. What command is used to connect remotely to a Linux server?

6. What command shows your current username?

7. Why should administrators avoid logging in directly as root?

---

# Summary

In this module you learned:

✓ Linux is an open-source operating system  
✓ The kernel manages hardware resources  
✓ Linux distributions package the kernel with tools and applications  
✓ Linux is widely used in servers and cloud platforms  
✓ Most administration is performed from the command line  
✓ Linux supports secure remote administration using SSH  
✓ Linux uses a structured filesystem and user permission model  

Next module:

**Module 01 - Command Line Fundamentals**
