# Lesson 01 - Networking Fundamentals

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 01 – Command Line Fundamentals
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Networking is a fundamental skill for Linux administrators, cloud engineers, and DevOps professionals.

Linux systems rely heavily on networking to communicate with other systems, access services, transfer data, and support applications.

Understanding networking fundamentals allows administrators to:

- Understand how systems communicate
- Troubleshoot connectivity issues
- Configure Linux network settings
- Support servers and cloud environments
- Work with containers and distributed systems

This lesson introduces the basic concepts required before learning IP addressing, subnetting, and network troubleshooting.

---

# Learning Objectives

By completing this lesson you will understand:

- What a network is
- How devices communicate
- The purpose of IP addresses
- The role of MAC addresses
- The difference between local and remote networks
- The purpose of gateways
- How DNS works
- What ports and protocols are
- Basic Linux networking commands

---

# What Is a Network?

A network is a collection of connected devices that can communicate and exchange information.

Examples of networked devices:

- Computers
- Servers
- Routers
- Switches
- Mobile devices
- IoT devices
- Cloud infrastructure

A simple network:

```text
Computer
    |
 Switch
    |
 Router
    |
 Internet
```

Networks allow systems to share:

- Data
- Applications
- Services
- Internet access
- Storage

---

# Types of Networks

Networks can be classified by their size and purpose.

---

# Local Area Network (LAN)

A Local Area Network connects devices within a small geographical area.

Examples:

- Home networks
- Office networks
- Data centre networks

Example:

```text
Laptop
   |
 Switch
   |
Server
```

A LAN allows devices to communicate directly with each other.

---

# Wide Area Network (WAN)

A Wide Area Network connects networks across larger distances.

Examples:

- Company sites connected together
- Internet connections
- Cloud networks

Example:

```text
Office Network

      |
      |

   Internet

      |
      |

 Cloud Network
```

The internet is the largest example of a WAN.

---

# How Devices Communicate

Devices communicate using agreed rules called protocols.

Communication requires:

- A source device
- A destination device
- An addressing system
- A communication protocol

Example:

```text
Linux Server

192.168.1.50

        |
        |
      Network
        |
        |

Database Server

192.168.1.100
```

The devices use addresses to identify where data should be sent.

---

# IP Addresses

An IP address identifies a device on a network.

Example:

```text
192.168.1.50
```

IP addresses allow systems to:

- Send data to the correct device
- Identify network locations
- Communicate across networks

IPv4 addresses contain four numbers separated by periods.

Example:

```text
192 . 168 . 1 . 50
```

Each section is called an octet.

Each octet has a range of:

```text
0 - 255
```

IP addressing and subnetting are covered in detail in:

```text
Lesson 02 - IP Addressing and Subnetting
```

---

# MAC Addresses

A MAC address identifies a physical network interface.

Example:

```text
00:1A:2B:3C:4D:5E
```

MAC addresses:

- Are assigned to network hardware
- Are used by switches
- Operate at Layer 2 of the OSI model

Example:

```text
Computer

MAC Address

      |

Network Switch

      |

Router
```

A switch uses MAC addresses to deliver traffic inside a local network.

---

# Routers and Default Gateways

A router connects different networks together.

Example:

```text
Home Network

192.168.1.0/24

        |

     Router

        |

     Internet
```

The router acts as the default gateway.

The default gateway is where a device sends traffic that is not on the local network.

Example:

```text
Linux Server

192.168.1.50


Default Gateway

192.168.1.1
```

Traffic to another local device stays on the LAN.

Traffic to the internet goes through the gateway.

---

# DNS

DNS stands for Domain Name System.

DNS converts human-readable names into IP addresses.

Humans use:

```text
www.example.com
```

Computers use:

```text
93.184.216.34
```

DNS allows users and applications to access services without remembering IP addresses.

Common DNS servers:

| Provider | Address |
|---|---|
| Google DNS | `8.8.8.8` |
| Cloudflare DNS | `1.1.1.1` |

---

# Ports and Services

A server can run multiple network services at the same time.

Ports identify individual services.

Example:

```text
192.168.1.50:22
```

This means:

- IP address: `192.168.1.50`
- Port: `22`

Common ports:

| Port | Protocol | Purpose |
|---|---|---|
| 22 | SSH | Remote administration |
| 53 | DNS | Name resolution |
| 80 | HTTP | Web traffic |
| 443 | HTTPS | Secure web traffic |
| 3306 | MySQL | Database |
| 5432 | PostgreSQL | Database |

---

# Network Protocols

Protocols define how devices communicate.

---

# TCP

Transmission Control Protocol.

TCP provides:

- Reliable communication
- Error checking
- Ordered delivery
- Connection management

Common TCP services:

- SSH
- HTTPS
- Databases

---

# UDP

User Datagram Protocol.

UDP provides:

- Faster communication
- Lower overhead
- No guaranteed delivery

Common UDP services:

- DNS queries
- Video streaming
- Voice communication

---

# Linux Networking Commands

Linux provides several commands for viewing and troubleshooting networking.

---

# View Network Interfaces

The `ip address` command displays network interfaces and IP addresses.

```bash
ip address
```

Example output:

```text
eth0

inet 192.168.1.50/24
```

---

# View Routing Information

The routing table shows where traffic is sent.

```bash
ip route
```

Example:

```text
default via 192.168.1.1 dev eth0
```

---

# Test Connectivity

The `ping` command tests whether another device can be reached.

```bash
ping 8.8.8.8
```

Example uses:

- Testing network connectivity
- Checking if a host responds

---

# DNS Lookup

The `nslookup` command checks DNS resolution.

```bash
nslookup google.com
```

Example:

```text
Name:

google.com

Address:

142.250.x.x
```

---

# View Network Connections

The `ss` command shows network sockets and listening services.

```bash
ss -tulnp
```

This can show:

- Open ports
- Running network services
- Listening applications

---

# Practical Lab

The objective of this lab is to explore basic networking information on a Linux system.

Tasks:

- Identify network interfaces
- View IP addresses
- View routing information
- Test connectivity
- Check network services

---

# Lab 1 - View Network Interfaces

Run:

```bash
ip address
```

Identify:

- Network interface name
- IP address
- MAC address

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

# Lab 3 - Test Connectivity

Test internet connectivity:

```bash
ping 8.8.8.8
```

Test DNS:

```bash
ping google.com
```

---

# Lab 4 - View Network Services

Run:

```bash
ss -tulnp
```

Identify:

- Listening services
- Open ports
- Running applications

---

# Lab Challenge

A Linux server cannot access a website.

Describe the troubleshooting process:

1. Check the network interface
2. Confirm the IP address
3. Check the default gateway
4. Test network connectivity
5. Test DNS resolution
6. Check listening services
7. Check firewall rules

---

# Summary

In this lesson you learned:

- What networks are
- How devices communicate
- The purpose of IP addresses
- The role of MAC addresses
- How routers and gateways work
- How DNS translates names into addresses
- How ports identify services
- Basic Linux networking commands

The next lesson covers:

```text
Lesson 02 - IP Addressing and Subnetting
```
