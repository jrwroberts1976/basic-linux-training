# Lesson 03 - Conditions and Loops

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 08 – Shell Scripting
> - Lesson 01 – Shell Scripting Fundamentals
> - Lesson 02 – Variables and Input
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Conditions and loops allow shell scripts to make decisions and repeat tasks.

Without conditions, scripts execute commands in a fixed order.

With conditions and loops, scripts can:

- Check system states
- Respond to errors
- Process multiple files
- Monitor services
- Perform repeated tasks

These features are essential for writing useful automation scripts.

---

# Learning Objectives

By completing this lesson you will understand:

- How conditional statements work
- How to use `if` statements
- How to compare values
- How to test files and directories
- How to use `case` statements
- How to create loops
- How to process multiple items automatically

---

# Conditional Logic

Conditional statements allow scripts to make decisions.

Example:

```text
IF something is true

    Do this

ELSE

    Do something else
```

Example:

```bash
if disk space is low

then

send an alert
```

---

# The if Statement

Basic syntax:

```bash
if [ condition ]
then
    command
fi
```

Example:

```bash
#!/bin/bash

if [ "$USER" = "root" ]
then
    echo "Running as root"
fi
```

---

# Adding else

The `else` statement runs when the condition is false.

Example:

```bash
#!/bin/bash

if [ "$USER" = "root" ]
then
    echo "Administrator account"
else
    echo "Standard user"
fi
```

---

# Adding elif

Multiple conditions can be checked using `elif`.

Example:

```bash
#!/bin/bash

if [ "$USER" = "root" ]
then
    echo "Root user"

elif [ "$USER" = "admin" ]
then
    echo "Administrator"

else
    echo "Normal user"

fi
```

---

# Comparison Operators

Bash provides operators for comparing values.

## String Comparisons

| Operator | Meaning |
|---|---|
| `=` | Equal |
| `!=` | Not equal |
| `-z` | Empty string |
| `-n` | Not empty |

Example:

```bash
if [ "$name" = "James" ]
then
    echo "Welcome James"
fi
```

---

# Number Comparisons

| Operator | Meaning |
|---|---|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-lt` | Less than |
| `-ge` | Greater or equal |
| `-le` | Less or equal |

Example:

```bash
if [ $age -ge 18 ]
then
    echo "Adult"
fi
```

---

# File Tests

Scripts often need to check whether files exist.

Common tests:

| Test | Purpose |
|---|---|
| `-f` | File exists |
| `-d` | Directory exists |
| `-r` | File readable |
| `-w` | File writable |
| `-x` | File executable |

Example:

```bash
if [ -f "/etc/passwd" ]
then
    echo "File exists"
fi
```

---

# Checking Disk Space Example

Example:

```bash
#!/bin/bash

usage=$(df / | tail -1 | awk '{print $5}' | sed 's/%//')

if [ $usage -gt 80 ]
then
    echo "Disk usage is high"
else
    echo "Disk usage is OK"
fi
```

This checks whether the root filesystem is above 80%.

---

# The case Statement

`case` is useful when checking multiple possible values.

Syntax:

```bash
case value in

option1)
    command
    ;;

option2)
    command
    ;;

esac
```

---

# Case Example

Example:

```bash
#!/bin/bash

case $1 in

start)
    echo "Starting service"
    ;;

stop)
    echo "Stopping service"
    ;;

restart)
    echo "Restarting service"
    ;;

*)
    echo "Unknown option"
    ;;

esac
```

Run:

```bash
./service.sh start
```

Output:

```text
Starting service
```

---

# Loops

Loops repeat commands automatically.

Common Bash loops:

- `for`
- `while`
- `until`

---

# The for Loop

A `for` loop processes a list of items.

Example:

```bash
for item in one two three
do
    echo $item
done
```

Output:

```text
one

two

three
```

---

# Processing Files With for

Example:

```bash
for file in /var/log/*
do
    echo $file
done
```

This displays every file in `/var/log`.

---

# The while Loop

A `while` loop continues while a condition is true.

Syntax:

```bash
while [ condition ]
do
    command
done
```

Example:

```bash
count=1

while [ $count -le 5 ]
do
    echo $count
    count=$((count+1))
done
```

Output:

```text
1

2

3

4

5
```

---

# Loop Control

Loops can be controlled using:

## break

Stops a loop.

Example:

```bash
break
```

---

## continue

Skips to the next iteration.

Example:

```bash
continue
```

---

# Practical Lab

The objective of this lab is to create scripts using conditions and loops.

Tasks:

- Create conditional checks
- Test files
- Use loops
- Process multiple values

---

# Lab 1 - User Check Script

Create:

```bash
nano user-check.sh
```

Add:

```bash
#!/bin/bash

if [ "$USER" = "root" ]
then
    echo "You are root"
else
    echo "You are not root"
fi
```

Run:

```bash
./user-check.sh
```

---

# Lab 2 - File Check Script

Create:

```bash
nano file-check.sh
```

Add:

```bash
#!/bin/bash

if [ -f "/etc/passwd" ]
then
    echo "Password file exists"
else
    echo "File missing"
fi
```

---

# Lab 3 - Loop Practice

Create:

```bash
nano loop-test.sh
```

Add:

```bash
#!/bin/bash

for number in 1 2 3 4 5
do
    echo "Number: $number"
done
```

---

# Lab Challenge

Create a script called:

```text
service-check.sh
```

The script should:

- Accept a service name as an argument
- Check whether the service exists
- Display whether it is running

Example:

```bash
./service-check.sh ssh
```

Useful commands:

```bash
systemctl status

systemctl is-active
```

---

# Summary

In this lesson you learned:

- How conditional statements work
- How to use `if`, `elif`, and `else`
- How to compare values
- How to test files
- How to use `case`
- How to create loops
- How to automate repeated tasks

The next lesson covers:

```text
Lesson 04 - Functions and Error Handling
```
