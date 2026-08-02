# Lesson 02 - IP Addressing and Subnetting

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 06 – Networking Fundamentals
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

IP addressing is a fundamental networking skill for Linux administrators.

Every device connected to a network requires an address so that systems can communicate with each other.

Understanding IP addressing allows administrators to:

- Identify devices on a network
- Understand network ranges
- Configure Linux network settings
- Troubleshoot connectivity problems
- Support cloud and enterprise environments

This lesson introduces IPv4 addressing, subnet masks, CIDR notation, and network gateways.

---

# Learning Objectives

By completing this lesson you will understand:

- What an IP address is
- How IPv4 addresses are structured
- The difference between private and public addresses
- The purpose of subnet masks
- How CIDR notation works
- How networks and hosts are identified
- The purpose of default gateways
- How to view IP configuration on Linux

---

# What Is an IP Address?

An IP address is a unique identifier assigned to a device on a network.

IP addresses allow systems to:

- Communicate with other devices
- Send and receive network traffic
- Access services
- Connect to other networks

Example:

```text
192.168.1.50
```

An IPv4 address contains four numbers separated by periods.

Example:

```text
192 . 168 . 1 . 50
```

Each section is called an octet.

Each octet has a range of:

```text
0 - 255
```

---

# IPv4 Address Structure

An IPv4 address contains two sections:

- Network portion
- Host portion

Example:

```text
192.168.1.50/24
```

The `/24` represents the subnet size.

The address contains:

```text
Network:
192.168.1.0

Host:
50
```

The network portion identifies the network.

The host portion identifies the individual device.

---

# Private IP Addresses

Private IP addresses are used inside internal networks.

They are not directly accessible from the internet.

Common private address ranges:

| Range | Usage |
|---|---|
| 10.0.0.0/8 | Large private networks |
| 172.16.0.0/12 | Medium private networks |
| 192.168.0.0/16 | Home and small business networks |

Examples:

```text
192.168.1.50

10.0.0.25

172.16.5.10
```

Common environments using private addresses:

- Home networks
- Enterprise networks
- Cloud virtual networks
- Container networks

---

# Public IP Addresses

Public IP addresses are used for communication across the internet.

Examples:

```text
8.8.8.8

1.1.1.1
```

Public IP addresses are used by:

- Websites
- Public cloud services
- Internet-facing applications

Internet Service Providers assign public addresses to customers.

---

# Static and Dynamic IP Addresses

IP addresses can be assigned in two ways.

---

# Static IP Address

A static IP address is manually configured.

Common uses:

- Servers
- Network equipment
- Infrastructure services

Example:

```text
Linux Server

192.168.1.50
```

Advantages:

- Address remains consistent
- Easier administration
- Suitable for services

---

# Dynamic IP Address

A dynamic IP address is automatically assigned using DHCP.

Common uses:

- Workstations
- Laptops
- Mobile devices

Example:

```text
Laptop

192.168.1.120
```

Advantages:

- Automatic configuration
- Easier management

---

# Subnet Masks

A subnet mask determines which part of an IP address identifies the network and which part identifies the host.

Example:

```text
IP Address:

192.168.1.50


Subnet Mask:

255.255.255.0
```

CIDR notation:

```text
192.168.1.50/24
```

The `/24` means:

- 24 bits identify the network
- 8 bits identify hosts

---

# Common CIDR Notation

| CIDR | Subnet Mask | Available Hosts |
|---|---|---|
| /24 | 255.255.255.0 | 254 |
| /16 | 255.255.0.0 | 65,534 |
| /8 | 255.0.0.0 | 16 million |

---

# Network Address

The network address identifies the network itself.

Example:

```text
192.168.1.0/24
```

Network address:

```text
192.168.1.0
```

This address cannot be assigned to a device.

---

# Broadcast Address

The broadcast address is used to communicate with all devices on the network.

Example:

```text
192.168.1.255
```

This address is reserved for network broadcasts.

---

# Default Gateway

A default gateway allows devices to communicate with other networks.

Usually this is a router.

Example:

```text
Linux Server

192.168.1.50

        |
        |

Router

192.168.1.1

        |
        |

Internet
```

The Linux system sends traffic outside its local network through the default gateway.

---

# Viewing Network Configuration on Linux

Display IP address information:

```bash
ip address
```

Example:

```text
eth0

inet 192.168.1.50/24
```

View routing information:

```bash
ip route
```

Example:

```text
default via 192.168.1.1 dev eth0
```

---

# Practical Lab

The objective of this lab is to identify and understand IP addressing on a Linux system.

Tasks include:

- Identify IP addresses
- Identify network information
- Understand subnet sizes
- Identify default gateways

---

# Lab 1 - View IP Address Information

Run:

```bash
ip address
```

Identify:

- Network interface
- IP address
- MAC address
- CIDR prefix

Example:

```text
192.168.1.50/24
```

---

# Lab 2 - View Routing Information

Run:

```bash
ip route
```

Identify:

- Default gateway
- Network routes
- Active interface

---

# Lab 3 - Calculate Network Information

Using:

```text
192.168.1.50/24
```

Identify:

Network:

```text
192.168.1.0
```

Broadcast:

```text
192.168.1.255
```

Available hosts:

```text
192.168.1.1 - 192.168.1.254
```

---

# Lab Challenge

A Linux server has the following configuration:

```text
IP Address:

192.168.10.25/24


Gateway:

192.168.10.1
```

Answer:

1. What is the network address?
2. What is the broadcast address?
3. Can the server communicate with:

```text
192.168.10.50
```

4. Can the server communicate with:

```text
192.168.20.50
```

Explain why.

---

# Summary

In this lesson you learned:

- How IPv4 addresses work
- How private and public addresses differ
- How subnet masks define networks
- How CIDR notation works
- How default gateways provide external connectivity
- How to view Linux network configuration

IP addressing knowledge is essential for Linux administration, cloud platforms, containers, and enterprise networking.
