# Lesson 01 - Storage Fundamentals

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 01 – Command Line Fundamentals
> - Module 02 – Filesystem Fundamentals
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Storage management is a fundamental skill for Linux administrators.

Every Linux system requires storage to hold:

- The operating system
- Applications
- Configuration files
- User data
- Logs
- Databases
- Container data

Understanding how Linux manages storage allows administrators to identify disks, understand storage layouts, and troubleshoot storage problems.

This lesson introduces the basic concepts of Linux storage, including disks, block devices, partitions, and storage layouts.

---

# Learning Objectives

By completing this lesson you will understand:

- What storage devices are
- How Linux represents storage devices
- The difference between disks and partitions
- What block devices are
- The purpose of `/dev`
- Common storage technologies
- The difference between HDD and SSD storage
- How to identify storage devices on Linux

---

# What Is Storage?

Storage is hardware or software used to save data permanently.

Unlike memory (RAM), storage retains data when the system is powered off.

Examples of storage devices:

- Hard disk drives (HDD)
- Solid state drives (SSD)
- USB drives
- Network storage
- Cloud storage

A Linux server may use storage for:

- The operating system
- Application data
- Databases
- Virtual machines
- Container images

---

# Storage Devices in Linux

Linux represents storage devices as files inside the `/dev` directory.

The `/dev` directory contains device files that represent hardware.

Example:

```text
/dev/sda
```

This usually represents the first disk detected by Linux.

Other examples:

```text
/dev/sdb
/dev/nvme0n1
/dev/mmcblk0
```

---

# Common Linux Storage Device Names

## SATA and SCSI Devices

Traditional disks are usually named:

```text
/dev/sda
/dev/sdb
/dev/sdc
```

Example:

```text
/dev/sda

First disk in the system
```

Partitions are numbered:

```text
/dev/sda1
/dev/sda2
/dev/sda3
```

Example:

```text
/dev/sda

    |
    |
    +-- /dev/sda1
    |
    +-- /dev/sda2
```

---

## NVMe Devices

Modern SSDs often use NVMe naming.

Example:

```text
/dev/nvme0n1
```

Partitions are shown as:

```text
/dev/nvme0n1p1
/dev/nvme0n1p2
```

Example:

```text
/dev/nvme0n1

        |
        |

/dev/nvme0n1p1

        |

/dev/nvme0n1p2
```

---

# Block Devices

Linux storage devices are usually block devices.

A block device stores and retrieves data in fixed-size blocks.

Examples:

- Hard drives
- SSDs
- USB storage devices
- Virtual disks

Linux identifies block devices using the `lsblk` command.

Example:

```bash
lsblk
```

Example output:

```text
NAME        SIZE TYPE
sda         100G disk
├─sda1       1G part
└─sda2      99G part
```

This shows:

- Physical disk
- Partitions
- Storage sizes

---

# Disks and Partitions

A disk is the physical storage device.

A partition is a logical section of a disk.

Example:

```text
Physical Disk

/dev/sda

        |
        |

Partitions

/dev/sda1
/dev/sda2
/dev/sda3
```

Partitions allow a single disk to be divided into separate areas.

Common uses:

- Separate operating system files
- Separate user data
- Separate application storage

---

# Disk Types

## Hard Disk Drive (HDD)

HDDs use spinning magnetic disks.

Advantages:

- Low cost
- Large capacities
- Good for bulk storage

Disadvantages:

- Slower performance
- Moving parts
- Higher power usage

Common uses:

- File servers
- Backup storage
- Archives

---

## Solid State Drive (SSD)

SSDs use flash memory.

Advantages:

- Faster performance
- No moving parts
- Lower power usage

Disadvantages:

- Higher cost per GB
- Limited write endurance

Common uses:

- Operating systems
- Databases
- Virtual machines
- Cloud servers

---

# Local Storage Layout

A typical Linux system may look like:

```text
Disk

/dev/sda

 |

Partitions

 |

Filesystem

 |

Directories

 |
 
/data
/home
/var
```

The filesystem provides the structure used to store files and directories.

---

# Viewing Storage Devices on Linux

Linux provides several commands to inspect storage.

---

# List Block Devices

The `lsblk` command displays disks and partitions.

```bash
lsblk
```

Example:

```text
NAME        SIZE TYPE
nvme0n1     500G disk
├─nvme0n1p1 512M part
└─nvme0n1p2 499G part
```

---

# Display Disk Information

The `fdisk` command can display partition information.

```bash
sudo fdisk -l
```

Example:

```text
Disk /dev/sda: 100 GiB
```

---

# Display Filesystem Information

The `blkid` command shows filesystem details.

```bash
blkid
```

Example:

```text
/dev/sda1: UUID="1234-abcd" TYPE="ext4"
```

---

# Storage Information Workflow

A common administrator workflow:

## Step 1 - Identify Disks

```bash
lsblk
```

---

## Step 2 - Check Partitions

```bash
sudo fdisk -l
```

---

## Step 3 - Identify Filesystems

```bash
blkid
```

---

## Step 4 - Check Usage

```bash
df -h
```

---

# Practical Lab

The objective of this lab is to identify storage devices on a Linux system.

Tasks:

- Identify disks
- Identify partitions
- Identify filesystems
- Check storage usage

---

# Lab 1 - List Storage Devices

Run:

```bash
lsblk
```

Identify:

- Disk names
- Partition names
- Disk sizes

---

# Lab 2 - Display Disk Information

Run:

```bash
sudo fdisk -l
```

Identify:

- Disk devices
- Partition layout
- Disk size

---

# Lab 3 - Identify Filesystems

Run:

```bash
blkid
```

Identify:

- Filesystem type
- UUID values

---

# Lab 4 - Check Disk Usage

Run:

```bash
df -h
```

Identify:

- Mounted filesystems
- Available space
- Used space

---

# Lab Challenge

A Linux server reports that a new disk has been added.

The administrator needs to answer:

1. What device name was assigned to the disk?
2. Does the disk contain partitions?
3. Does it have a filesystem?
4. Is it currently mounted?

Describe the commands you would use.

---

# Summary

In this lesson you learned:

- What storage is
- How Linux represents storage devices
- The difference between disks and partitions
- What block devices are
- How `/dev` represents hardware
- The difference between HDD and SSD storage
- How to identify storage devices using Linux commands

The next lesson covers:

```text
Lesson 02 - Partitions and Filesystems
```
