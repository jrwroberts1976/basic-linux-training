# Linux Training Plan

## Overview

The **Basic Linux Training** course provides a structured introduction to Linux system administration.

The course is designed to build practical Linux skills through:

- Theory and concepts
- Command examples
- Practical exercises
- Knowledge checks
- Hands-on labs

Each module builds on the previous module, gradually introducing the skills required to support and administer Linux systems.

---

# Learning Path

## Module 00 - Introduction to Linux

### Topics Covered

- What is Linux?
- Linux history
- UNIX and GNU foundations
- Linux distributions
- Linux server vs desktop environments
- Common Linux environments
- Accessing Linux systems
- Linux terminology

### Practical Exercises

- Identify Linux distribution
- Check kernel version
- Explore system information
- Identify Linux environment

### Status

✅ Complete

---

# Module 01 - Command Line Fundamentals

## Lessons

| Lesson | Topic | Status |
|---|---|---|
| 01 | Linux Shell and Navigation | ✅ Complete |
| 02 | Working with Files and Directories | ✅ Complete |
| 03 | Viewing Files and Getting Help | ✅ Complete |
| 04 | Practical Command Line Lab | ✅ Complete |

---

## Topics Covered

### Linux Shell

Topics:

- Understanding Linux shell
- Bash
- Command structure
- Linux command prompt
- Running commands

Common commands:

```bash
echo
pwd
ls
cd
```

---

### Files and Directories

Topics:

- Creating directories
- Creating files
- Copying files
- Moving files
- Removing files safely
- Using wildcards

Common commands:

```bash
mkdir
touch
cp
mv
rm
rmdir
```

---

### Viewing Files and Getting Help

Topics:

- Viewing file contents
- Reviewing system information
- Finding command documentation
- Using manual pages
- Understanding command locations

Common commands:

```bash
cat
less
head
tail
man
history
which
whatis
```

---

### Practical Command Line Lab

The module concludes with practical exercises covering:

- Directory creation
- File management
- Viewing files
- Searching documentation
- Using command history
- Basic administration tasks

### Status

✅ Complete

---

# Module 02 - Linux Filesystem Administration

## Lessons

| Lesson | Topic | Status |
|---|---|---|
| 01 | Linux Filesystem Hierarchy | ✅ Complete |
| 02 | File Permissions and Ownership | ✅ Complete |
| 03 | Finding Files and Links | ✅ Complete |
| 04 | Filesystem Administration Lab | ✅ Complete |

---

## Topics Covered

### Linux Filesystem

Topics:

- Linux filesystem structure
- Root filesystem (`/`)
- Standard directories
- File locations
- Navigation techniques

Example structure:

```text
/
├── bin
├── etc
├── home
├── var
├── usr
└── tmp
```

---

### File Ownership and Permissions

Topics:

- Users and groups
- File ownership
- Permission model
- Read, write and execute permissions
- Changing ownership
- Changing permissions

Commands:

```bash
ls -l
chmod
chown
chgrp
```

---

### Finding Files and Links

Topics:

- Searching the filesystem
- Finding files
- Symbolic links
- Hard links

Commands:

```bash
find
locate
ln
```

---

### Filesystem Administration Lab

Practical exercises:

- Create directory structures
- Review ownership
- Modify permissions
- Locate files
- Create links
- Troubleshoot access issues

### Status

✅ Complete

---
# Module 03 - Users and Groups

## Topics Covered

- User accounts
- Groups
- Password management
- sudo
- Administrative access

## Lessons

| Lesson | Topic | Status |
|---|---|---|
| 01 | Understanding Users and Groups | ✅ Complete |
| 02 | Managing Users and Groups | ☐ Planned |
| 03 | Passwords and sudo | ☐ Planned |
| 04 | Users and Groups Administration Lab | ☐ Planned |

### Status

✅ Complete

---

# Module 04 - Processes and Services

## Topics Covered

- Linux processes
- Background services
- systemd
- Service management
- Log analysis

## Lessons

| Lesson | Topic | Status |
|---|---|---|
| 01 | Understanding Processes | ✅ Complete |
| 02 | Managing Processes | ✅ Complete |
| 03 | systemd and Service Management | ✅ Complete |
| 04 | Logs and journalctl | ✅ Complete |
| 05 | Processes and Services Lab | ✅ Complete |

### Status

✅ Complete

---

# Module 05 - Package Management

## Topics Covered

- Package managers
- Software repositories
- Installing software
- Updating systems

Platforms:

- Debian / Ubuntu (APT)
- Red Hat / Rocky Linux (DNF)

## Lessons

| Lesson | Topic | Status |
|---|---|---|
| 01 | Understanding Linux Package Managers | ✅ Complete |
| 02 | Installing Software Packages | ✅ Complete |
| 03 | Updating Linux Systems | ✅ Complete |
| 04 | Software Repositories | ✅ Complete |
| 05 | Package Management Administration Lab | ✅ Complete |

### Status

✅ Complete

---

# Module 06 - Networking

## Lessons

| Lesson | Topic | Status |
|---|---|---|
| 01 | Networking Fundamentals | ✅ Complete |
| 02 | IP Addressing and Subnetting | ✅ Complete |
| 03 | Network Troubleshooting | ✅ Complete |
| 04 | Networking Administration Lab | ✅ Complete |

---

## Topics Covered

### Networking Fundamentals

Topics:

- Network communication
- Network interfaces
- MAC addresses
- IP addresses
- TCP and UDP
- Ports and services

---

### IP Addressing and Subnetting

Topics:

- IPv4 addressing
- Private and public addresses
- Static and dynamic addressing
- Subnet masks
- CIDR notation
- Network addresses
- Broadcast addresses
- Default gateways

---

### Network Troubleshooting

Topics:

- Troubleshooting methodology
- Checking interfaces
- Testing connectivity
- Routing investigation
- DNS troubleshooting
- Service validation
- Firewall investigation

---

### Networking Administration Lab

Practical exercises:

- Review Linux network configuration
- Identify network interfaces
- Analyse IP addressing
- Test connectivity
- Troubleshoot DNS
- Check network services
- Document findings

### Status

✅ Complete

---

# Module 07 - Storage Management

## Topics Covered

- Disks
- Partitions
- Filesystems
- Mount points
- Disk usage

### Status

☐ Planned

---

# Module 08 - Bash Scripting

## Topics Covered

- Shell scripts
- Variables
- Conditions
- Loops
- Automation

### Status

☐ Planned

---

# Module 09 - Linux Security

## Topics Covered

- SSH security
- User permissions
- Firewalls
- Updates
- Logging

### Status

☐ Planned

---

# Module 10 - Troubleshooting

## Topics Covered

Common Linux issues:

- High CPU usage
- Memory problems
- Disk space issues
- Service failures
- Network problems

Troubleshooting approach:

1. Identify symptoms
2. Gather information
3. Check logs
4. Test possible causes
5. Apply fixes
6. Document resolution

### Status

☐ Planned

---

# Final Linux Administration Lab

Participants will complete a practical administration challenge.

Tasks may include:

- Deploying a Linux system
- Creating users
- Installing applications
- Configuring services
- Securing the system
- Troubleshooting issues

### Status

☐ Planned

---

# Recommended Training Environment

The course can be completed using:

- Virtual machines
- Raspberry Pi
- Cloud virtual machines
- Windows Subsystem for Linux (WSL)
- Physical Linux systems

Recommended distributions:

- Ubuntu Server LTS
- Debian
- Rocky Linux

---

# Progress Tracking

| Module | Status |
|---|---|
| Module 00 - Introduction to Linux | ✅ Complete |
| Module 01 - Command Line Fundamentals | ✅ Complete |
| Module 02 - Linux Filesystem Administration | ✅ Complete |
| Module 03 - Users and Groups | ✅ Complete |
| Module 04 - Processes and Services | ✅ Complete |
| Module 05 - Package Management | ✅ Complete |
| Module 06 - Networking | ✅ Complete |
| Module 07 - Storage Management | ☐ Planned |
| Module 08 - Bash Scripting | ☐ Planned |
| Module 09 - Linux Security | ☐ Planned |
| Module 10 - Troubleshooting | ☐ Planned |
| Final Linux Administration Lab | ☐ Planned |
