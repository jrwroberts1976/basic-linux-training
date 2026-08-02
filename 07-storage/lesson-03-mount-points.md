# Lesson 03 - Mount Points

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 07 – Storage Management
> - Lesson 01 – Storage Fundamentals
> - Lesson 02 – Partitions and Filesystems
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

A filesystem must be attached to the Linux directory structure before it can be used.

This process is called mounting.

Mount points allow Linux administrators to connect storage devices to directories, making the data available to users and applications.

Understanding mount points is essential for managing:

- Additional disks
- Application storage
- Database storage
- Backup locations
- Cloud attached storage

This lesson introduces mounting filesystems, persistent mounts, and the `/etc/fstab` configuration file.

---

# Learning Objectives

By completing this lesson you will understand:

- What a mount point is
- How Linux mounts filesystems
- The difference between temporary and permanent mounts
- How to mount and unmount storage
- How UUIDs are used
- How `/etc/fstab` works
- How to troubleshoot mount problems

---

# What Is a Mount Point?

A mount point is a directory where a filesystem is attached.

Linux uses a single directory tree.

Unlike Windows, which uses drive letters:

```text
C:
D:
E:
```

Linux attaches storage into directories.

Example:

```text
Filesystem

/dev/sdb1

        |

        |

Mount Point

/data

        |

        |

Files

/data/application.log
```

The filesystem contents become available inside the mount point directory.

---

# Linux Directory Structure

Common mount locations include:

| Directory | Purpose |
|---|---|
| `/` | Root filesystem |
| `/home` | User data |
| `/var` | Application data and logs |
| `/opt` | Optional software |
| `/data` | Additional storage |
| `/mnt` | Temporary mounts |

---

# Viewing Mounted Filesystems

The `mount` command displays mounted filesystems.

```bash
mount
```

Example:

```text
/dev/sda2 on / type ext4

/dev/sdb1 on /data type ext4
```

This shows:

- Device name
- Mount location
- Filesystem type

---

# Using the df Command

The `df` command also shows mounted filesystems.

```bash
df -h
```

Example:

```text
Filesystem      Size  Used Avail Mounted on

/dev/sda2       100G   40G   60G /

/dev/sdb1       500G  100G  400G /data
```

---

# Creating a Mount Point

Before mounting storage, the directory must exist.

Example:

```bash
sudo mkdir /data
```

The directory can then be used as a mount point.

---

# Temporary Mounts

A filesystem can be mounted manually.

Example:

```bash
sudo mount /dev/sdb1 /data
```

This attaches:

```text
/dev/sdb1

to

/data
```

The storage is immediately available.

---

# Checking a Mount

After mounting:

```bash
df -h
```

Example:

```text
/dev/sdb1

Mounted on:

/data
```

Files can now be stored in:

```text
/data
```

---

# Unmounting Filesystems

A filesystem can be detached using `umount`.

Example:

```bash
sudo umount /data
```

The filesystem is removed from the directory tree.

Important:

A filesystem cannot usually be unmounted while it is being used.

---

# Finding What Is Using a Mount

If unmounting fails:

```bash
lsof /data
```

Example:

```text
process1

application.log

/data
```

This shows which processes are accessing the filesystem.

---

# Persistent Mounts

Manual mounts are temporary.

After a reboot:

```text
Mounted filesystem

        |

        |

System restart

        |

        |

Mount removed
```

To automatically mount storage, Linux uses:

```text
/etc/fstab
```

---

# The /etc/fstab File

The filesystem table controls automatic mounting.

View the file:

```bash
cat /etc/fstab
```

Example:

```text
UUID=1234-abcd /data ext4 defaults 0 2
```

Each field has a purpose:

| Field | Purpose |
|---|---|
| UUID | Filesystem identifier |
| Mount point | Directory location |
| Filesystem type | ext4, xfs etc |
| Options | Mount settings |
| Dump | Backup setting |
| Pass | Filesystem check order |

---

# Using UUIDs

Linux recommends using UUIDs instead of device names.

Example:

Device name:

```text
/dev/sdb1
```

UUID:

```text
UUID=7f3a9d2e-1234
```

The UUID remains consistent even if device names change.

---

# Finding UUID Values

Use:

```bash
blkid
```

Example:

```text
/dev/sdb1

UUID="7f3a9d2e-1234"

TYPE="ext4"
```

---

# Testing /etc/fstab

After editing `/etc/fstab`, test the configuration.

Run:

```bash
sudo mount -a
```

If there are no errors, the configuration is valid.

---

# Common Mount Problems

## Incorrect UUID

Symptoms:

- System fails to mount storage
- Mount errors during boot

Check:

```bash
blkid
```

Compare with:

```bash
cat /etc/fstab
```

---

## Missing Mount Directory

Example:

```text
/data
```

does not exist.

Create it:

```bash
sudo mkdir /data
```

---

## Filesystem Type Incorrect

Example:

```text
TYPE=xfs
```

but the filesystem is actually:

```text
ext4
```

Check:

```bash
blkid
```

---

## Filesystem In Use

Unmount fails because processes are using it.

Check:

```bash
lsof /data
```

---

# Practical Lab

The objective of this lab is to mount and manage storage.

Tasks:

- Create a mount point
- Mount a filesystem
- Verify the mount
- Configure persistent mounting

---

# Lab 1 - Create a Mount Point

Create a directory:

```bash
sudo mkdir /data
```

---

# Lab 2 - Mount Storage

Example:

```bash
sudo mount /dev/sdb1 /data
```

Verify:

```bash
df -h
```

---

# Lab 3 - Identify UUID

Run:

```bash
blkid
```

Record the UUID value.

---

# Lab 4 - Configure Persistent Mounting

Edit:

```bash
sudo nano /etc/fstab
```

Add:

```text
UUID=<filesystem-uuid> /data ext4 defaults 0 2
```

Test:

```bash
sudo mount -a
```

---

# Lab Challenge

A server has a new disk mounted manually at:

```text
/data
```

After reboot the directory is empty.

Explain:

1. Why did this happen?
2. Which file controls automatic mounts?
3. How would you make the mount persistent?

---

# Summary

In this lesson you learned:

- What mount points are
- How Linux attaches filesystems
- How to mount storage manually
- How to unmount filesystems
- How UUIDs identify storage
- How `/etc/fstab` provides persistent mounts
- How to troubleshoot mount problems

The next lesson covers:

```text
Lesson 04 - Disk Usage and Monitoring
```
