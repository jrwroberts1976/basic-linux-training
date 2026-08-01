# Lesson 04 - Logs and journalctl

> **Estimated time:** 60–90 minutes  
>
> **Prerequisites:**
> - Module 04 – Processes and Services
> - Lesson 03 – Systemd and Service Management
>
> **Difficulty:** Beginner to Intermediate
>
> **Hands-on exercises:** Yes

---

# Overview

Linux systems generate a large amount of information about what is happening on the system.

This information is stored in logs.

Logs help administrators:

- Troubleshoot problems
- Investigate service failures
- Monitor system activity
- Identify security events
- Understand system behaviour

Modern Linux systems use **systemd-journald** to collect and manage system logs.

The main tool used to view these logs is:

```bash
journalctl
Linux Logging

Linux records information about:

System startup
Running services
User activity
Hardware events
Application messages
Security events

Examples of logs:

Log Type	Example
Authentication	SSH login attempts
System	Kernel messages
Services	Service startup failures
Applications	Application errors
Traditional Log Files

Historically, Linux stored logs in:

/var/log

View the directory:

ls /var/log

Common log files:

File	Purpose
auth.log	Authentication events
syslog	General system messages
kern.log	Kernel messages
dpkg.log	Package management events

Example:

cat /var/log/syslog
systemd Journal

Modern Linux distributions use the systemd journal.

The journal collects messages from:

The kernel
System services
Applications
User sessions

The journal is managed by:

systemd-journald

Check the service:

systemctl status systemd-journald
Viewing Logs with journalctl

The basic command:

journalctl

displays the system journal.

Example:

Jul 31 10:15:01 server systemd[1]: Started SSH service.
Jul 31 10:15:02 server sshd[500]: Accepted password login.
Viewing Recent Logs

Show the latest log entries:

journalctl -n

Example:

journalctl -n 50

This displays the last 50 entries.

Following Live Logs

Similar to tail -f:

journalctl -f

This displays new log entries as they appear.

Useful when:

Starting services
Testing changes
Troubleshooting problems

Exit using:

CTRL + C
Viewing Logs for a Service

To view logs for a specific service:

journalctl -u service_name

Example:

journalctl -u ssh

This shows only SSH service logs.

Viewing Recent Service Failures

Show recent errors:

journalctl -p err

Example output:

Failed to start nginx.service

Priority levels include:

Level	Meaning
emerg	System unusable
alert	Immediate action required
crit	Critical error
err	Error
warning	Warning
info	Information
debug	Debug messages
Viewing Logs Since Boot

View logs from the current boot:

journalctl -b

This is useful after:

System crashes
Unexpected reboots
Startup problems
Previous Boot Logs

View logs from the previous boot:

journalctl -b -1

Useful when investigating:

Failed boots
System crashes
Hardware problems
Kernel Messages

The kernel produces important system messages.

View kernel messages:

dmesg

Examples:

Hardware detection
Driver messages
Disk errors
Network events

Example:

dmesg | less
Filtering Logs by Time

View logs after a specific time:

journalctl --since "1 hour ago"

Example:

journalctl --since today

View logs before a specific time:

journalctl --until "10:00"
Searching Logs

Use standard Linux tools with journalctl.

Example:

journalctl | grep ssh

Search for errors:

journalctl | grep error
Checking Service Failures

When a service fails:

First check status:

systemctl status service_name

Then check logs:

journalctl -u service_name

Example:

systemctl status nginx

journalctl -u nginx

Troubleshooting approach:

Check service status
Review logs
Identify the error
Correct the issue
Restart the service
Log Storage

The systemd journal can store logs:

Temporary:

/run/log/journal

Persistent:

/var/log/journal

Check journal storage:

journalctl --disk-usage
Managing Journal Size

View journal usage:

journalctl --disk-usage

Clean old logs:

sudo journalctl --vacuum-time=7d

This removes logs older than 7 days.

Practical Exercise
Task 1 - View Recent Logs

Run:

journalctl -n 20

Identify:

Recent system events
Running services
Task 2 - Check SSH Logs

Run:

journalctl -u ssh

Find:

Service startup messages
Login events
Task 3 - Find Errors

Run:

journalctl -p err

Record:

Errors found:
Task 4 - Check Kernel Messages

Run:

dmesg | less

Identify:

Hardware messages
Driver information
Knowledge Check
Where are traditional Linux log files stored?
What command displays the systemd journal?
How do you view logs for a specific service?
What option shows logs from the current boot?
What command displays kernel messages?
Why are logs important for administrators?
Summary

In this lesson you learned:

✓ Why Linux logging is important
✓ The difference between traditional logs and systemd journal
✓ How to use journalctl
✓ How to view service logs
✓ How to investigate failures
✓ How to analyse system events

Next Lesson

Lesson 05 - Processes and Services Administration Lab

You will complete practical tasks covering:

Process monitoring
Service management
Log analysis
Troubleshooting failures