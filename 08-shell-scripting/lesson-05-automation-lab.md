# Lesson 05 - Automation Lab

> **Estimated time:** 90–120 minutes
>
> **Prerequisites:**
> - Module 08 – Shell Scripting
> - Lesson 01 – Shell Scripting Fundamentals
> - Lesson 02 – Variables and Input
> - Lesson 03 – Conditions and Loops
> - Lesson 04 – Functions and Error Handling
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

This practical lab combines the scripting skills learned throughout this module.

The objective is to create useful Bash automation scripts that can help Linux administrators perform common operational tasks.

Automation is a key skill in:

- Linux administration
- Cloud engineering
- DevOps
- Infrastructure support
- Site reliability engineering

The scripts created in this lab demonstrate real-world administration tasks.

---

# Lab Objectives

By completing this lab you will:

- Create reusable Bash automation scripts
- Collect system information
- Monitor system health
- Check services
- Monitor disk usage
- Create backup automation
- Schedule scripts using cron

---

# Lab Environment

Requirements:

- Linux system
- Bash shell
- User with sudo privileges

Check Bash version:

```bash
bash --version
```

---

# Lab 1 - System Health Check Script

Create:

```bash
nano health-check.sh
```

Add:

```bash
#!/bin/bash

echo "System Health Check"

echo "=================="

echo ""

echo "Hostname:"

hostname

echo ""

echo "Uptime:"

uptime

echo ""

echo "Disk Usage:"

df -h /

echo ""

echo "Memory Usage:"

free -h
```

Make executable:

```bash
chmod +x health-check.sh
```

Run:

```bash
./health-check.sh
```

---

# Lab 2 - Disk Monitoring Script

Create:

```bash
nano disk-check.sh
```

Add:

```bash
#!/bin/bash

THRESHOLD=80

USAGE=$(df / | tail -1 | awk '{print $5}' | sed 's/%//')

echo "Disk usage is ${USAGE}%"

if [ $USAGE -gt $THRESHOLD ]
then
    echo "WARNING: Disk usage is high"
else
    echo "Disk usage is normal"
fi
```

Run:

```bash
./disk-check.sh
```

This script:

- Checks disk usage
- Compares against a threshold
- Reports problems

---

# Lab 3 - Service Monitoring Script

Create:

```bash
nano service-check.sh
```

Add:

```bash
#!/bin/bash

SERVICE=$1

if systemctl is-active --quiet $SERVICE
then
    echo "$SERVICE is running"
else
    echo "$SERVICE is not running"
fi
```

Make executable:

```bash
chmod +x service-check.sh
```

Run:

```bash
./service-check.sh ssh
```

Example:

```text
ssh is running
```

---

# Lab 4 - Backup Script

Create:

```bash
nano backup.sh
```

Add:

```bash
#!/bin/bash

SOURCE="/etc"

DEST="/backup"

DATE=$(date +%Y%m%d)

mkdir -p $DEST

tar -czf $DEST/etc-backup-$DATE.tar.gz $SOURCE

if [ $? -eq 0 ]
then
    echo "Backup completed successfully"
else
    echo "Backup failed"
    exit 1
fi
```

Run:

```bash
./backup.sh
```

Check:

```bash
ls -lh /backup
```

---

# Lab 5 - Logging Script Output

Scripts often write information to log files.

Example:

```bash
./health-check.sh >> health.log
```

View:

```bash
cat health.log
```

Append timestamps:

```bash
date >> health.log
```

---

# Lab 6 - Scheduling Automation

Linux uses cron to schedule automated tasks.

View current cron jobs:

```bash
crontab -l
```

Edit cron jobs:

```bash
crontab -e
```

Example:

Run a health check every day at midnight:

```text
0 0 * * * /home/user/health-check.sh
```

Cron format:

```text
Minute Hour Day Month Weekday Command
```

---

# Lab 7 - Script Permissions

Check permissions:

```bash
ls -l *.sh
```

Example:

```text
-rwxr-xr-x health-check.sh
```

Scripts should have execute permission:

```bash
chmod +x script.sh
```

---

# Lab 8 - Script Validation

Before running automation scripts:

Check syntax:

```bash
bash -n script.sh
```

Run with debugging:

```bash
bash -x script.sh
```

Check exit status:

```bash
echo $?
```

---

# Automation Troubleshooting

Common problems:

---

## Script Does Not Run

Error:

```text
Permission denied
```

Solution:

```bash
chmod +x script.sh
```

---

## Command Not Found

Check command location:

```bash
which command
```

Example:

```bash
which python3
```

---

## Script Works Manually But Not in Cron

Common causes:

- Different PATH environment
- Missing absolute paths
- Permission issues

Use full paths:

Example:

```bash
/usr/bin/df
```

instead of:

```bash
df
```

---

# Final Lab Challenge

Create a script called:

```text
server-monitor.sh
```

The script should:

- Display hostname
- Display current date
- Check disk usage
- Check memory usage
- Check SSH service status
- Write output to a log file
- Return an error if a check fails

Example output:

```text
Server Monitor

Hostname:
server01

Disk:
OK

Memory:
OK

SSH:
Running
```

---

# Review Questions

Answer the following:

1. What command makes a script executable?

```text
Answer:
```

2. How do you check script syntax?

```text
Answer:
```

3. What command schedules automated tasks?

```text
Answer:
```

4. What does `$?` contain?

```text
Answer:
```

5. Why should scripts use logging?

```text
Answer:
```

---

# Summary

In this lab you practised:

- Creating automation scripts
- Monitoring Linux systems
- Checking services
- Creating backups
- Logging script output
- Scheduling automation with cron
- Troubleshooting Bash scripts

You have now completed:

```text
Module 08 - Shell Scripting
```

Next module:

```text
Module 09 - Security
```
