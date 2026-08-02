# Lesson 04 - Networking Administration Lab

> **Estimated time:** 2–3 hours
>
> **Prerequisites:**
> - Module 06 Lesson 01 – Networking Fundamentals
> - Module 06 Lesson 02 – IP Addressing and Subnetting
> - Module 06 Lesson 03 – Network Troubleshooting
>
> **Difficulty:** Beginner to Intermediate
>
> **Hands-on exercises:** Yes

---

# Overview

This practical lab combines the networking concepts covered throughout Module 06.

The objective is to practise the skills required by Linux administrators when configuring, validating, and troubleshooting network connectivity.

You will investigate a Linux system, collect network information, test communication, and document your findings.

---

# Lab Objectives

By completing this lab you will be able to:

- Identify Linux network interfaces
- Review IP addressing information
- Understand routing configuration
- Test network connectivity
- Troubleshoot DNS resolution
- Identify running network services
- Document network troubleshooting activities

---

# Lab Environment

You will need:

- A Linux system
- Network connectivity
- Terminal access
- Basic command-line knowledge

Example environment:

```text
Linux Server

        |
        |

Network Switch

        |
        |

Router

        |
        |

Internet
```

---

# Task 1 - Identify Network Interfaces

## Objective

Identify the network interfaces available on the Linux system.

Run:

```bash
ip link
```

Example output:

```text
1: lo:
2: eth0:
```

Record:

- Interface names
- Interface status
- Available network adapters

---

# Task 2 - Review IP Configuration

## Objective

Identify the IP addresses assigned to the system.

Run:

```bash
ip address
```

Example:

```text
eth0

inet 192.168.1.50/24
```

Record:

| Item | Value |
|---|---|
| Interface | |
| IP Address | |
| CIDR Prefix | |
| MAC Address | |

---

# Task 3 - Identify Network Details

Using the IP address discovered, identify:

Example:

```text
IP Address:

192.168.1.50/24
```

Network address:

```text
192.168.1.0
```

Broadcast address:

```text
192.168.1.255
```

Available host range:

```text
192.168.1.1 - 192.168.1.254
```

Record your results:

| Item | Value |
|---|---|
| Network Address | |
| Broadcast Address | |
| Host Range | |

---

# Task 4 - Check Routing Configuration

## Objective

Identify how traffic leaves the local network.

Run:

```bash
ip route
```

Example:

```text
default via 192.168.1.1 dev eth0
```

Record:

| Item | Value |
|---|---|
| Default Gateway | |
| Interface | |

---

# Task 5 - Test Local Connectivity

## Objective

Confirm communication with the local gateway.

Run:

```bash
ping <gateway-address>
```

Example:

```bash
ping 192.168.1.1
```

Record:

- Packets sent
- Packets received
- Response time

Example:

```text
Packets transmitted: 4
Packets received: 4
Packet loss: 0%
```

---

# Task 6 - Test External Connectivity

## Objective

Verify access outside the local network.

Run:

```bash
ping 8.8.8.8
```

Record:

- Successful response
- Packet loss
- Latency

---

# Task 7 - Test DNS Resolution

## Objective

Verify that DNS is working.

Run:

```bash
nslookup google.com
```

Example:

```text
Name:

google.com


Address:

142.x.x.x
```

Record:

| Item | Value |
|---|---|
| DNS Server | |
| Resolved Address | |

---

# Task 8 - Check Listening Network Services

## Objective

Identify services running on the Linux system.

Run:

```bash
ss -tuln
```

Example:

```text
LISTEN 0 128 0.0.0.0:22
```

Record:

| Port | Service |
|---|---|
| | |
| | |

---

# Task 9 - Test Application Connectivity

## Objective

Test communication with a service.

Example HTTP test:

```bash
curl http://localhost
```

Example SSH test:

```bash
ssh localhost
```

Record:

- Service tested
- Result
- Any errors

---

# Troubleshooting Exercise

## Scenario

A Linux server cannot access an external website.

You have been asked to investigate.

---

# Investigation Checklist

## Step 1 - Check Interface

Run:

```bash
ip link
```

Question:

Is the network interface active?

---

## Step 2 - Check IP Address

Run:

```bash
ip address
```

Question:

Does the system have a valid IP address?

---

## Step 3 - Check Route

Run:

```bash
ip route
```

Question:

Is a default gateway configured?

---

## Step 4 - Test Gateway

Run:

```bash
ping <gateway-address>
```

Question:

Can the server communicate locally?

---

## Step 5 - Test External IP

Run:

```bash
ping 8.8.8.8
```

Question:

Does external connectivity work?

---

## Step 6 - Test DNS

Run:

```bash
nslookup google.com
```

Question:

Can the system resolve names?

---

# Lab Report

Document your findings.

---

## System Information

```text
Hostname:

Operating System:

IP Address:

Network Interface:
```

---

## Network Configuration

```text
Gateway:

DNS Server:

Network Range:
```

---

## Tests Completed

| Test | Result |
|---|---|
| Interface check | |
| IP configuration | |
| Routing check | |
| Gateway connectivity | |
| External connectivity | |
| DNS resolution | |
| Service validation | |

---

## Findings

Describe:

- Problems identified
- Evidence collected
- Commands used

---

## Resolution

Document:

- Actions taken
- Configuration changes
- Validation completed

---

# Skills Demonstrated

This lab demonstrates practical Linux administration skills:

- Network investigation
- IP configuration analysis
- Connectivity testing
- DNS troubleshooting
- Service validation
- Technical documentation

---

# Module Completion

After completing this lab you should be confident with:

- Linux networking commands
- Basic IP addressing
- Network troubleshooting
- Service connectivity testing

---

# Next Module

## Module 07 - Storage

You will learn:

- Disk management
- Linux filesystems
- Storage configuration
- Mount points
- Logical Volume Management (LVM)
- Storage troubleshooting
