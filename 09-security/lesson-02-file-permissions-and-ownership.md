# Lesson 02 - File Permissions and Ownership

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 03 – Users and Groups
> - Module 09 – Security Fundamentals
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

File permissions and ownership are a core part of Linux security.

Linux controls access to files and directories by using:

- Users
- Groups
- Permissions
- Ownership

Understanding permissions allows administrators to control who can:

- Read files
- Modify files
- Execute programs
- Access directories

Incorrect permissions can create security risks, while correctly configured permissions help protect systems.

---

# Learning Objectives

By completing this lesson you will understand:

- How Linux ownership works
- How file permissions are structured
- The meaning of read, write, and execute permissions
- How to use `chmod`
- How to use `chown`
- How to use `chgrp`
- Special permissions
- Basic Access Control Lists

---

# Linux File Ownership Model

Every file and directory has:

- An owner
- A group
- Permissions

Example:

```text
-rwxr-xr-- 1 james developers script.sh
```

The file contains:

```text
Owner:

james

Group:

developers

Permissions:

-rwxr-xr--
```

---

# Viewing File Permissions

Use:

```bash
ls -l
```

Example:

```text
-rw-r--r-- 1 james james 1024 notes.txt
```

The first section shows permissions:

```text
-rw-r--r--
```

---

# Understanding Permission Fields

Example:

```text
-rwxr-xr--
```

Breakdown:

```text
-

rw-

r-x

r--
```

Meaning:

```text
File type

Owner permissions

Group permissions

Other users permissions
```

---

# File Types

The first character identifies the type.

Examples:

| Character | Meaning |
|---|---|
| `-` | Regular file |
| `d` | Directory |
| `l` | Symbolic link |

Example:

```text
drwxr-xr-x
```

The `d` means directory.

---

# Permission Types

Linux has three main permissions.

| Permission | Symbol | Meaning |
|---|---|---|
| Read | r | View contents |
| Write | w | Modify contents |
| Execute | x | Run file |

---

# File Permissions

Example:

```text
-rwxr-xr--
```

Owner:

```text
rwx
```

Can:

- Read
- Write
- Execute

Group:

```text
r-x
```

Can:

- Read
- Execute

Others:

```text
r--
```

Can:

- Read

---

# Directory Permissions

Directory permissions work differently.

## Read

Allows listing files.

Example:

```bash
ls directory
```

---

## Write

Allows creating and deleting files.

Example:

```bash
touch file.txt
```

---

## Execute

Allows entering a directory.

Example:

```bash
cd directory
```

---

# Numeric Permissions

Permissions can also be represented using numbers.

Values:

| Permission | Value |
|---|---|
| Read | 4 |
| Write | 2 |
| Execute | 1 |

---

# Calculating Permissions

Example:

```text
rwx
```

Calculation:

```text
4 + 2 + 1 = 7
```

Example:

```text
r-x
```

Calculation:

```text
4 + 1 = 5
```

Example:

```text
r--
```

Calculation:

```text
4
```

---

# Common Permission Examples

Full access:

```bash
chmod 777 file
```

Permissions:

```text
rwxrwxrwx
```

Owner full access:

```bash
chmod 700 file
```

Permissions:

```text
rwx------
```

Common script permission:

```bash
chmod 755 script.sh
```

Permissions:

```text
rwxr-xr-x
```

---

# Changing Permissions With chmod

The `chmod` command changes permissions.

Example:

```bash
chmod 644 file.txt
```

Result:

```text
Owner:

rw-

Group:

r--

Others:

r--
```

---

# Symbolic chmod

Permissions can also be changed using letters.

Add execute permission:

```bash
chmod +x script.sh
```

Remove write permission:

```bash
chmod -w file.txt
```

Add group write:

```bash
chmod g+w file.txt
```

---

# Changing Ownership With chown

The `chown` command changes file ownership.

Example:

```bash
sudo chown james file.txt
```

Change owner and group:

```bash
sudo chown james:developers file.txt
```

---

# Changing Group Ownership With chgrp

Change group ownership:

```bash
sudo chgrp developers file.txt
```

Verify:

```bash
ls -l file.txt
```

---

# Ownership Security Example

Incorrect:

```text
-rwxrwxrwx password.txt
```

Everyone can modify the file.

Better:

```text
-rw------- password.txt
```

Only the owner can access it.

---

# Special Permissions

Linux has additional permission types:

- SUID
- SGID
- Sticky bit

---

# SUID Permission

SUID allows a program to run with the owner's privileges.

Example:

```text
-rwsr-xr-x
```

The `s` replaces the execute bit.

Find SUID files:

```bash
find / -perm -4000
```

---

# SGID Permission

SGID allows files created in a directory to inherit the group.

Example:

```bash
chmod g+s directory
```

---

# Sticky Bit

The sticky bit prevents users deleting other users' files.

Common example:

```text
/tmp
```

View:

```bash
ls -ld /tmp
```

Example:

```text
drwxrwxrwt
```

The `t` represents the sticky bit.

---

# Access Control Lists (ACLs)

ACLs provide more detailed permissions.

View ACLs:

```bash
getfacl file.txt
```

Add permission:

```bash
setfacl -m u:james:rwx file.txt
```

Remove ACL:

```bash
setfacl -b file.txt
```

---

# Practical Lab

The objective of this lab is to practise Linux permissions and ownership.

Tasks:

- Create files
- View permissions
- Change permissions
- Change ownership
- Test access

---

# Lab 1 - Create Test Files

Create a directory:

```bash
mkdir security-test
```

Enter:

```bash
cd security-test
```

Create a file:

```bash
touch example.txt
```

View permissions:

```bash
ls -l
```

---

# Lab 2 - Change Permissions

Set permissions:

```bash
chmod 640 example.txt
```

Verify:

```bash
ls -l
```

Expected:

```text
-rw-r-----
```

---

# Lab 3 - Change Ownership

View current ownership:

```bash
ls -l example.txt
```

Change ownership:

```bash
sudo chown root:root example.txt
```

Verify:

```bash
ls -l example.txt
```

---

# Lab 4 - Test Directory Permissions

Create:

```bash
mkdir test-directory
```

Set permissions:

```bash
chmod 700 test-directory
```

Check:

```bash
ls -ld test-directory
```

---

# Lab Challenge

A web server administrator reports:

```text
Users can modify configuration files they should only read.
```

Investigate:

- File ownership
- File permissions
- Group membership

Suggest a secure permission model.

Consider:

- Who needs access?
- Who should only read?
- Who should not access the files?

---

# Summary

In this lesson you learned:

- How Linux permissions work
- How ownership controls access
- How to use `chmod`
- How to use `chown`
- How to use `chgrp`
- How special permissions work
- How ACLs provide additional control

The next lesson covers:

```text
Lesson 03 - Users, Passwords and Authentication
```
