# Module 07 - Storage Management

> **Estimated time:** 4–6 hours
>
> **Prerequisites:**
> - Module 01 – Command Line Fundamentals
> - Module 02 – Filesystem Fundamentals
> - Module 06 – Networking Fundamentals
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Storage management is a fundamental skill for Linux administrators.

Linux systems rely on storage for:

- Operating system files
- Application data
- User data
- Logs
- Databases
- Virtual machines
- Container workloads

Understanding how Linux manages storage allows administrators to:

- Identify disks and devices
- Create and manage partitions
- Understand filesystems
- Mount storage devices
- Monitor disk usage
- Troubleshoot storage problems

This module introduces the core storage concepts required for Linux administration, cloud platforms, and DevOps environments.

---

# Learning Objectives

By completing this module you will understand:

- How Linux represents storage devices
- The difference between disks and partitions
- How filesystems work
- The purpose of mount points
- How to view disk usage
- How to create and manage filesystems
- How Linux mounts storage automatically
- How to troubleshoot common storage issues

---

# Module Contents

## Lesson 01 - Storage Fundamentals

Topics covered:

- Storage concepts
- Block devices
- Linux storage layout
- Disk types
- HDD vs SSD
- `/dev` device files
- Identifying storage devices

---

## Lesson 02 - Partitions and Filesystems

Topics covered:

- Disk partitions
- Partition tables
- MBR and GPT
- Creating partitions
- Filesystem types
- ext4 filesystem
- Formatting storage

---

## Lesson 03 - Mount Points

Topics covered:

- What mount points are
- Mounting filesystems
- Temporary mounts
- Persistent mounts
- `/etc/fstab`
- UUIDs

---

## Lesson 04 - Disk Usage and Monitoring

Topics covered:

- Checking disk space
- Finding large files
- Inode usage
- Storage monitoring
- Troubleshooting full disks

---

## Lesson 05 - Storage Lab

Practical exercises:

- Identify storage devices
- Create partitions
- Create filesystems
- Mount storage
- Configure persistent mounts
- Troubleshoot storage problems

---

# Key Linux Storage Commands

| Command | Purpose |
|---|---|
| `lsblk` | List block devices |
| `blkid` | Display filesystem information |
| `fdisk` | Manage partitions |
| `parted` | Partition management |
| `mkfs` | Create filesystems |
| `mount` | Mount filesystems |
| `umount` | Unmount filesystems |
| `df` | Display filesystem usage |
| `du` | Display directory usage |
| `find` | Search for files |

---

# Storage Concepts

Linux storage is built from several layers:

```text
Physical Disk

      |

Partition

      |

Filesystem

      |

Mount Point

      |

Files and Directories
```

Understanding these layers is essential for managing Linux systems.

---

# Practical Skills Developed

After completing this module you should be able to:

- Inspect Linux storage devices
- Understand disk layouts
- Create and manage filesystems
- Mount storage correctly
- Monitor disk capacity
- Diagnose storage issues

---

# Module Status

⏳ Complete
