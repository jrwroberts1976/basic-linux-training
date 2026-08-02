# Lesson 02 - Partitions and Filesystems

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 07 – Storage Management
> - Lesson 01 – Storage Fundamentals
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Partitions and filesystems are essential parts of Linux storage management.

A disk provides physical storage, but before Linux can store files on that disk it normally requires:

- A partition layout
- A filesystem
- A mount point

Understanding partitions and filesystems allows administrators to prepare new storage devices, manage server storage, and troubleshoot storage issues.

This lesson introduces partition tables, partition management, filesystem types, and creating filesystems on Linux.

---

# Learning Objectives

By completing this lesson you will understand:

- What disk partitions are
- The difference between MBR and GPT partition tables
- How Linux identifies partitions
- Common Linux filesystem types
- How to create filesystems
- How to inspect filesystem information
- How to safely prepare storage devices

---

# What Is a Partition?

A partition is a logical section of a physical storage device.

A single disk can contain multiple partitions.

Example:

```text
Physical Disk

/dev/sda

        |
        |

+----------------+
| /dev/sda1      |
| Operating      |
| System         |
+----------------+

+----------------+
| /dev/sda2      |
| Data           |
+----------------+
```

Partitions allow administrators to separate different types of data.

Common uses:

- Operating system files
- User data
- Application storage
- Database storage
- Swap space

---

# Partition Tables

Before partitions can be created, a disk requires a partition table.

The partition table stores information about:

- Partition locations
- Partition sizes
- Partition types

The two common partition table formats are:

- MBR
- GPT

---

# MBR Partition Table

MBR stands for Master Boot Record.

MBR is an older partitioning system.

Limitations:

- Maximum disk size around 2 TB
- Maximum of four primary partitions

Example:

```text
/dev/sda

MBR

 |
 |
 +-- Partition 1
 |
 +-- Partition 2
 |
 +-- Partition 3
 |
 +-- Partition 4
```

MBR is still supported but is less common on modern systems.

---

# GPT Partition Table

GPT stands for GUID Partition Table.

GPT is the modern replacement for MBR.

Advantages:

- Supports very large disks
- Supports many partitions
- More reliable partition information
- Works with modern UEFI systems

Example:

```text
/dev/nvme0n1

GPT

 |
 |
 +-- Partition 1
 |
 +-- Partition 2
 |
 +-- Partition 3
```

Modern Linux installations normally use GPT.

---

# Viewing Partition Information

Linux provides several commands to inspect disks and partitions.

---

# lsblk

The `lsblk` command displays block devices.

```bash
lsblk
```

Example:

```text
NAME        SIZE TYPE
sda         100G disk
├─sda1       20G part
└─sda2       80G part
```

This shows:

- Disk name
- Partition names
- Sizes
- Device types

---

# fdisk

The `fdisk` command manages disk partitions.

Display partition information:

```bash
sudo fdisk -l
```

Example:

```text
Disk /dev/sda: 100 GiB

Device      Size
/dev/sda1   20G
/dev/sda2   80G
```

---

# Creating Partitions

The `fdisk` utility can create partitions.

Example:

```bash
sudo fdisk /dev/sdb
```

Common options inside `fdisk`:

| Option | Purpose |
|---|---|
| `n` | Create new partition |
| `d` | Delete partition |
| `p` | Display partition table |
| `w` | Write changes |
| `q` | Quit without saving |

Example workflow:

```text
Open disk

Create partition

Review changes

Write changes
```

---

# Filesystems

A filesystem controls how data is stored and organised on a disk.

Without a filesystem, Linux cannot store normal files and directories.

A filesystem provides:

- File organisation
- Permissions
- Metadata
- Storage allocation

Example:

```text
Disk

 |

Partition

 |

Filesystem

 |

Files and Directories
```

---

# Common Linux Filesystems

## ext4

ext4 is the most common Linux filesystem.

Features:

- Reliable
- Good performance
- Supports large files
- Widely supported

Example:

```text
/dev/sda1

Filesystem:

ext4
```

---

## XFS

XFS is commonly used in enterprise environments.

Features:

- High performance
- Good for large filesystems
- Common on servers

Example uses:

- Database servers
- Large storage systems

---

## Btrfs

Btrfs is a modern filesystem with advanced features.

Features:

- Snapshots
- Compression
- Storage management features

---

# Creating a Filesystem

The `mkfs` command creates a filesystem.

Example:

```bash
sudo mkfs.ext4 /dev/sdb1
```

This creates an ext4 filesystem on the partition.

Warning:

Creating a filesystem will erase existing data.

---

# Checking Filesystem Information

The `blkid` command displays filesystem information.

```bash
blkid
```

Example:

```text
/dev/sdb1

UUID="abcd-1234"

TYPE="ext4"
```

Information displayed:

- Device name
- UUID
- Filesystem type

---

# UUIDs

A UUID is a unique identifier assigned to a filesystem.

Example:

```text
UUID="7f3a9d2e-1234"
```

Linux uses UUIDs because device names can change.

Example:

```text
/dev/sda1
```

could become:

```text
/dev/sdb1
```

The UUID remains the same.

UUIDs are commonly used in:

- `/etc/fstab`
- Automated mounts
- Server configurations

---

# Filesystem Check

Linux provides tools to check filesystem health.

For ext filesystems:

```bash
sudo fsck /dev/sdb1
```

`fsck` checks and repairs filesystem problems.

Important:

Do not run filesystem repairs on mounted filesystems.

---

# Practical Lab

The objective of this lab is to understand partitions and filesystems.

Tasks:

- Identify disks
- View partitions
- Identify filesystem types
- Create a test filesystem

---

# Lab 1 - Identify Storage Devices

Run:

```bash
lsblk
```

Identify:

- Disk devices
- Existing partitions
- Storage sizes

---

# Lab 2 - View Partition Information

Run:

```bash
sudo fdisk -l
```

Identify:

- Partition table type
- Partition layout
- Device names

---

# Lab 3 - View Filesystem Information

Run:

```bash
blkid
```

Identify:

- Filesystem type
- UUID values

---

# Lab Challenge

A new 100GB disk has been added to a Linux server.

The administrator needs to prepare it for application data.

Describe the required steps:

1. Identify the new disk
2. Create a partition
3. Create a filesystem
4. Mount the storage
5. Configure automatic mounting

---

# Summary

In this lesson you learned:

- What disk partitions are
- The difference between MBR and GPT
- How Linux identifies partitions
- What filesystems do
- Common Linux filesystem types
- How to create filesystems
- How UUIDs identify storage

The next lesson covers:

```text
Lesson 03 - Mount Points
```
