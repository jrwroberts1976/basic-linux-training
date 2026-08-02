# Lesson 04 - Disk Usage and Monitoring

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 07 – Storage Management
> - Lesson 01 – Storage Fundamentals
> - Lesson 02 – Partitions and Filesystems
> - Lesson 03 – Mount Points
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Monitoring storage usage is an essential task for Linux administrators.

A full filesystem can cause serious problems including:

- Applications failing
- Services stopping
- Databases becoming unavailable
- Log files failing to write
- System instability

Linux provides several tools to monitor storage usage, identify large files, and troubleshoot storage problems.

This lesson introduces disk usage commands, inode management, and storage troubleshooting techniques.

---

# Learning Objectives

By completing this lesson you will understand:

- How to check filesystem usage
- How to check directory sizes
- How to find large files
- What inodes are
- How to monitor storage growth
- How to troubleshoot full disks
- Common storage problems on Linux

---

# Checking Disk Space

The `df` command displays filesystem usage.

Example:

```bash
df -h
```

The `-h` option displays sizes in a human-readable format.

Example output:

```text
Filesystem      Size  Used Avail Use% Mounted on

/dev/sda2       100G   45G   50G  48% /
```

Information shown:

| Column | Meaning |
|---|---|
| Filesystem | Storage device |
| Size | Total capacity |
| Used | Space consumed |
| Avail | Available space |
| Use% | Percentage used |
| Mounted on | Mount location |

---

# Checking Specific Filesystems

A specific filesystem can be checked by providing the mount point.

Example:

```bash
df -h /
```

Example:

```text
Filesystem

/dev/sda2

Mounted on:

/
```

---

# Finding Large Directories

The `du` command displays directory usage.

Example:

```bash
du -h /var
```

Example output:

```text
500M    /var/log
2G      /var/lib
```

The `du` command is useful for finding where storage is being used.

---

# Summary Directory Sizes

The `-s` option displays a summary.

Example:

```bash
du -sh /var/*
```

Example:

```text
500M /var/log

2G   /var/lib

100M /var/cache
```

This helps identify large directories.

---

# Finding Large Files

Large files can consume storage quickly.

The `find` command can locate large files.

Example:

```bash
find / -type f -size +1G
```

This searches for files larger than 1GB.

Example output:

```text
/var/log/application.log
```

---

# Sorting Disk Usage

The output from `du` can be sorted.

Example:

```bash
du -sh /var/* | sort -h
```

Example:

```text
100M /var/cache

500M /var/log

2G /var/lib
```

This displays directories from smallest to largest.

---

# Log Files and Storage

Log files are a common cause of storage growth.

Common log locations:

```text
/var/log
```

Examples:

```text
/var/log/syslog

/var/log/auth.log

/var/log/journal
```

Large logs may indicate:

- Application problems
- Security events
- Misconfigured services

---

# Inodes

An inode stores information about files.

An inode contains:

- File permissions
- Ownership
- File size
- File timestamps
- File location information

Every file requires an inode.

A filesystem can run out of inodes even when free disk space exists.

---

# Checking Inode Usage

Use:

```bash
df -i
```

Example:

```text
Filesystem     Inodes  IUsed  IFree IUse%

/dev/sda2      655360 10000 645360 2%
```

The `IUse%` column shows inode usage.

---

# Common Inode Problems

A filesystem may have free space:

```text
Disk usage:

50%
```

but no available inodes:

```text
Inode usage:

100%
```

Symptoms:

- Cannot create files
- Applications fail
- Errors saying "No space left on device"

---

# Monitoring Storage Growth

Regular monitoring helps identify storage problems before failures occur.

Important metrics:

- Filesystem usage
- Available capacity
- Inode usage
- Large files
- Log growth

Example:

```bash
df -h
```

Run regularly to check storage status.

---

# Linux Storage Troubleshooting

A common troubleshooting workflow:

---

## Step 1 - Check Disk Space

```bash
df -h
```

Identify full filesystems.

---

## Step 2 - Find Large Directories

```bash
du -sh /*
```

Identify where space is being used.

---

## Step 3 - Find Large Files

```bash
find / -type f -size +1G
```

Locate large files.

---

## Step 4 - Check Logs

```bash
du -sh /var/log/*
```

Look for excessive log growth.

---

## Step 5 - Check Inodes

```bash
df -i
```

Confirm inode availability.

---

# Common Storage Problems

## Filesystem Full

Symptoms:

- Applications fail
- Cannot create files
- Services stop

Solution:

- Remove unnecessary files
- Archive old data
- Increase storage capacity

---

## Large Log Files

Symptoms:

- `/var/log` grows rapidly

Solution:

- Review logs
- Configure log rotation
- Investigate application errors

---

## Deleted Files Still Using Space

A deleted file can continue using disk space if a process still has it open.

Check:

```bash
lsof | grep deleted
```

Solution:

Restart the process holding the file.

---

# Practical Lab

The objective of this lab is to monitor storage usage and troubleshoot disk problems.

Tasks:

- Check filesystem usage
- Identify large directories
- Find large files
- Check inode usage

---

# Lab 1 - Check Disk Usage

Run:

```bash
df -h
```

Identify:

- Filesystem capacity
- Used space
- Available space

---

# Lab 2 - Find Large Directories

Run:

```bash
du -sh /*
```

Identify:

- Largest directories
- Potential storage issues

---

# Lab 3 - Check Inodes

Run:

```bash
df -i
```

Identify:

- Total inodes
- Used inodes
- Available inodes

---

# Lab Challenge

A Linux server reports:

```text
No space left on device
```

However:

```bash
df -h
```

shows:

```text
50% used
```

Explain:

1. What could cause this problem?
2. Which command would confirm the issue?
3. How would you resolve it?

---

# Summary

In this lesson you learned:

- How to monitor disk usage
- How to use `df`
- How to use `du`
- How to find large files
- What inodes are
- How to troubleshoot storage problems

The next lesson covers:

```text
Lesson 05 - Storage Lab
```
