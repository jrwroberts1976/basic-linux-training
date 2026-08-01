# Lesson 05 - Processes and Services Administration Lab

> **Estimated time:** 90–120 minutes  
>
> **Prerequisites:**
> - Module 04 – Processes and Services
> - Lesson 01 – Understanding Linux Processes
> - Lesson 02 – Managing Linux Processes
> - Lesson 03 – Systemd and Service Management
> - Lesson 04 – Logs and journalctl
>
> **Difficulty:** Intermediate
>
> **Hands-on exercises:** Yes

---

# Overview

This practical lab combines the skills learned throughout the Processes and Services module.

You will perform common Linux administration tasks including:

- Monitoring processes
- Managing running applications
- Checking services
- Investigating service problems
- Reviewing system logs
- Troubleshooting failures

The tasks simulate activities performed by Linux system administrators.

---

# Lab Environment

You can complete this lab using:

- Linux server
- Virtual machine
- Raspberry Pi
- Cloud Linux instance

Recommended:

- Debian
- Ubuntu Server
- Rocky Linux

---

# Task 1 - Identify Running Processes

## Objective

Understand what processes are running on your Linux system.

Run:

```bash
ps aux

Review:

Running applications
User ownership
CPU usage
Memory usage
Process Tree

View parent and child relationships:

pstree

Identify:

system processes
user processes
background services
Task 2 - Monitor System Activity
Objective

Monitor live system activity.

Run:

top

Review:

CPU usage
Memory usage
Running processes

If installed:

htop

Identify:

Highest CPU process
Highest memory process

Record:

Highest CPU process:

Highest memory process:
Task 3 - Find a Process
Objective

Locate running processes.

Search for SSH:

pgrep ssh

View details:

ps -fp PID

Replace:

PID

with the process ID returned.

Record:

SSH Process ID:
Task 4 - Manage a Process
Objective

Understand how processes can be controlled.

Start a background process:

sleep 300 &

Find the process:

ps aux | grep sleep

Stop the process:

kill PID

Confirm it has stopped:

ps aux | grep sleep
Task 5 - Check System Services
Objective

Use systemd to manage services.

Check SSH:

systemctl status ssh

Record:

Service status:

Running PID:
Task 6 - List Running Services

View active services:

systemctl list-units --type=service

Identify:

Running services
Service names
Current states

Record three services:

Service 1:

Service 2:

Service 3:
Task 7 - Manage a Service
Objective

Start, stop and restart services.

Choose a test service.

Example:

cron

Check status:

systemctl status cron

Stop:

sudo systemctl stop cron

Confirm:

systemctl status cron

Start again:

sudo systemctl start cron

Verify:

systemctl status cron
Task 8 - Enable a Service

Check if SSH starts automatically:

systemctl is-enabled ssh

Enable if required:

sudo systemctl enable ssh

Confirm:

systemctl is-enabled ssh
Task 9 - Review Service Logs
Objective

Investigate service activity.

View SSH logs:

journalctl -u ssh

View recent entries:

journalctl -u ssh -n 20

Identify:

Service startup messages
Login activity
Errors
Task 10 - Investigate System Errors

Find errors:

journalctl -p err

Review:

Failed services
Hardware messages
System warnings

Record:

Errors found:

Actions taken:
Task 11 - Boot Troubleshooting

View current boot logs:

journalctl -b

View previous boot:

journalctl -b -1

Identify:

Startup messages
Failed services
Warnings
Troubleshooting Scenario
Scenario

A web service is unavailable.

You are told:

Users cannot access the website.

Perform the following investigation.

Step 1 - Check Service Status

Example:

systemctl status nginx

Questions:

Is the service running?
Is the service failed?
What PID is running?
Step 2 - Review Logs

Run:

journalctl -u nginx

Look for:

Configuration errors
Permission issues
Startup failures
Step 3 - Restart Service

If appropriate:

sudo systemctl restart nginx

Verify:

systemctl status nginx
Knowledge Check
What command shows running processes?
What does PID mean?
What command manages systemd services?
How do you view logs for a service?
How do you restart a service?
What command shows errors in the system journal?
Why are logs important when troubleshooting?
Lab Completion Checklist
Task	Complete
View running processes	☐
Monitor system activity	☐
Find processes	☐
Stop and manage processes	☐
Check services	☐
Start and stop services	☐
Enable services	☐
Review journal logs	☐
Investigate errors	☐
Complete troubleshooting scenario	☐
Summary

You have completed the Processes and Services module.

You should now understand:

✓ Linux processes
✓ Process monitoring
✓ Process management
✓ systemd services
✓ Service troubleshooting
✓ Linux logging
✓ journalctl administration

Next Module

Module 05 - Package Management

You will learn:

Linux package managers
Software repositories
Installing applications
Updating systems
Managing software packages