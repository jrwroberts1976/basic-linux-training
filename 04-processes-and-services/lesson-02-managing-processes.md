# Lesson 02 - Managing Linux Processes

> **Estimated time:** 60–90 minutes  
>
> **Prerequisites:**
> - Module 04 – Processes and Services
> - Lesson 01 – Understanding Linux Processes
>
> **Difficulty:** Beginner to Intermediate
>
> **Hands-on exercises:** Yes

---

# Overview

Linux systems run many processes at the same time.

Administrators need to understand how to:

- View running processes
- Identify resource usage
- Find specific processes
- Run commands in the background
- Control and stop processes safely

Process management is an important skill for troubleshooting performance issues and maintaining system stability.

---

# Viewing Processes

Linux provides several commands for viewing running processes.

## ps Command

The `ps` command displays information about running processes.

Basic usage:

```bash
ps

Example:

PID TTY          TIME CMD
1234 pts/0    00:00:00 bash
5678 pts/0    00:00:01 ps

Information shown:

Column	Meaning
PID	Process ID
TTY	Terminal
TIME	CPU time used
CMD	Command
Viewing All Processes

To view all running processes:

ps aux

Example:

USER       PID %CPU %MEM COMMAND
root         1  0.0  1.2 systemd
james     1234  0.1  0.5 bash

Important columns:

Column	Meaning
USER	Process owner
PID	Process ID
%CPU	CPU usage
%MEM	Memory usage
COMMAND	Running command
Finding Processes
Using pgrep

pgrep searches for processes by name.

Example:

pgrep ssh

Output:

742

This returns the process ID.

Using ps with grep

Example:

ps aux | grep ssh

This searches the process list.

Example:

root 742 0.0 sshd
Process Information

To view details about a process:

ps -fp PID

Example:

ps -fp 742

Output:

UID   PID  PPID CMD
root  742    1  sshd

Information:

Field	Meaning
PID	Process ID
PPID	Parent Process ID
CMD	Command
Parent and Child Processes

Processes can create other processes.

Example:

systemd
 |
 ├── sshd
 |    |
 |    └── bash
 |
 └── cron

View process relationships:

pstree

This shows the hierarchy of processes.

Background Processes

Commands normally run in the foreground.

Example:

sleep 60

The terminal waits until the command finishes.

To run a command in the background:

sleep 300 &

Example:

[1] 12345

The number returned is the process ID.

Viewing Background Jobs

Show running background jobs:

jobs

Example:

[1]+ Running sleep 300 &
Bringing Jobs to the Foreground

Move a background job back:

fg

Example:

fg %1
Sending Processes to the Background

A running command can be moved into the background.

Press:

CTRL + Z

Then:

bg

Example:

sleep 300
CTRL + Z
bg
Process Signals

Linux controls processes using signals.

Common signals:

Signal	Number	Purpose
SIGTERM	15	Graceful shutdown
SIGKILL	9	Force termination
SIGHUP	1	Reload configuration
Stopping Processes
Using kill

Terminate a process:

kill PID

Example:

kill 12345

This sends SIGTERM.

Force Stopping Processes

If a process does not stop:

kill -9 PID

Example:

kill -9 12345

SIGKILL immediately stops the process.

Use carefully because the application cannot clean up.

Using pkill

Kill processes by name:

pkill process_name

Example:

pkill sleep
Monitoring Processes
top

The top command provides real-time process monitoring.

Run:

top

Shows:

CPU usage
Memory usage
Running processes
System load
htop

If installed:

htop

Provides an interactive interface.

Install:

sudo apt install htop
Process Priority

Linux allows processes to have different priorities.

Priority is controlled using:

nice
renice

View priority:

ps -el
Starting a Process with Priority

Example:

nice -n 10 command

Higher nice values mean lower priority.

Changing Process Priority

Example:

renice 10 -p PID
Practical Exercises
Task 1 - View Processes

Run:

ps aux

Identify:

Your shell process
System processes
Running applications
Task 2 - Monitor the System

Run:

top

Record:

Highest CPU process:

Highest memory process:
Task 3 - Create a Background Process

Run:

sleep 300 &

Find it:

ps aux | grep sleep

Stop it:

kill PID
Task 4 - Explore Process Tree

Run:

pstree

Identify:

Parent processes
Child processes
Knowledge Check
What does PID stand for?
Which command shows all running processes?
What command displays a process tree?
What symbol runs a command in the background?
What signal does kill send by default?
What is the difference between SIGTERM and SIGKILL?
Which command provides live process monitoring?
Summary

In this lesson you learned:

✓ How to view Linux processes
✓ How to find specific processes
✓ How parent and child processes work
✓ How to run background jobs
✓ How to stop processes safely
✓ How to monitor system activity
✓ How Linux signals control processes

Next Lesson

Lesson 03 - Systemd and Service Management

You will learn:

What systemd is
How services are managed
Starting and stopping services
Enabling services at boot
Checking service statu