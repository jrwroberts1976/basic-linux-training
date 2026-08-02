Lesson 01 - Networking Fundamentals
Overview

Networking is a core skill for Linux administrators, cloud engineers, and DevOps professionals.

Linux systems rely heavily on networking for communication between servers, applications, containers, and cloud platforms.

This lesson introduces the fundamental concepts required to understand how devices communicate across networks.

Topics Covered
Network fundamentals
IP addresses
IPv4 and IPv6
Subnets
MAC addresses
Default gateways
DNS
Ports and protocols
Network troubleshooting commands
Learning Objectives

By the end of this lesson you should understand:

How computers communicate across networks
The difference between IP addresses and MAC addresses
How subnetting works at a basic level
The purpose of gateways and DNS
Common network protocols
How to troubleshoot basic connectivity issues in Linux
What Is a Network?

A network allows devices to communicate and exchange data.

Examples of networked devices:

Computers
Servers
Routers
Switches
Mobile devices
IoT devices
Cloud infrastructure

A simple network:

Computer
    |
 Switch
    |
 Router
    |
 Internet

Networks allow systems to share:

Data
Applications
Services
Internet access
Storage
IP Addresses

An IP address identifies a device on a network.

Example IPv4 address:

192.168.1.50

An IP address contains:

Network portion
Host portion

Example:

192.168.1.50

Network: 192.168.1
Host:    50

Common private network ranges:

Range	Purpose
10.0.0.0/8	Private networks
172.16.0.0/12	Private networks
192.168.0.0/16	Home and small business networks

Example home network:

Router:  192.168.1.1
Laptop:  192.168.1.20
Server:  192.168.1.50
Printer: 192.168.1.100
IPv4 and IPv6
IPv4

IPv4 uses 32-bit addresses.

Example:

192.168.1.50

IPv4 has a limited number of available addresses.

IPv6

IPv6 uses 128-bit addresses.

Example:

2001:db8:abcd::1

IPv6 provides a much larger address space and was designed to replace IPv4.

MAC Addresses

A MAC address identifies a network interface at the hardware level.

Example:

00:1A:2B:3C:4D:5E

Characteristics:

Assigned to network hardware
Used by switches
Operates at Layer 2 of the OSI model

Example:

Laptop
  |
MAC Address
  |
Switch
  |
Router
Subnets

A subnet divides a network into smaller sections.

Example:

192.168.1.0/24

This means:

Network: 192.168.1.0
Available hosts: 192.168.1.1 - 192.168.1.254
Broadcast: 192.168.1.255

A /24 network contains:

256 total addresses
254 usable addresses
Default Gateway

The default gateway is the device that forwards traffic to other networks.

In most home networks this is the router.

Example:

Laptop
192.168.1.20

      |
      |
Gateway
192.168.1.1

      |
      |
Internet

Without a gateway, a device can only communicate with its local network.

DNS

DNS (Domain Name System) converts names into IP addresses.

Humans use:

www.example.com

Computers use:

93.184.216.34

DNS lookup process:

User
 |
Domain Name
 |
DNS Server
 |
IP Address

Common public DNS servers:

Google DNS:
8.8.8.8

Cloudflare DNS:
1.1.1.1
Ports and Protocols

Ports identify network services running on a system.

Example:

192.168.1.50:22

Means:

IP address: 192.168.1.50
Port: 22

Common ports:

Port	Protocol	Purpose
22	SSH	Remote administration
53	DNS	Name resolution
80	HTTP	Web traffic
443	HTTPS	Secure web traffic
3306	MySQL	Database
5432	PostgreSQL	Database
Common Network Protocols
TCP

Transmission Control Protocol.

Features:

Reliable delivery
Connection based
Ensures packets arrive correctly

Examples:

SSH
HTTPS
Databases
UDP

User Datagram Protocol.

Features:

Faster communication
No connection tracking
Does not guarantee delivery

Examples:

DNS queries
Streaming
Voice communication
Linux Networking Commands
View Network Interfaces
ip addr

Shows:

Network interfaces
IP addresses
Network configuration
View Routing Information
ip route

Example:

default via 192.168.1.1
Test Connectivity

Test an IP address:

ping 8.8.8.8

Test DNS resolution:

ping google.com
DNS Lookup

Using nslookup:

nslookup google.com

Using dig:

dig google.com
Check Open Ports
ss -tulnp

Shows:

Listening services
Ports
Processes
Test Web Services
curl http://example.com

Useful for testing HTTP connectivity.

Network Troubleshooting Process

When a Linux system cannot access a service:

Step 1 - Check Network Interface
ip addr

Check that the interface is active.

Step 2 - Check IP Address

Confirm the system has a valid IP address.

Example:

192.168.1.50
Step 3 - Check Default Gateway
ip route

Confirm a route exists.

Step 4 - Test IP Connectivity
ping 8.8.8.8
Step 5 - Test DNS
nslookup google.com
Step 6 - Check Services
ss -tulnp
Practical Exercises
Exercise 1 - View Network Configuration

Run:

ip addr

Record:

Network interface name
IP address
Network mask
Exercise 2 - View Routing

Run:

ip route

Identify:

Default gateway
Network routes
Exercise 3 - Test DNS

Run:

nslookup google.com

Identify:

DNS server used
Returned IP address
Exercise 4 - Check Listening Services

Run:

ss -tulnp

Identify:

Running network services
Ports in use
Administrator Challenge

A Linux server cannot access the internet.

Describe the troubleshooting steps:

Check the network interface
Check the IP address
Check the default gateway
Test external IP connectivity
Test DNS resolution
Check firewall rules
Check running services
Key Commands
Command	Purpose
ip addr	Show network interfaces
ip route	Show routing information
ping	Test connectivity
nslookup	DNS lookup
dig	Detailed DNS lookup
ss	Show network sockets
curl	Test HTTP services
traceroute	Trace network path
Lesson Status

✅ Completed
