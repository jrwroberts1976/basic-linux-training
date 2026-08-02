# Lesson 04 - Functions and Error Handling

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 08 – Shell Scripting
> - Lesson 01 – Shell Scripting Fundamentals
> - Lesson 02 – Variables and Input
> - Lesson 03 – Conditions and Loops
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Functions and error handling allow shell scripts to become more organised, reliable, and easier to maintain.

As scripts become larger, repeating the same commands makes them harder to manage.

Functions allow administrators to create reusable sections of code.

Error handling allows scripts to detect problems and respond appropriately.

These concepts are important when creating automation used in:

- System administration
- Monitoring
- Backups
- Deployment tasks
- Maintenance scripts

---

# Learning Objectives

By completing this lesson you will understand:

- What functions are
- How to create reusable code
- How to pass arguments to functions
- How to return values
- How to handle command failures
- How to use exit codes
- How to debug shell scripts
- How to create reliable automation

---

# What Is a Function?

A function is a reusable block of code.

Instead of writing the same commands multiple times, a function can be called whenever required.

Example:

```text
Function

    |

Reusable Commands

    |

Called Multiple Times
```

---

# Creating a Function

Basic syntax:

```bash
function_name()
{
    commands
}
```

Example:

```bash
#!/bin/bash

hello()
{
    echo "Hello Linux"
}

hello
```

Output:

```text
Hello Linux
```

---

# Function Example

Create:

```bash
nano functions.sh
```

Add:

```bash
#!/bin/bash

show_date()
{
    date
}

show_date
```

Run:

```bash
./functions.sh
```

The function executes the `date` command.

---

# Passing Arguments to Functions

Functions can accept arguments.

Example:

```bash
#!/bin/bash

greeting()
{
    echo "Hello $1"
}

greeting James
```

Output:

```text
Hello James
```

Function arguments use the same format as script arguments:

| Variable | Meaning |
|---|---|
| `$1` | First argument |
| `$2` | Second argument |
| `$#` | Number of arguments |

---

# Returning Values

Functions can return exit codes.

Example:

```bash
check_file()
{
    if [ -f "/etc/passwd" ]
    then
        return 0
    else
        return 1
    fi
}
```

A successful result:

```text
0
```

A failure:

```text
1
```

---

# Using Function Results

Example:

```bash
check_file

if [ $? -eq 0 ]
then
    echo "File exists"
else
    echo "File missing"
fi
```

The `$?` variable stores the previous command exit code.

---

# Why Error Handling Matters

Automation scripts often run without supervision.

A script should be able to:

- Detect failures
- Report problems
- Stop safely
- Provide useful information

Example:

Bad script:

```bash
backup
delete_old_files
```

If backup fails, files may still be deleted.

Better:

```bash
backup

if backup failed

stop script
```

---

# Checking Command Success

Example:

```bash
mkdir /backup

if [ $? -ne 0 ]
then
    echo "Failed to create backup directory"
fi
```

---

# Using set -e

The `set -e` option stops a script when a command fails.

Example:

```bash
#!/bin/bash

set -e

command1

command2

command3
```

If `command1` fails:

```text
Script stops
```

---

# Using set -x for Debugging

The `set -x` option displays commands as they execute.

Example:

```bash
#!/bin/bash

set -x

echo "Testing script"
```

Output:

```text
+ echo Testing script

Testing script
```

Useful when troubleshooting scripts.

---

# Logging Script Output

Scripts can write output to log files.

Example:

```bash
echo "Backup started" >> backup.log
```

The `>>` operator appends output.

Example:

```text
backup.log

Backup started
```

---

# Redirecting Errors

Standard output:

```text
stdout
```

Standard errors:

```text
stderr
```

Redirect errors:

```bash
command 2> errors.log
```

Example:

```bash
ls /missing 2> error.log
```

---

# Combining Output and Errors

Save all output:

```bash
command > output.log 2>&1
```

This stores:

- Normal output
- Error messages

in the same file.

---

# Trap Commands

The `trap` command allows scripts to respond to events.

Example:

```bash
trap cleanup EXIT
```

The cleanup function runs when the script exits.

Example:

```bash
cleanup()
{
    echo "Cleaning up"
}

trap cleanup EXIT
```

---

# Script Debugging Checklist

When a script fails:

---

## Check Permissions

```bash
ls -l script.sh
```

---

## Check Syntax

```bash
bash -n script.sh
```

---

## Run Debug Mode

```bash
bash -x script.sh
```

---

## Check Exit Codes

```bash
echo $?
```

---

## Review Logs

```bash
cat script.log
```

---

# Practical Lab

The objective of this lab is to create reliable scripts using functions and error handling.

Tasks:

- Create functions
- Check command results
- Add logging
- Debug scripts

---

# Lab 1 - Create a Function

Create:

```bash
nano function-test.sh
```

Add:

```bash
#!/bin/bash

show_info()
{
    hostname
    uptime
}

show_info
```

Run:

```bash
./function-test.sh
```

---

# Lab 2 - Add Error Handling

Create:

```bash
nano error-test.sh
```

Add:

```bash
#!/bin/bash

mkdir /test-directory

if [ $? -ne 0 ]
then
    echo "Directory creation failed"
    exit 1
fi

echo "Success"
```

---

# Lab 3 - Debug a Script

Run:

```bash
bash -x script.sh
```

Identify:

- Commands being executed
- Where errors occur
- Exit status

---

# Lab Challenge

Create a script called:

```text
backup-check.sh
```

The script should:

- Use functions
- Check that a backup directory exists
- Report errors
- Write results to a log file
- Return a successful or failed exit code

Example output:

```text
Backup Check

Directory exists

Backup system OK
```

---

# Summary

In this lesson you learned:

- How functions organise scripts
- How to reuse code
- How to pass function arguments
- How exit codes indicate success or failure
- How to handle errors
- How to debug scripts
- How to create more reliable automation

The next lesson covers:

```text
Lesson 05 - Automation Lab
```
