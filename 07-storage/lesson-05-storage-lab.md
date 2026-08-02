# Lesson 05 - Storage Lab

> **Estimated time:** 90–120 minutes
>
> **Prerequisites:**
> - Module 07 – Storage Management
> - Lesson 01 – Storage Fundamentals
> - Lesson 02 – Partitions and Filesystems
> - Lesson 03 – Mount Points
> - Lesson 04 – Disk Usage and Monitoring
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

This practical lab combines the storage concepts covered throughout this module.

The objective is to safely identify storage devices, create partitions, create filesystems, mount storage, and monitor disk usage.

Storage management is a critical Linux administration skill used in:

- Servers
- Cloud environments
- Virtual machines
- Containers
- Database systems

---

# Lab Objectives

By completing this lab you will:

- Identify storage devices
- Inspect existing disk layouts
- Create a partition
- Create a filesystem
- Mount storage
- Configure persistent mounting
- Verify storage usage
- Troubleshoot storage problems

---

# Lab Environment

This lab requires:

- A Linux system
- A test disk or virtual disk
- Administrator privileges

Example test device:

```text
/dev/sdb
```

Warning:

Do not use a production disk.

The commands in this lab may erase data on the selected device.

---

# Lab 1 - Identify Storage Devices

Before modifying storage, identify available disks.

Run:

```bash
lsblk
```

Example:

```text
NAME        SIZE TYPE

sda         100G disk
├─sda1       1G part
└─sda2      99G part

sdb          50G disk
```

Identify:

- Existing system disk
- New storage disk
- Available capacity

---

# Lab 2 - Inspect Disk Information

Display detailed partition information.

Run:

```bash
sudo fdisk -l
```

Identify:

- Disk device name
- Disk size
- Partition table type

Example:

```text
Disk /dev/sdb: 50 GiB

Partition table:

gpt
```

---

# Lab 3 - Create a Partition

Open the disk using `fdisk`.

Example:

```bash
sudo fdisk /dev/sdb
```

Inside `fdisk`:

Create a new partition:

```text
n
```

Display the partition table:

```text
p
```

Write changes:

```text
w
```

The new partition should appear:

```text
/dev/sdb1
```

Verify:

```bash
lsblk
```

---

# Lab 4 - Create a Filesystem

Create an ext4 filesystem.

Example:

```bash
sudo mkfs.ext4 /dev/sdb1
```

Example output:

```text
Creating filesystem with blocks

Filesystem UUID:

abcd-1234
```

The partition is now ready to store files.

---

# Lab 5 - Create a Mount Point

Create a directory for the storage.

Example:

```bash
sudo mkdir /data
```

This directory will become the mount point.

---

# Lab 6 - Mount the Filesystem

Mount the new filesystem.

Example:

```bash
sudo mount /dev/sdb1 /data
```

Verify:

```bash
df -h
```

Example:

```text
Filesystem

/dev/sdb1

Mounted on

/data
```

---

# Lab 7 - Test Storage

Create a test file.

```bash
sudo touch /data/test-file.txt
```

Check:

```bash
ls -la /data
```

Expected:

```text
test-file.txt
```

---

# Lab 8 - Find the Filesystem UUID

Display filesystem information.

Run:

```bash
blkid
```

Example:

```text
/dev/sdb1

UUID="abcd-1234"

TYPE="ext4"
```

Record the UUID.

---

# Lab 9 - Configure Persistent Mounting

Edit:

```bash
sudo nano /etc/fstab
```

Add:

```text
UUID=abcd-1234 /data ext4 defaults 0 2
```

Save the file.

Test:

```bash
sudo mount -a
```

If no errors appear, the configuration is valid.

---

# Lab 10 - Check Storage Usage

View filesystem usage.

Run:

```bash
df -h
```

Check:

- Total size
- Used space
- Available space

---

# Lab 11 - Monitor Directory Usage

Check directory sizes.

Run:

```bash
du -sh /data
```

Example:

```text
4.0K /data
```

---

# Storage Troubleshooting Exercise

A server administrator receives this alert:

```text
No space left on device
```

The administrator runs:

```bash
df -h
```

and sees:

```text
Filesystem

/dev/sda2

Use%

95%
```

---

## Troubleshooting Steps

Check filesystem usage:

```bash
df -h
```

Find large directories:

```bash
du -sh /*
```

Find large files:

```bash
find / -type f -size +1G
```

Check logs:

```bash
du -sh /var/log/*
```

Check inodes:

```bash
df -i
```

---

# Lab Challenge

A new disk has been added to a Linux server.

The requirements are:

- Create a partition
- Format it as ext4
- Mount it at `/data`
- Ensure it survives reboot

Describe the complete process:

1. Identify the disk
2. Create the partition
3. Create the filesystem
4. Create the mount point
5. Mount the filesystem
6. Find the UUID
7. Configure `/etc/fstab`
8. Test the configuration

---

# Review Questions

Answer the following:

1. What command lists block devices?

```text
Answer:
```

2. What command creates an ext4 filesystem?

```text
Answer:
```

3. Where are persistent mounts configured?

```text
Answer:
```

4. Why are UUIDs preferred over device names?

```text
Answer:
```

5. What command checks filesystem usage?

```text
Answer:
```

---

# Summary

In this lab you practised:

- Identifying storage devices
- Managing partitions
- Creating filesystems
- Mounting storage
- Configuring persistent mounts
- Monitoring disk usage
- Troubleshooting storage problems

You have now completed the Linux Storage Management module.

Next module:

```text
Module 08 - Shell Scripting
```
