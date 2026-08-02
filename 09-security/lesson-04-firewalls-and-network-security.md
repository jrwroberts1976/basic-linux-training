# Lesson 04 - Firewalls and Network Security

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 06 – Networking Fundamentals
> - Module 09 – Security Fundamentals
> - Lesson 03 – Users, Passwords and Authentication
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Network security is an important part of Linux administration.

Linux servers often provide network services such as:

- Web applications
- Databases
- SSH access
- Monitoring platforms
- Container services

Every exposed service creates a potential entry point.

Firewalls help administrators control network access by deciding which traffic is allowed or blocked.

This lesson introduces firewall concepts, Linux firewall tools, and basic network security practices.

---

# Learning Objectives

By completing this lesson you will understand:

- What a firewall is
- How network traffic is controlled
- The difference between inbound and outbound traffic
- Ports and services
- Linux firewall tools
- How to use UFW
- Basic nftables concepts
- How to reduce network exposure

---

# What Is a Firewall?

A firewall is a security control that filters network traffic.

It decides whether traffic should be:

- Allowed
- Blocked
- Logged

Example:

```text
Internet

    |

 Firewall

    |

 Linux Server
```

---

# Why Firewalls Matter

Without a firewall:

```text
Internet

    |

All Services Exposed
```

With a firewall:

```text
Internet

    |

Firewall Rules

    |

Only Required Services Accessible
```

---

# Network Traffic Direction

Traffic has two main directions.

---

# Incoming Traffic

Traffic coming into a system.

Examples:

```text
User connecting to SSH

Web request to server

Database connection
```

---

# Outgoing Traffic

Traffic leaving a system.

Examples:

```text
Server downloading updates

Application connecting to an API

DNS queries
```

---

# Ports and Services

Network services listen on ports.

Example:

```text
192.168.1.50:22
```

Means:

```text
IP Address:

192.168.1.50

Port:

22
```

Common ports:

| Port | Service | Purpose |
|---|---|---|
| 22 | SSH | Remote administration |
| 53 | DNS | Name resolution |
| 80 | HTTP | Web traffic |
| 443 | HTTPS | Secure web traffic |
| 3306 | MySQL | Database |
| 5432 | PostgreSQL | Database |

---

# Firewall Principle

A good firewall follows:

```text
Allow required traffic

Block everything else
```

Example:

A web server may allow:

```text
80/tcp

443/tcp

22/tcp
```

But block:

```text
Unused ports
```

---

# Linux Firewall Options

Common Linux firewall tools:

- UFW
- nftables
- iptables

Modern Linux distributions use:

```text
nftables
```

as the underlying firewall framework.

---

# Checking Firewall Status

On systems using UFW:

```bash
sudo ufw status
```

Example:

```text
Status: active
```

---

# UFW Firewall

UFW stands for:

```text
Uncomplicated Firewall
```

It provides a simpler interface for managing firewall rules.

---

# Enable UFW

Enable firewall:

```bash
sudo ufw enable
```

Check:

```bash
sudo ufw status
```

---

# Disable UFW

Disable firewall:

```bash
sudo ufw disable
```

---

# Allowing Services

Allow SSH:

```bash
sudo ufw allow ssh
```

Allow a port:

```bash
sudo ufw allow 8080/tcp
```

---

# Blocking Services

Block a port:

```bash
sudo ufw deny 3306/tcp
```

---

# Removing Rules

View numbered rules:

```bash
sudo ufw status numbered
```

Delete a rule:

```bash
sudo ufw delete 1
```

---

# UFW Example Configuration

A basic server firewall:

```text
Allow SSH

Allow HTTP

Allow HTTPS

Deny everything else
```

Commands:

```bash
sudo ufw allow ssh

sudo ufw allow http

sudo ufw allow https
```

---

# nftables

nftables is the modern Linux firewall framework.

It replaces older iptables configurations.

View rules:

```bash
sudo nft list ruleset
```

Example structure:

```text
Table

    |

Chain

    |

Rules
```

---

# nftables Concepts

Important components:

## Tables

Contain firewall rules.

Example:

```text
inet filter
```

---

## Chains

Process traffic.

Examples:

```text
input

output

forward
```

---

## Rules

Define actions.

Example:

```text
Allow SSH traffic
```

---

# Checking Open Ports

Before securing a server, identify exposed services.

Use:

```bash
ss -tulnp
```

Example:

```text
LISTEN

0.0.0.0:22

0.0.0.0:80
```

---

# Reducing Network Exposure

Security improvements:

- Remove unused services
- Close unnecessary ports
- Restrict access by IP
- Use encryption
- Monitor network activity

Example:

Before:

```text
20 open ports
```

After:

```text
5 required ports
```

---

# Firewall and Containers

Containers can expose services to the network.

Example:

Docker:

```bash
docker ps
```

Shows:

```text
0.0.0.0:8080->80
```

This means:

```text
Host port 8080

|

Container port 80
```

Always review exposed container ports.

---

# Firewall Logging

Logs help identify blocked traffic.

View system logs:

```bash
journalctl
```

For UFW:

```bash
sudo journalctl -k | grep UFW
```

---

# Security Monitoring

Firewall monitoring can identify:

- Port scans
- Failed connections
- Suspicious traffic
- Attack attempts

Useful tools:

- journalctl
- fail2ban
- CrowdSec
- SIEM platforms

---

# Practical Lab

The objective of this lab is to practise basic firewall management.

Tasks:

- Check firewall status
- Allow services
- Review ports
- Identify exposed services

---

# Lab 1 - Check Open Ports

Run:

```bash
ss -tulnp
```

Identify:

- Listening ports
- Running services

---

# Lab 2 - Check UFW Status

Run:

```bash
sudo ufw status
```

---

# Lab 3 - Allow SSH

Run:

```bash
sudo ufw allow ssh
```

Verify:

```bash
sudo ufw status
```

---

# Lab 4 - Review nftables

Run:

```bash
sudo nft list ruleset
```

Identify:

- Tables
- Chains
- Rules

---

# Lab Challenge

A Linux server is running:

```text
SSH

Web server

Database

Unused test application
```

The server is accessible from the internet.

Describe the security improvements required.

Consider:

- Firewall rules
- Open ports
- Service removal
- Access restrictions
- Monitoring

---

# Summary

In this lesson you learned:

- What firewalls do
- How network traffic is controlled
- How ports relate to services
- How to manage UFW rules
- Basic nftables concepts
- How to reduce network exposure
- How to review network security

The next lesson covers:

```text
Lesson 05 - Security Hardening Lab
```
