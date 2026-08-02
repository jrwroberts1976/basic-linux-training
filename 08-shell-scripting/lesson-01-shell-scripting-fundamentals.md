# Lesson 01 - Shell Scripting Fundamentals

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 01 – Command Line Fundamentals
> - Module 04 – Processes and Services
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Shell scripting allows Linux administrators to automate tasks by combining commands into reusable programs.

Instead of manually running the same commands repeatedly, administrators can create scripts that perform tasks automatically.

Common uses of shell scripts include:

- System administration
- Backups
- Monitoring
- Software installation
- User management
- Log processing
- Server maintenance

This lesson introduces the fundamentals of Bash scripting and how Linux executes shell scripts.

---

# Learning Objectives

By completing this lesson you will understand:

- What shell scripting is
- The purpose of Bash
- How to create a shell script
- The shebang line
- How to execute scripts
- File permissions
- Basic script commands
- How to troubleshoot simple scripts

---

# What Is Shell Scripting?

A shell script is a text file containing Linux commands that are executed in sequence.

Example:

```text
Script

   |

Linux Commands

   |

Automated Task
```

A script allows administrators to turn manual tasks into repeatable automation.

Example tasks:

Manual:

```bash
df -h
systemctl status ssh
journalctl -xe
```

Automated:

```bash
./health-check.sh
```

---

# What Is Bash?

Bash stands for:

```text
Bourne Again Shell
```

Bash is one of the most common Linux shells.

A shell provides an interface between:

```text
User

 |

Shell

 |

Linux Kernel

 |

Hardware
```

Common Linux shells:

| Shell | Description |
|---|---|
| bash | Default Linux shell |
| sh | Bourne shell |
| zsh | Extended interactive shell |
| fish | User-friendly shell |

---

# Checking Your Current Shell

The current shell can be checked using:

```bash
echo $SHELL
```

Example:

```text
/bin/bash
```

The current running shell can be checked with:

```bash
echo $0
```

---

# Creating Your First Script

Create a file:

```bash
nano hello.sh
```

Add:

```bash
#!/bin/bash

echo "Hello Linux"
```

Save the file.

---

# The Shebang Line

The first line of a script is called the shebang.

Example:

```bash
#!/bin/bash
```

It tells Linux which interpreter should execute the script.

Other examples:

```bash
#!/bin/sh
```

or:

```bash
#!/usr/bin/python3
```

---

# Making a Script Executable

A new script is not automatically executable.

Check permissions:

```bash
ls -l hello.sh
```

Example:

```text
-rw-r--r-- hello.sh
```

Add execute permission:

```bash
chmod +x hello.sh
```

Check again:

```bash
ls -l hello.sh
```

Example:

```text
-rwxr-xr-x hello.sh
```

The `x` permission allows execution.

---

# Running a Script

There are several ways to run a script.

## Method 1 - Execute Directly

```bash
./hello.sh
```

Output:

```text
Hello Linux
```

---

## Method 2 - Run Using Bash

```bash
bash hello.sh
```

This does not require execute permission.

---

# Script Output

The `echo` command displays text.

Example:

```bash
echo "Linux Administration"
```

Output:

```text
Linux Administration
```

Scripts often use `echo` to provide information to users.

Example:

```bash
echo "Checking disk usage"

df -h
```

---

# Comments in Scripts

Comments explain what a script does.

Comments start with:

```bash
#
```

Example:

```bash
#!/bin/bash

# Display system information

hostname
```

Comments are ignored by the shell.

---

# Running Linux Commands in Scripts

Any normal Linux command can usually be used inside a script.

Example:

```bash
#!/bin/bash

hostname

uptime

df -h
```

When executed:

```bash
./system-info.sh
```

the commands run in order.

---

# Script Execution Flow

A script executes from top to bottom.

Example:

```bash
#!/bin/bash

echo "Starting"

date

echo "Finished"
```

Output:

```text
Starting

Sun Aug 02 10:00:00 UTC 2026

Finished
```

---

# Exit Codes

Linux commands return an exit status.

A successful command returns:

```text
0
```

A failed command returns a non-zero value.

Example:

```bash
ls /tmp
```

Check the exit code:

```bash
echo $?
```

Example:

```text
0
```

---

# Basic Script Example

Example:

```bash
#!/bin/bash

echo "System Information"

hostname

uptime

df -h
```

This script:

- Displays a heading
- Shows the hostname
- Shows system uptime
- Shows disk usage

---

# Troubleshooting Scripts

Common problems:

---

## Permission Denied

Example:

```text
bash: ./script.sh: Permission denied
```

Solution:

```bash
chmod +x script.sh
```

---

## Wrong Interpreter

Example:

```text
bad interpreter
```

Check:

```bash
head -1 script.sh
```

Confirm:

```bash
#!/bin/bash
```

---

## Syntax Errors

Run:

```bash
bash -n script.sh
```

This checks syntax without running the script.

---

# Practical Lab

The objective of this lab is to create and execute basic Bash scripts.

Tasks:

- Create a script
- Add commands
- Make it executable
- Run the script
- Troubleshoot errors

---

# Lab 1 - Create a Script

Create:

```bash
nano system-info.sh
```

Add:

```bash
#!/bin/bash

echo "System Information"

hostname

uptime

df -h
```

---

# Lab 2 - Make Executable

Run:

```bash
chmod +x system-info.sh
```

---

# Lab 3 - Execute Script

Run:

```bash
./system-info.sh
```

Verify:

- Hostname is displayed
- Uptime is displayed
- Disk usage is displayed

---

# Lab 4 - Check Script Syntax

Run:

```bash
bash -n system-info.sh
```

No output means no syntax errors.

---

# Lab Challenge

Create a script called:

```text
server-summary.sh
```

The script should display:

- Hostname
- Current date
- Current user
- Disk usage
- Memory usage

Example commands:

```bash
hostname

date

whoami

df -h

free -h
```

---

# Summary

In this lesson you learned:

- What shell scripting is
- How Bash works
- How to create scripts
- The purpose of the shebang line
- How to execute scripts
- How permissions affect execution
- How to troubleshoot basic script problems

The next lesson covers:

```text
Lesson 02 - Variables and Input
```
