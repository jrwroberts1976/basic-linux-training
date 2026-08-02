# Lesson 01 - Linux Security Fundamentals

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 03 – Users and Groups
> - Module 04 – Processes and Services
> - Module 06 – Networking Fundamentals
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Security is a fundamental part of Linux administration.

Linux systems are widely used for:

- Servers
- Cloud platforms
- Containers
- Enterprise infrastructure
- Network services

A Linux administrator must understand how to protect systems from unauthorised access, reduce risks, and maintain secure configurations.

This lesson introduces the core security concepts required before learning permissions, authentication, firewalls, and system hardening.

---

# Learning Objectives

By completing this lesson you will understand:

- What Linux security means
- Common security threats
- The difference between authentication and authorisation
- The principle of least privilege
- Defence in depth
- The Linux security model
- Basic security best practices

---

# What Is Linux Security?

Linux security is the process of protecting a Linux system from:

- Unauthorised access
- Data loss
- Malware
- Misconfiguration
- Service vulnerabilities
- Network attacks

Security involves protecting:

```text
Users

    |

Applications

    |

Services

    |

Data

    |

Operating System
```

---

# Why Linux Security Matters

Linux is commonly used for critical systems.

Examples:

- Web servers
- Database servers
- Cloud infrastructure
- Container platforms
- Network appliances

A compromised Linux system can result in:

- Data exposure
- Service disruption
- Unauthorised access
- Loss of availability

---

# Common Security Threats

Linux systems can be affected by many types of threats.

---

## Weak Passwords

Weak passwords can allow attackers to gain access.

Examples:

Bad:

```text
password123
```

Better:

```text
A long unique password
```

Best:

```text
SSH key authentication
```

---

## Unpatched Software

Software vulnerabilities can be exploited.

Example:

```text
Old package

    |

Known vulnerability

    |

Possible attack
```

Keeping systems updated reduces risk.

---

## Excessive Permissions

Users should not have unnecessary access.

Example:

Incorrect:

```text
Everyone can modify system files
```

Correct:

```text
Only administrators can modify system files
```

---

## Unnecessary Services

Every running service increases the attack surface.

Example:

```text
Running service

        |

Open port

        |

Potential attack point
```

Remove or disable services that are not required.

---

# Authentication vs Authorisation

These two concepts are important in security.

---

# Authentication

Authentication answers:

```text
Who are you?
```

Examples:

- Password
- SSH key
- Multi-factor authentication

Example:

```text
User enters password

        |

System verifies identity
```

---

# Authorisation

Authorisation answers:

```text
What are you allowed to do?
```

Examples:

- Read files
- Modify files
- Run administrative commands

Example:

```text
Authenticated user

        |

Permission check

        |

Access granted or denied
```

---

# Linux Security Model

Linux uses several layers to control access.

```text
User Identity

        |

Groups

        |

File Permissions

        |

Process Permissions

        |

System Resources
```

Security decisions are based on:

- User ID
- Group ID
- Permissions
- Privileges

---

# Users and Security

Every Linux process runs as a user.

Check your current user:

```bash
whoami
```

Example:

```text
james
```

Display identity information:

```bash
id
```

Example:

```text
uid=1000(james)

gid=1000(james)
```

---

# The Root User

The root user has full system privileges.

Example:

```text
root

UID:

0
```

Root can:

- Modify system files
- Install software
- Change permissions
- Control services

Because of this, root access should be carefully controlled.

---

# Least Privilege

Least privilege means users and applications should only have the access they need.

Example:

A web server needs:

```text
Read website files
```

It does not need:

```text
Full administrator access
```

---

# Benefits of Least Privilege

Least privilege:

- Reduces security risks
- Limits damage from mistakes
- Limits attacker access
- Improves accountability

---

# Defence in Depth

Defence in depth means using multiple security controls.

Example:

```text
Firewall

    +

Strong Authentication

    +

File Permissions

    +

Updates

    +

Monitoring
```

If one control fails, other controls still provide protection.

---

# Reducing Attack Surface

The attack surface is the number of possible entry points into a system.

Reduce attack surface by:

- Removing unused software
- Disabling unused services
- Closing unnecessary ports
- Removing unused accounts
- Applying updates

---

# Checking Running Services

View active services:

```bash
systemctl list-units --type=service
```

Check network services:

```bash
ss -tulnp
```

Identify:

- Listening ports
- Running applications
- Exposed services

---

# Security Updates

Keeping packages updated is an important security practice.

Debian/Ubuntu example:

```bash
sudo apt update
```

Upgrade packages:

```bash
sudo apt upgrade
```

---

# Security Logs

Linux records important system events.

View system logs:

```bash
journalctl
```

View recent events:

```bash
journalctl -xe
```

Logs can help identify:

- Failed logins
- Service failures
- Security events

---

# Practical Lab

The objective of this lab is to review basic Linux security information.

Tasks:

- Identify users
- Review running services
- Check network exposure
- Review system logs

---

# Lab 1 - Check Current User

Run:

```bash
whoami
```

Identify:

- Current username

---

# Lab 2 - View User Identity

Run:

```bash
id
```

Identify:

- User ID
- Group ID
- Group memberships

---

# Lab 3 - Review Running Services

Run:

```bash
systemctl list-units --type=service
```

Identify:

- Active services
- Services that are required

---

# Lab 4 - Review Open Ports

Run:

```bash
ss -tulnp
```

Identify:

- Listening ports
- Applications using those ports

---

# Lab Challenge

A Linux server has the following issues:

```text
- Root login enabled over SSH
- Unused services running
- Weak user passwords
- Open ports that are not required
```

Describe the security improvements you would make.

Consider:

- User access
- Authentication
- Services
- Network security
- Monitoring

---

# Summary

In this lesson you learned:

- What Linux security is
- Common security threats
- The difference between authentication and authorisation
- The principle of least privilege
- Defence in depth
- How Linux controls access
- Basic security checks

The next lesson covers:

```text
Lesson 02 - File Permissions and Ownership
```
