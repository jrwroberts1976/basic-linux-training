# Lesson 02 - Variables and Input

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 08 – Shell Scripting
> - Lesson 01 – Shell Scripting Fundamentals
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Variables allow shell scripts to store and reuse information.

Instead of hard-coding values throughout a script, variables allow administrators to create flexible and reusable automation.

Shell scripts commonly use variables for:

- File names
- User input
- System information
- Configuration values
- Command output
- Script arguments

This lesson introduces Bash variables, user input, environment variables, and command arguments.

---

# Learning Objectives

By completing this lesson you will understand:

- What variables are
- How to create and use variables
- The difference between local and environment variables
- How to accept user input
- How to use command-line arguments
- How to use special Bash variables
- How exit codes work

---

# What Is a Variable?

A variable stores information that can be used later in a script.

Example:

```bash
name="James"
```

The variable contains:

```text
Variable:

name

Value:

James
```

Variables allow scripts to reuse information.

---

# Creating Variables

Variables are created by assigning a value.

Example:

```bash
username="admin"
```

Important:

There must be no spaces around the equals sign.

Correct:

```bash
name="Linux"
```

Incorrect:

```bash
name = "Linux"
```

---

# Using Variables

Variables are accessed using the `$` symbol.

Example:

```bash
name="Linux"

echo $name
```

Output:

```text
Linux
```

---

# Script Example

Create:

```bash
nano variables.sh
```

Add:

```bash
#!/bin/bash

name="Linux Administrator"

echo "Welcome $name"
```

Run:

```bash
./variables.sh
```

Output:

```text
Welcome Linux Administrator
```

---

# Variable Naming Rules

Variable names:

- Can contain letters
- Can contain numbers
- Can contain underscores
- Cannot contain spaces
- Are case sensitive

Examples:

Valid:

```bash
username="james"

server_name="web01"
```

Invalid:

```bash
server name="web01"
```

---

# Quoting Variables

Variables can contain spaces.

Example:

```bash
message="Linux Administration Training"
```

Use quotes when assigning values containing spaces.

Example:

```bash
echo "$message"
```

---

# Environment Variables

Environment variables are available to programs running on the system.

Common environment variables:

| Variable | Purpose |
|---|---|
| `$USER` | Current user |
| `$HOME` | User home directory |
| `$PATH` | Command search path |
| `$SHELL` | Current shell |
| `$HOSTNAME` | System hostname |

Example:

```bash
echo $USER
```

Output:

```text
james
```

---

# Viewing Environment Variables

Display all environment variables:

```bash
env
```

Example:

```text
USER=james

HOME=/home/james

SHELL=/bin/bash
```

---

# Creating Environment Variables

A variable can be exported.

Example:

```bash
export APP_NAME="WebServer"
```

The variable is now available to child processes.

Check:

```bash
echo $APP_NAME
```

---

# User Input

Scripts can request information from users.

The `read` command accepts input.

Example:

```bash
read username

echo "Hello $username"
```

---

# Prompting Users

The `-p` option displays a message.

Example:

```bash
read -p "Enter your name: " username

echo "Hello $username"
```

Example:

```text
Enter your name:

James

Hello James
```

---

# Script Example Using Input

Create:

```bash
nano greeting.sh
```

Add:

```bash
#!/bin/bash

read -p "Enter your name: " name

echo "Welcome $name"
```

Run:

```bash
./greeting.sh
```

---

# Command-Line Arguments

Scripts can accept values when they are started.

Example:

```bash
./script.sh value
```

Arguments are stored in special variables.

---

# Special Argument Variables

| Variable | Meaning |
|---|---|
| `$0` | Script name |
| `$1` | First argument |
| `$2` | Second argument |
| `$3` | Third argument |
| `$#` | Number of arguments |
| `$@` | All arguments |

---

# Argument Example

Create:

```bash
nano arguments.sh
```

Add:

```bash
#!/bin/bash

echo "Script name: $0"

echo "First argument: $1"

echo "Second argument: $2"
```

Run:

```bash
./arguments.sh Linux Admin
```

Output:

```text
Script name: ./arguments.sh

First argument: Linux

Second argument: Admin
```

---

# Checking Number of Arguments

Scripts can check how many arguments were provided.

Example:

```bash
echo "Arguments supplied: $#"
```

Run:

```bash
./script.sh one two three
```

Output:

```text
Arguments supplied: 3
```

---

# Command Substitution

A variable can store command output.

Example:

```bash
hostname=$(hostname)
```

The command runs and the result is stored.

Example:

```bash
#!/bin/bash

server=$(hostname)

echo "Server: $server"
```

---

# Exit Codes

Every Linux command returns an exit code.

Success:

```text
0
```

Failure:

```text
Non-zero value
```

Example:

```bash
ls /tmp

echo $?
```

Output:

```text
0
```

---

# Creating Exit Codes

Scripts can return their own exit codes.

Example:

```bash
exit 0
```

Successful completion.

Example:

```bash
exit 1
```

Indicates an error.

---

# Practical Lab

The objective of this lab is to create scripts using variables and user input.

Tasks:

- Create variables
- Accept user input
- Use command arguments
- Check exit codes

---

# Lab 1 - Create a Variable Script

Create:

```bash
nano system-details.sh
```

Add:

```bash
#!/bin/bash

server=$(hostname)

user=$USER

echo "Server: $server"

echo "User: $user"
```

Run:

```bash
./system-details.sh
```

---

# Lab 2 - User Input

Create:

```bash
nano welcome.sh
```

Add:

```bash
#!/bin/bash

read -p "Enter your name: " name

echo "Welcome $name"
```

---

# Lab 3 - Script Arguments

Create:

```bash
nano arguments-test.sh
```

Add:

```bash
#!/bin/bash

echo "First value: $1"

echo "Second value: $2"
```

Run:

```bash
./arguments-test.sh Linux Admin
```

---

# Lab Challenge

Create a script called:

```text
server-report.sh
```

The script should:

- Accept a server name as an argument
- Display the current user
- Display the hostname
- Display disk usage
- Display memory usage

Example:

```bash
./server-report.sh web01
```

Output:

```text
Server: web01

User: james

Disk:

Memory:
```

---

# Summary

In this lesson you learned:

- How variables work in Bash
- How to store and reuse information
- How to use environment variables
- How to accept user input
- How to use command-line arguments
- How to capture command output
- How exit codes work

The next lesson covers:

```text
Lesson 03 - Conditions and Loops
```
