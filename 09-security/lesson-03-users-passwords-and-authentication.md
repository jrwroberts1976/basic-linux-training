# Lesson 03 - Users, Passwords and Authentication

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 03 – Users and Groups
> - Module 09 – Security Fundamentals
> - Lesson 02 – File Permissions and Ownership
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

User management and authentication are important parts of Linux security.

Linux systems rely on user accounts to control access to:

- Files
- Services
- Applications
- System resources

Secure authentication ensures that only authorised users can access systems.

This lesson covers Linux users, passwords, sudo access, SSH authentication, and basic authentication security.

---

# Learning Objectives

By completing this lesson you will understand:

- How Linux user accounts work
- How passwords are managed
- How to create and remove users
- How sudo provides administrative access
- How SSH authentication works
- The role of SSH keys
- Basic authentication security practices

---

# Linux User Accounts

Every user on a Linux system has an identity.

User information includes:

- Username
- User ID (UID)
- Group ID (GID)
- Home directory
- Default shell

View your identity:

```bash
id
```

Example:

```text
uid=1000(james)

gid=1000(james)
```

---

# User Database

Linux stores user account information in:

```text
/etc/passwd
```

View:

```bash
cat /etc/passwd
```

Example:

```text
james:x:1000:1000:James:/home/james:/bin/bash
```

Fields include:

```text
Username

Password location

UID

GID

Home directory

Login shell
```

---

# Password Storage

Passwords are not stored in plain text.

Encrypted password information is stored in:

```text
/etc/shadow
```

This file is protected.

View:

```bash
sudo cat /etc/shadow
```

Only administrators should have access.

---

# Creating Users

Create a user:

```bash
sudo useradd username
```

A more complete command:

```bash
sudo adduser username
```

Example:

```bash
sudo adduser developer
```

This creates:

- User account
- Home directory
- Password prompt

---

# Removing Users

Remove a user:

```bash
sudo userdel username
```

Remove user and home directory:

```bash
sudo userdel -r username
```

Example:

```bash
sudo userdel -r developer
```

---

# Changing Passwords

Change your own password:

```bash
passwd
```

Change another user's password:

```bash
sudo passwd username
```

Example:

```bash
sudo passwd developer
```

---

# Password Security

Good password practices:

- Use long passwords
- Avoid reused passwords
- Use password managers
- Enable multi-factor authentication where possible
- Prefer SSH keys for remote access

Avoid:

```text
password

welcome123

admin123
```

---

# User Groups

Groups allow administrators to manage permissions for multiple users.

View groups:

```bash
groups
```

Example:

```text
james sudo docker
```

A user can belong to multiple groups.

---

# Adding Users to Groups

Add a user to a group:

```bash
sudo usermod -aG group username
```

Example:

```bash
sudo usermod -aG sudo developer
```

Verify:

```bash
groups developer
```

---

# The sudo Command

`sudo` allows users to run commands with elevated privileges.

Example:

```bash
sudo systemctl restart ssh
```

The command runs with administrator privileges.

---

# Why Use sudo?

Using sudo is safer than logging in directly as root.

Benefits:

- Accountability
- Logging
- Reduced risk
- Controlled access

Example:

Incorrect:

```text
Everyone uses root
```

Better:

```text
Users have limited access

+

sudo when required
```

---

# The sudo Configuration

The sudo configuration is stored in:

```text
/etc/sudoers
```

Edit safely using:

```bash
sudo visudo
```

This checks for syntax errors before saving.

---

# SSH Authentication

SSH provides secure remote access to Linux systems.

Example:

```bash
ssh user@server
```

Authentication can use:

- Passwords
- SSH keys

---

# Password Authentication

Traditional SSH login:

```text
Username

+

Password

|

Access granted
```

While convenient, passwords can be attacked using:

- Brute force
- Password guessing
- Credential reuse

---

# SSH Key Authentication

SSH keys use cryptographic authentication.

The key pair contains:

```text
Private Key

+

Public Key
```

The private key stays on the client.

The public key is copied to the server.

---

# Generating SSH Keys

Create a key pair:

```bash
ssh-keygen
```

Example:

```text
~/.ssh/id_rsa

~/.ssh/id_rsa.pub
```

---

# Installing SSH Keys

Copy the public key:

```bash
ssh-copy-id user@server
```

After setup:

```bash
ssh user@server
```

The system authenticates using the key.

---

# SSH Security Best Practices

Recommended:

- Use SSH keys
- Disable root login
- Disable password authentication where appropriate
- Use firewall restrictions
- Monitor login attempts

---

# Checking Login History

View successful logins:

```bash
last
```

View failed login attempts:

```bash
sudo lastb
```

---

# Authentication Logs

Linux records authentication events.

View logs:

```bash
journalctl
```

Search SSH events:

```bash
journalctl | grep ssh
```

On Debian systems:

```bash
sudo tail /var/log/auth.log
```

---

# Account Security Checks

Check logged-in users:

```bash
who
```

Check recent activity:

```bash
last
```

Find users:

```bash
cat /etc/passwd
```

Review unnecessary accounts.

---

# Practical Lab

The objective of this lab is to practise user management and authentication.

Tasks:

- Create users
- Manage passwords
- Configure sudo access
- Review SSH settings
- Check authentication logs

---

# Lab 1 - Create a User

Create:

```bash
sudo adduser testuser
```

Verify:

```bash
id testuser
```

---

# Lab 2 - Add User to sudo Group

Run:

```bash
sudo usermod -aG sudo testuser
```

Verify:

```bash
groups testuser
```

---

# Lab 3 - Review Authentication Logs

Run:

```bash
sudo tail /var/log/auth.log
```

Identify:

- Successful logins
- Failed attempts
- SSH activity

---

# Lab 4 - Generate SSH Keys

Create a key:

```bash
ssh-keygen
```

Review:

```bash
ls -la ~/.ssh
```

---

# Lab Challenge

A company has a Linux server with the following issues:

```text
- Multiple users share the root password
- SSH allows root login
- Password authentication is enabled
- Old user accounts remain active
```

Describe the security improvements required.

Consider:

- User accounts
- sudo access
- SSH configuration
- Authentication methods
- Account cleanup

---

# Summary

In this lesson you learned:

- How Linux user accounts work
- How passwords are managed
- How sudo provides controlled administration
- How SSH authentication works
- How SSH keys improve security
- How to review authentication activity

The next lesson covers:

```text
Lesson 04 - Firewalls and Network Security
```
