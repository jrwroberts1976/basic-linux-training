# Lesson 01 - Understanding Linux Processes

> **Estimated time:** 60–90 minutes  
>
> **Prerequisites:**
> - Module 01 – Command Line Fundamentals
> - Module 02 – Linux Filesystem Administration
> - Module 03 – Users and Groups
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

A Linux system is made up of many running processes.

Every command you execute, every application you start, and every system service running in the background is a process.

Understanding processes is a fundamental Linux administration skill because it allows administrators to:

- Monitor system activity
- Identify resource usage
- Troubleshoot problems
- Stop unwanted applications
- Investigate service failures

---

# What is a Process?

A **process** is a running instance of a program.

When a program is stored on disk, it is simply a file.

When that program is started, Linux loads it into memory and creates a process.

Example:

Program:

```text
/usr/bin/nginx

Running process:

nginx process
Programs vs Processes

A program is:

A file stored on disk
Contains instructions for the computer

A process is:

A running copy of a program
Uses CPU and memory resources
Has a unique identifier

Example:

Program:

/usr/bin/nginx


Running Process:

nginx PID 1234
Process IDs (PID)

Every running process in Linux receives a unique number called a:

Process ID (PID)

The PID allows administrators to identify and manage individual processes.

Example:

PID   COMMAND

1     systemd
550   sshd
1200  nginx
2500  bash

No two running processes have the same PID.

The Init Process

The first process started by the Linux kernel is:

PID 1

On modern Linux systems this is normally:

systemd

Check PID 1:

ps -p 1

Example output:

PID TTY      TIME CMD
1   ?        00:00:02 systemd

The PID 1 process is responsible for:

Starting system services
Managing background services
Handling system startup
Replacing failed processes
Parent and Child Processes

Processes can create other processes.

The process that creates another process is called the:

Parent Process

The new process is called the:

Child Process

Example:

systemd
 |
 ├── sshd
 |    |
 |    └── bash
 |
 └── cron

In this example:

systemd is the parent of sshd
sshd is the parent of bash
Viewing Processes

The ps command displays running processes.

Basic usage:

ps

Example:

PID TTY          TIME CMD
2301 pts/0    00:00:00 bash
2450 pts/0    00:00:00 ps

By default, ps only shows processes from your current terminal.

Viewing All Processes

To view all running processes:

ps aux

Example:

USER       PID %CPU %MEM COMMAND

root         1  0.0  0.5 /sbin/init
root       500  0.1  1.2 sshd
james     2200  0.0  0.3 bash

Information shown:

Column	Meaning
USER	Owner of process
PID	Process ID
%CPU	CPU usage
%MEM	Memory usage
COMMAND	Program running
Viewing Process Relationships

The pstree command displays processes in a tree format.

Example:

pstree

Output:

systemd
├─sshd
│ └─bash
├─cron
└─nginx

This makes parent and child relationships easier to understand.

Searching for Processes

The pgrep command searches for processes by name.

Example:

pgrep ssh

Output:

500

This returns the PID of matching processes.

Monitoring Processes

The top command provides a live view of system activity.

Run:

top

Example:

PID USER      %CPU %MEM COMMAND

1200 root      5.0  2.1 nginx
2200 james     1.0  0.5 bash

Useful information:

CPU usage
Memory usage
Running processes
System load

Exit top:

q
Background Processes

Linux can run commands in the background.

Example:

sleep 300 &

The & symbol runs the command in the background.

Example output:

[1] 3456

Where:

3456 = Process ID
Practical Exercise
Task 1 - View Running Processes

Run:

ps aux

Identify:

Your shell process
PID 1
Any services running
Task 2 - Find a Process

Run:

pgrep systemd

Record:

PID:
Task 3 - Monitor the System

Run:

top

Identify:

Highest CPU process
Highest memory process
Knowledge Check
What is a process?
What does PID stand for?
Which process normally has PID 1?
What command shows all running processes?
What command displays processes as a tree?
What symbol runs a command in the background?
Summary

In this lesson you learned:

✓ What Linux processes are
✓ The difference between programs and processes
✓ How Linux identifies processes using PIDs
✓ Parent and child processes
✓ How to view running processes
✓ How to monitor system activity

Next Lesson

Lesson 02 - Managing Linux Processes

You will learn:

Process signals
Stopping processes
Using kill
Managing background jobs
Troubleshooting stuck applications