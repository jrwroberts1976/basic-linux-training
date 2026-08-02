# Lesson 03 - Network Troubleshooting

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 06 Lesson 01 – Networking Fundamentals
> - Module 06 Lesson 02 – IP Addressing and Subnetting
>
> **Difficulty:** Beginner to Intermediate
>
> **Hands-on exercises:** Yes

---

# Overview

Network troubleshooting is an essential skill for Linux administrators.

When users report connectivity problems, administrators need a structured approach to identify the cause and resolve the issue.

Network problems can occur at different layers:

- Network interface
- IP configuration
- Routing
- DNS resolution
- Firewall rules
- Application services

This lesson introduces a practical troubleshooting methodology and the Linux tools used to diagnose network problems.

---

# Learning Objectives

By completing this lesson you will understand:

- How to troubleshoot Linux network problems
- How to check network interfaces
- How to verify IP configuration
- How to analyse routing information
- How to test connectivity
- How DNS affects network communication
- How to identify network services
- How to collect troubleshooting evidence

---

# A Structured Troubleshooting Approach

Network troubleshooting should follow a logical process.

A common approach:

```text
Identify Problem
        |
        v
Check Interface
        |
        v
Verify IP Configuration
        |
        v
Check Routing
        |
        v
Test Connectivity
        |
        v
Check DNS
        |
        v
Check Services
        |
        v
Document Resolution
```

Always collect evidence before making changes.

---

# Step 1 - Check Network Interfaces

The first step is confirming that the Linux system has an active network connection.

Use:

```bash
ip address
```

Example:

```text
eth0

state UP

inet 192.168.1.50/24
```

Check:

- Interface exists
- Interface is enabled
- IP address is assigned
- Correct network is configured

---

# Network Interface Status

View interface status:

```bash
ip link
```

Example:

```text
eth0: <BROADCAST,MULTICAST,UP>
```

Common states:

| State | Meaning |
|---|---|
| UP | Interface active |
| DOWN | Interface disabled |
| UNKNOWN | Status unavailable |

---

# Step 2 - Verify IP Configuration

A system requires a valid IP address to communicate.

View configuration:

```bash
ip address
```

Check:

- IP address
- Subnet prefix
- Network interface

Example:

```text
192.168.1.50/24
```

Common problems:

- Missing IP address
- Incorrect subnet
- Wrong interface configuration

---

# Step 3 - Check Routing

Routing determines where network traffic is sent.

View routes:

```bash
ip route
```

Example:

```text
default via 192.168.1.1 dev eth0
```

This shows:

- Default gateway
- Network route
- Active interface

Routing problems can cause:

- Internet access failures
- Remote connection failures
- Application communication issues

---

# Step 4 - Test Connectivity

The `ping` command tests network communication.

Test a local device:

```bash
ping 192.168.1.1
```

Test external connectivity:

```bash
ping 8.8.8.8
```

Example output:

```text
64 bytes from 8.8.8.8:
time=12 ms
```

Successful responses indicate:

- Network path exists
- Device is reachable

---

# Understanding Ping Results

Successful response:

```text
64 bytes from 8.8.8.8:
time=12 ms
```

Indicates:

- Host responded
- Network communication works

---

Packet loss example:

```text
100% packet loss
```

Possible causes:

- Network failure
- Incorrect routing
- Firewall blocking traffic
- Remote host unavailable

---

# Step 5 - Troubleshoot DNS

A system may have network connectivity but still fail to access services if DNS is not working.

DNS converts names into IP addresses.

Example:

```text
google.com

        |

        v

142.250.x.x
```

Check DNS resolution:

```bash
nslookup google.com
```

or:

```bash
dig google.com
```

---

# DNS Configuration

View configured DNS servers:

```bash
cat /etc/resolv.conf
```

Example:

```text
nameserver 192.168.1.1
```

Check:

- DNS server availability
- Correct DNS configuration
- Name resolution success

---

# Step 6 - Check Listening Services

Applications provide services through network ports.

View listening services:

```bash
ss -tuln
```

Example:

```text
LISTEN 0.0.0.0:22
```

This indicates:

- SSH service
- Port 22 listening

---

# Common Network Ports

| Port | Service |
|---|---|
| 22 | SSH |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 3306 | MySQL |
| 5432 | PostgreSQL |

---

# Step 7 - Check Firewall Configuration

Firewalls control network traffic.

Common Linux firewall technologies:

- nftables
- iptables
- ufw
- firewalld

Check firewall status:

```bash
sudo ufw status
```

Review nftables rules:

```bash
sudo nft list ruleset
```

Firewall problems can cause:

- Blocked connections
- Unreachable services
- Failed remote access

---

# Useful Network Troubleshooting Commands

| Command | Purpose |
|---|---|
| ip address | View interfaces and addresses |
| ip route | View routing information |
| ping | Test connectivity |
| traceroute | Show network path |
| nslookup | Test DNS |
| dig | Detailed DNS queries |
| ss | View listening services |
| curl | Test application connectivity |

---

# Practical Lab

The objective of this lab is to troubleshoot common Linux network issues.

Tasks include:

- Checking network interfaces
- Reviewing IP configuration
- Testing connectivity
- Checking DNS
- Identifying services

---

# Lab 1 - Check Network Interfaces

Run:

```bash
ip link
```

Record:

- Available interfaces
- Interface status

---

# Lab 2 - Check IP Configuration

Run:

```bash
ip address
```

Record:

- IP address
- Subnet
- Interface name

---

# Lab 3 - Check Routing

Run:

```bash
ip route
```

Identify:

- Default gateway
- Network routes

---

# Lab 4 - Test Connectivity

Test the gateway:

```bash
ping <gateway-address>
```

Test internet connectivity:

```bash
ping 8.8.8.8
```

Record:

- Success or failure
- Packet loss
- Response time

---

# Lab 5 - Test DNS

Run:

```bash
nslookup google.com
```

Identify:

- DNS server
- Returned IP address

---

# Lab 6 - Check Running Services

Run:

```bash
ss -tuln
```

Identify:

- Listening ports
- Available services

---

# Troubleshooting Scenario

A user reports:

> "The application server cannot connect to the database."

You have been asked to investigate.

---

## Investigation Steps

Check network configuration:

```bash
ip address
```

Check routing:

```bash
ip route
```

Test connectivity:

```bash
ping database-server
```

Test DNS:

```bash
nslookup database-server
```

Check services:

```bash
ss -tuln
```

---

# Troubleshooting Report

Document:

## Problem

Describe the reported issue.

---

## Evidence Collected

Include:

- Commands executed
- Output observed
- Errors identified

---

## Root Cause

Examples:

- Incorrect IP address
- Missing route
- DNS failure
- Firewall rule
- Service unavailable

---

## Resolution

Document:

- Changes made
- Tests performed
- Final outcome

---

# Summary

In this lesson you learned:

- A structured approach to network troubleshooting
- How to inspect Linux network interfaces
- How to verify IP configuration
- How to analyse routing
- How to troubleshoot DNS
- How to identify network services
- How to document technical issues

Network troubleshooting is a core Linux administration skill used in enterprise systems, cloud environments, containers, and production platforms.
