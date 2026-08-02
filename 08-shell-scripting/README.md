# Module 08 - Shell Scripting

> **Estimated time:** 5–8 hours
>
> **Prerequisites:**
> - Module 01 – Command Line Fundamentals
> - Module 04 – Processes and Services
> - Module 07 – Storage Management
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Shell scripting is an essential skill for Linux administrators, cloud engineers, and DevOps professionals.

Linux administrators often need to automate repetitive tasks such as:

- System checks
- Backups
- Log management
- Software deployment
- Service monitoring
- User management

Shell scripts allow administrators to combine Linux commands into reusable automation tools.

This module introduces Bash scripting fundamentals and builds the skills required to automate Linux administration tasks.

---

# Learning Objectives

By completing this module you will understand:

- What shell scripts are
- How Bash interprets scripts
- How to create and execute scripts
- How to use variables
- How to accept user input
- How to use conditions and loops
- How to create reusable functions
- How to handle errors
- How to automate Linux administration tasks

---

# Module Contents

## Lesson 01 - Shell Scripting Fundamentals

Topics covered:

- What shell scripting is
- Bash shell overview
- Creating scripts
- The shebang line
- Script permissions
- Running scripts
- Basic commands in scripts

---

## Lesson 02 - Variables and Input

Topics covered:

- Creating variables
- Environment variables
- Command arguments
- User input
- Reading values
- Exit codes

---

## Lesson 03 - Conditions and Loops

Topics covered:

- Conditional statements
- `if` statements
- `case` statements
- `for` loops
- `while` loops
- File testing

---

## Lesson 04 - Functions and Error Handling

Topics covered:

- Creating functions
- Passing arguments
- Returning values
- Error handling
- Debugging scripts
- Logging output

---

## Lesson 05 - Automation Lab

Practical exercises:

- Create system health checks
- Automate backups
- Monitor disk usage
- Check running services
- Create administration scripts

---

# Key Bash Commands

| Command | Purpose |
|---|---|
| `bash` | Run Bash scripts |
| `chmod` | Change script permissions |
| `echo` | Display output |
| `read` | Accept user input |
| `export` | Create environment variables |
| `test` | Perform condition checks |
| `grep` | Search text |
| `awk` | Process text |
| `sed` | Modify text |
| `cron` | Schedule scripts |

---

# Script Structure

A basic Bash script contains:

```text
Shebang

Variables

Commands

Logic

Output
```

Example:

```bash
#!/bin/bash

echo "Hello Linux"
```

The first line tells Linux which interpreter should run the script.

---

# Automation Concepts

Shell scripting is commonly used for:

- Server administration
- Monitoring
- Backups
- Deployment tasks
- Maintenance jobs

Example workflow:

```text
Administrator

      |

Shell Script

      |

Linux Commands

      |

Automated Task
```

---

# Practical Skills Developed

After completing this module you should be able to:

- Write basic Bash scripts
- Automate common Linux tasks
- Create administration utilities
- Troubleshoot script problems
- Schedule automated jobs

---

# Module Status

⏳ Complete
