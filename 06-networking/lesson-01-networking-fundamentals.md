# Lesson 01 - Networking Fundamentals

## Overview

Networking is a fundamental skill for Linux administrators and engineers.

Linux systems rarely operate in isolation. Servers, applications, cloud platforms, and users all depend on reliable network communication.

Understanding networking fundamentals allows administrators to configure systems, troubleshoot problems, and support modern infrastructure environments.

---

## Learning Objectives

By the end of this lesson, you will understand:

- What a network is
- How computers communicate
- The role of network interfaces
- The difference between MAC addresses and IP addresses
- The basics of TCP and UDP
- How ports identify services
- Basic Linux networking commands

---

## What Is a Network?

A network is a collection of connected devices that communicate and exchange information.

Examples of network devices include:

- Servers
- Workstations
- Laptops
- Routers
- Switches
- Mobile devices
- Cloud services

Networks allow systems to:

- Share data
- Access applications
- Communicate with other systems
- Provide services to users

Examples:

- A user connecting to a website
- An administrator accessing a Linux server using SSH
- A server connecting to a database

---

## How Computers Communicate

Network communication follows a structured approach where different layers handle different responsibilities.

A simplified view:


Application
|
v
Transport
|
v
Internet
|
v
Network Interface
|
v
Physical Network


Each layer provides services to the layer above it.

For example, accessing a website involves:


Web Browser
|
v
HTTPS
|
v
TCP
|
v
IP Address
|
v
Network Interface


---

## Network Interfaces

A network interface allows a Linux system to connect to a network.

Common interface names include:


eth0
ens33
enp0s3
wlan0


Common interface types:

| Interface | Description |
|---|---|
| Ethernet | Wired network connection |
| Wireless | Wi-Fi connection |
| Loopback | Internal system communication |

The loopback interface allows a computer to communicate with itself:


lo


Example:

```bash
ping 127.0.0.1
Viewing Network Interfaces

The modern Linux networking command is:

ip address

Example:

2: eth0:
    inet 192.168.1.50/24

This provides information about:

Interface name
IP address
Network configuration
Interface state

To view interface status:

ip link
MAC Addresses

A MAC address is a unique hardware identifier assigned to a network interface.

Example:

00:1A:2B:3C:4D:5E

MAC addresses:

Identify network hardware
Operate on the local network
Are assigned to network interfaces

Examples:

Ethernet adapter
Wireless adapter
IP Addresses

An IP address identifies a device on a network.

Example:

192.168.1.100

IP addresses allow devices to communicate across networks.

Unlike MAC addresses, IP addresses:

Can change
Are assigned manually or automatically
Allow communication between different networks

Example:

Laptop
192.168.1.20

        |

Router

        |

Server
192.168.1.50
TCP and UDP

Linux systems use network protocols to communicate.

The two most common transport protocols are TCP and UDP.

TCP

Transmission Control Protocol provides reliable communication.

Characteristics:

Connection-based
Ensures data delivery
Detects errors
Maintains sessions

Examples:

SSH
HTTPS
Email
UDP

User Datagram Protocol provides faster communication.

Characteristics:

Connectionless
Lower overhead
Does not guarantee delivery

Examples:

DNS
Video streaming
Online gaming
Ports and Services

An IP address identifies a system.

A port identifies a service running on that system.

Example:

192.168.1.50:22

This means:

System:
192.168.1.50

Service:
SSH

Port:
22

Common ports:

Port	Service
22	SSH
53	DNS
80	HTTP
443	HTTPS
3306	MySQL
Linux Networking Commands
View IP configuration
ip address
View network routes
ip route
Test connectivity
ping hostname

Example:

ping google.com
View listening services
ss -tuln
Test DNS resolution
nslookup example.com
Practical Exercise
Task 1 - View Network Configuration

Run:

ip address

Identify:

Network interface name
IP address
MAC address
Task 2 - Test Connectivity

Run:

ping 8.8.8.8

Record:

Number of packets sent
Number of packets received
Response time
Task 3 - Identify Running Services

Run:

ss -tuln

Identify:

Listening ports
Services using those ports
Summary

In this lesson you learned:

What networks are
How Linux systems communicate
The purpose of network interfaces
The difference between MAC and IP addresses
How TCP and UDP work
How ports identify services
Basic Linux networking commands

These concepts provide the foundation for Linux administration, cloud platforms, containers, and troubleshooting enterprise systems.
