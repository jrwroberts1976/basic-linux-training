# Module 09 - Security

> **Estimated time:** 6–10 hours
>
> **Prerequisites:**
> - Module 03 – Users and Groups
> - Module 04 – Processes and Services
> - Module 06 – Networking Fundamentals
> - Module 08 – Shell Scripting
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Security is a fundamental responsibility for Linux administrators, cloud engineers, and DevOps professionals.

Linux systems are commonly used for servers, cloud platforms, containers, and enterprise infrastructure.

Understanding Linux security allows administrators to:

- Protect systems from unauthorised access
- Control user permissions
- Secure network services
- Harden server configurations
- Monitor security events
- Reduce operational risks

This module introduces the core security concepts required to administer and maintain secure Linux systems.

---

# Learning Objectives

By completing this module you will understand:

- Linux security principles
- The importance of least privilege
- Users and groups security
- File permissions and ownership
- Authentication methods
- sudo access
- SSH security
- Firewall configuration
- Basic Linux hardening techniques

---

# Module Contents

## Lesson 01 - Linux Security Fundamentals

Topics covered:

- Security principles
- Threats and vulnerabilities
- Defence in depth
- Least privilege
- Linux security model
- Security best practices

---

## Lesson 02 - File Permissions and Ownership

Topics covered:

- Linux ownership model
- Users and groups
- File permissions
- chmod
- chown
- chgrp
- Special permissions
- Access Control Lists

---

## Lesson 03 - Users, Passwords and Authentication

Topics covered:

- Creating and managing users
- Password policies
- sudo administration
- Authentication methods
- SSH keys
- PAM fundamentals

---

## Lesson 04 - Firewalls and Network Security

Topics covered:

- Firewall concepts
- Network exposure
- ufw
- nftables
- Service filtering
- Port security
- Basic network protection

---

## Lesson 05 - Security Hardening Lab

Practical exercises:

- Review system security
- Harden user access
- Secure SSH configuration
- Configure firewall rules
- Audit permissions
- Apply security improvements

---

# Key Security Commands

| Command | Purpose |
|---|---|
| `id` | Display user identity |
| `whoami` | Show current user |
| `sudo` | Run commands with elevated privileges |
| `chmod` | Change permissions |
| `chown` | Change ownership |
| `passwd` | Manage passwords |
| `ssh` | Remote secure access |
| `ufw` | Manage firewall rules |
| `ss` | View network connections |
| `journalctl` | View system logs |

---

# Linux Security Model

Linux security is based on:

```text
Users

    |

Groups

    |

Permissions

    |

Processes

    |

Resources
```

Access is controlled by:

- Identity
- Permissions
- Authentication
- Authorisation

---

# Security Principles

Important security principles include:

## Least Privilege

Users and applications should only receive the access required to perform their tasks.

Example:

```text
Web Server

Needs:

Read website files

Does not need:

Administrator access
```

---

## Defence in Depth

Multiple security controls should be used together.

Example:

```text
Firewall

    +

Strong Authentication

    +

Permissions

    +

Monitoring
```

---

## Reduce Attack Surface

Only required services should be running.

Example:

```text
Disable:

Unused services

Unused ports

Unused accounts
```

---

# Practical Skills Developed

After completing this module you should be able to:

- Manage Linux permissions securely
- Control user access
- Configure basic firewall protection
- Secure remote access
- Identify common security issues
- Apply Linux hardening techniques

---

# Module Status

⏳ Complete
