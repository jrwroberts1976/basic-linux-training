# Lesson 05 - Security Hardening Lab

> **Estimated time:** 90–120 minutes
>
> **Prerequisites:**
> - Module 09 – Security
> - Lesson 01 – Linux Security Fundamentals
> - Lesson 02 – File Permissions and Ownership
> - Lesson 03 – Users, Passwords and Authentication
> - Lesson 04 – Firewalls and Network Security
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

This practical lab combines the security skills learned throughout this module.

The objective is to review and improve the security posture of a Linux system.

Security hardening involves:

- Reducing unnecessary access
- Securing authentication
- Protecting files
- Limiting network exposure
- Monitoring system activity

These tasks are common responsibilities for Linux administrators and DevOps engineers.

---

# Lab Objectives

By completing this lab you will:

- Review Linux user security
- Improve file permissions
- Harden SSH access
- Configure firewall rules
- Identify exposed services
- Review security logs
- Create a basic security checklist

---

# Lab Environment

Requirements:

- Linux system
- User with sudo privileges
- SSH access recommended

Check operating system:

```bash
cat /etc/os-release
```

Check current user:

```bash
whoami
```

---

# Lab 1 - Review User Accounts

The first step in securing a system is understanding who has access.

List users:

```bash
cat /etc/passwd
```

Review:

- Active accounts
- Unused accounts
- Service accounts

---

# Check Logged In Users

Run:

```bash
who
```

Review:

- Current sessions
- Unexpected users

---

# Review Groups

Run:

```bash
groups
```

View administrator access:

```bash
getent group sudo
```

Check who has elevated privileges.

---

# Lab 2 - Review File Permissions

Incorrect permissions can expose sensitive data.

Check important files:

```bash
ls -l /etc/passwd
```

```bash
ls -l /etc/shadow
```

Expected:

```text
/etc/shadow

Only root access
```

---

# Find World Writable Files

World writable files can be a security risk.

Run:

```bash
find / -type f -perm -002 2>/dev/null
```

Review:

- Required access
- Incorrect permissions

---

# Correcting Permissions

Example:

```bash
chmod 640 file.txt
```

Change ownership:

```bash
sudo chown root:root file.txt
```

---

# Lab 3 - Secure SSH Configuration

SSH is one of the most common attack targets.

Review configuration:

```bash
sudo nano /etc/ssh/sshd_config
```

---

# Recommended SSH Settings

Consider:

Disable root login:

```text
PermitRootLogin no
```

Disable password authentication:

```text
PasswordAuthentication no
```

Use SSH keys:

```text
PubkeyAuthentication yes
```

---

# Restart SSH

After changes:

```bash
sudo systemctl restart ssh
```

Check status:

```bash
systemctl status ssh
```

---

# Lab 4 - Review Open Ports

Identify exposed services.

Run:

```bash
ss -tulnp
```

Review:

- Listening ports
- Applications
- Required services

---

# Remove Unnecessary Services

List services:

```bash
systemctl list-units --type=service
```

Stop unused services:

```bash
sudo systemctl stop service-name
```

Disable at boot:

```bash
sudo systemctl disable service-name
```

---

# Lab 5 - Configure Firewall Protection

Check firewall:

```bash
sudo ufw status
```

Enable:

```bash
sudo ufw enable
```

---

# Allow Required Services

Example:

Allow SSH:

```bash
sudo ufw allow ssh
```

Allow web traffic:

```bash
sudo ufw allow http
```

```bash
sudo ufw allow https
```

---

# Review Firewall Rules

Run:

```bash
sudo ufw status numbered
```

Remove unnecessary rules:

```bash
sudo ufw delete rule-number
```

---

# Lab 6 - Review Authentication Logs

Security events are recorded in logs.

View authentication activity:

```bash
sudo tail /var/log/auth.log
```

Look for:

- Failed logins
- Unknown users
- SSH attempts

---

# Search Failed Login Attempts

Run:

```bash
sudo grep "Failed password" /var/log/auth.log
```

Example:

```text
Failed password for invalid user
```

---

# Lab 7 - System Updates

Keeping systems updated reduces vulnerabilities.

Update package information:

```bash
sudo apt update
```

Install updates:

```bash
sudo apt upgrade
```

---

# Lab 8 - Security Checklist Script

Create:

```bash
nano security-check.sh
```

Add:

```bash
#!/bin/bash

echo "Linux Security Check"

echo "==================="

echo ""

echo "Hostname:"
hostname

echo ""

echo "Current User:"
whoami

echo ""

echo "Listening Ports:"
ss -tulnp

echo ""

echo "Disk Usage:"
df -h /
```

Make executable:

```bash
chmod +x security-check.sh
```

Run:

```bash
./security-check.sh
```

---

# Hardening Checklist

A secure Linux server should have:

## User Security

- Remove unused accounts
- Use strong passwords
- Limit sudo access

---

## File Security

- Correct ownership
- Correct permissions
- Protect sensitive files

---

## SSH Security

- Disable root login
- Use SSH keys
- Limit access

---

## Network Security

- Firewall enabled
- Required ports only
- Unused services removed

---

## Monitoring

- Review logs
- Monitor authentication
- Monitor services

---

# Final Lab Challenge

You are given a new Linux server.

Current state:

```text
SSH allows root login

Password authentication enabled

Firewall disabled

Unused services running

Multiple unused users exist

Sensitive files have weak permissions
```

Create a hardening plan.

Your plan should include:

1. User account changes
2. SSH improvements
3. Firewall configuration
4. Permission corrections
5. Monitoring improvements

---

# Review Questions

1. Why should root SSH login be disabled?

```text
Answer:
```

2. What command shows listening network ports?

```text
Answer:
```

3. What command changes file permissions?

```text
Answer:
```

4. Why are firewalls important?

```text
Answer:
```

5. What principle limits user access?

```text
Answer:
```

---

# Summary

In this module you learned:

- Linux security fundamentals
- File permissions and ownership
- User management and authentication
- SSH security
- Firewall management
- Security hardening techniques

You have now completed:

```text
Module 09 - Security
```

Next module:

```text
Module 10 - Troubleshooting
```
