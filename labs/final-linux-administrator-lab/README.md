# Final Linux Administrator Lab

> **Estimated time:** 4–6 hours
>
> **Difficulty:** Intermediate
>
> **Prerequisites:**
> - Complete Modules 01–10
>
> **Objective:**
>
> Build, secure, troubleshoot, and document a Linux server using the skills learned throughout this training.

---

# Scenario

You have been given a new Linux server that will be used to host internal services.

Your task is to prepare the server for production use.

The server must be:

- Secure
- Properly configured
- Monitored
- Documented
- Easy to troubleshoot

---

# Lab Requirements

Complete the following tasks:

1. Initial system assessment
2. User configuration
3. Storage configuration
4. Network configuration
5. Software installation
6. Service management
7. Security hardening
8. Troubleshooting tests
9. Documentation

---
## Lab Validation Script

Once you have completed the final administrator lab, you can use the validation script to check your work.

Download the checker script:

[Download check-my-work.sh](check-my-work.sh)

Make the script executable:

```bash
chmod +x check-my-work.sh

# Task 1 - System Assessment

Collect information about the server.

Commands:

```bash
hostname

uname -a

cat /etc/os-release

uptime

df -h

free -h
```

Document:

- Hostname
- Operating system
- Kernel version
- CPU/memory resources
- Storage availability

---

# Task 2 - User Management

Create an administration user.

Requirements:

- Create a named user
- Configure sudo access
- Set a secure password
- Verify access

Commands:

```bash
sudo adduser adminuser

sudo usermod -aG sudo adminuser

id adminuser
```

---

# Task 3 - File Permissions

Create an application directory:

```bash
sudo mkdir /opt/application
```

Create a test file:

```bash
sudo touch /opt/application/config.txt
```

Configure:

- Correct ownership
- Secure permissions

Example:

```bash
sudo chown adminuser:adminuser /opt/application/config.txt

chmod 640 /opt/application/config.txt
```

Verify:

```bash
ls -l /opt/application
```

---

# Task 4 - Storage Management

Review storage:

```bash
lsblk

df -h

du -sh /*
```

Tasks:

- Identify mounted filesystems
- Identify large directories
- Check available space

---

# Task 5 - Networking

Verify network configuration.

Commands:

```bash
ip address

ip route

ss -tulnp
```

Document:

- IP address
- Default gateway
- Listening services

---

# Task 6 - Install Software

Install useful administration tools.

Example:

```bash
sudo apt update

sudo apt install htop curl wget tree
```

Verify:

```bash
htop --version

curl --version
```

---

# Task 7 - Create a Service

Install a web service:

```bash
sudo apt install nginx
```

Check:

```bash
systemctl status nginx
```

Enable startup:

```bash
sudo systemctl enable nginx
```

Test:

```bash
curl localhost
```

---

# Task 8 - Firewall Configuration

Enable firewall protection.

Example:

```bash
sudo ufw enable
```

Allow SSH:

```bash
sudo ufw allow ssh
```

Allow web traffic:

```bash
sudo ufw allow http

sudo ufw allow https
```

Check:

```bash
sudo ufw status
```

---

# Task 9 - Security Review

Complete a security review.

Check:

Users:

```bash
cat /etc/passwd
```

Permissions:

```bash
find / -type f -perm -002 2>/dev/null
```

Open ports:

```bash
ss -tulnp
```

Authentication logs:

```bash
sudo tail /var/log/auth.log
```

---

# Task 10 - Troubleshooting Exercise

The following issues have been introduced.

## Problem 1

The web service is unavailable.

Investigate:

```bash
systemctl status nginx

journalctl -u nginx
```

Restore service.

---

## Problem 2

The disk is reporting low space.

Investigate:

```bash
df -h

du -sh /*
```

Identify the cause.

---

## Problem 3

A user cannot access a file.

Investigate:

```bash
ls -l filename
```

Correct:

- Ownership
- Permissions

---

# Task 11 - Monitoring Script

Create:

```bash
nano system-check.sh
```

Create a script that displays:

- Hostname
- Disk usage
- Memory usage
- Running services
- Network ports

Example:

```bash
#!/bin/bash

echo "System Health Check"

echo "=================="

hostname

echo ""

df -h /

echo ""

free -h

echo ""

systemctl --failed

echo ""

ss -tulnp
```

Make executable:

```bash
chmod +x system-check.sh
```

Run:

```bash
./system-check.sh
```

---

# Task 12 - Documentation

Create a final report.

Document:

```text
Server Details:

Configuration Changes:

Security Improvements:

Services Installed:

Problems Found:

Solutions Applied:

Lessons Learned:
```

---

# Final Assessment

You should now be able to:

## Linux Administration

- Manage users
- Manage permissions
- Manage services
- Manage software

## Networking

- Configure networking
- Troubleshoot connectivity
- Analyse ports

## Storage

- Understand filesystems
- Investigate disk usage

## Security

- Secure accounts
- Configure firewalls
- Harden services

## Troubleshooting

- Gather evidence
- Identify root causes
- Apply fixes
- Document solutions

---

# Completion Criteria

The lab is complete when:

- The server is configured
- Services are running
- Security controls are applied
- Troubleshooting scenarios are resolved
- Documentation is completed

---

# Congratulations

You have completed:

```text
Basic Linux Training
```

You are now ready to progress into:

```text
Docker

Cloud Engineering

Kubernetes

DevOps Automation

Infrastructure as Code
```	
