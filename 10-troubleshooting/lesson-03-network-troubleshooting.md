# Lesson 03 - Network Troubleshooting

> **Estimated time:** 60–90 minutes
>
> **Prerequisites:**
> - Module 06 – Networking Fundamentals
> - Module 10 – Linux Troubleshooting Fundamentals
>
> **Difficulty:** Beginner
>
> **Hands-on exercises:** Yes

---

# Overview

Network problems are one of the most common issues Linux administrators troubleshoot.

Applications, services, and users depend on reliable network connectivity.

Network failures can be caused by:

- Incorrect IP configuration
- DNS problems
- Routing issues
- Firewall rules
- Service failures
- Hardware problems

A structured approach helps identify where the problem exists.

---

# Learning Objectives

By completing this lesson you will understand:

- A network troubleshooting process
- How to check network configuration
- How to test connectivity
- How to troubleshoot DNS problems
- How to investigate ports and services
- How to analyse network routes
- Common network troubleshooting tools

---

# Network Troubleshooting Methodology

A good troubleshooting process follows the network path.

```text
Physical Connection

        |

Network Interface

        |

IP Configuration

        |

Routing

        |

DNS

        |

Application Service
```

---

# Step 1 - Check the Network Interface

The first step is confirming the network interface exists.

View interfaces:

```bash
ip link
```

Example:

```text
eth0

state UP
```

A working interface should show:

```text
UP
```

---

# Step 2 - Check IP Configuration

View IP addresses:

```bash
ip address
```

Example:

```text
inet 192.168.1.50/24
```

Check:

- Correct IP address
- Correct subnet
- Active interface

---

# Common IP Problems

Symptoms:

```text
Cannot communicate with network
```

Possible causes:

- No IP address
- Incorrect subnet
- Disabled interface

---

# Step 3 - Check Routing

The routing table determines where traffic is sent.

View routes:

```bash
ip route
```

Example:

```text
default via 192.168.1.1
```

The default route should normally point to the gateway.

---

# Common Routing Problems

Symptoms:

```text
Local network works

Internet does not work
```

Check:

```bash
ip route
```

Possible causes:

- Missing gateway
- Incorrect route
- Wrong interface

---

# Step 4 - Test Local Connectivity

Test the local network.

Ping the gateway:

```bash
ping 192.168.1.1
```

Successful response:

```text
64 bytes from 192.168.1.1
```

Failure may indicate:

- Network cable issue
- Wi-Fi issue
- Interface problem
- Firewall blocking traffic

---

# Step 5 - Test Internet Connectivity

Test an external IP address:

```bash
ping 8.8.8.8
```

If this works:

```text
Network connectivity exists
```

If it fails:

```text
Investigate routing and firewall
```

---

# Step 6 - Troubleshoot DNS

DNS converts names into IP addresses.

Example:

```text
google.com

        |

142.250.x.x
```

---

# Test DNS Resolution

Use:

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

# Check DNS Configuration

View DNS settings:

```bash
cat /etc/resolv.conf
```

Example:

```text
nameserver 1.1.1.1
```

---

# DNS Troubleshooting Process

If:

```bash
ping 8.8.8.8
```

works

but:

```bash
ping google.com
```

fails

The problem is likely DNS.

---

# Step 7 - Check Listening Services

A service may be running but unavailable.

View listening ports:

```bash
ss -tulnp
```

Example:

```text
LISTEN

0.0.0.0:443
```

Check:

- Service running
- Correct port
- Correct address binding

---

# Testing Ports

Test if a port is reachable:

```bash
nc -zv hostname port
```

Example:

```bash
nc -zv server 443
```

---

# Firewall Troubleshooting

A firewall can block valid traffic.

Check UFW:

```bash
sudo ufw status
```

Check nftables:

```bash
sudo nft list ruleset
```

---

# Network Tools Reference

| Command | Purpose |
|---|---|
| `ip address` | View IP configuration |
| `ip route` | View routes |
| `ping` | Test connectivity |
| `traceroute` | View network path |
| `nslookup` | DNS testing |
| `dig` | DNS troubleshooting |
| `ss` | View ports |
| `curl` | Test applications |

---

# Traceroute

Traceroute shows the path traffic takes.

Install if required:

```bash
sudo apt install traceroute
```

Run:

```bash
traceroute google.com
```

Example:

```text
Computer

 |

Router

 |

ISP

 |

Destination
```

---

# Curl Testing

curl can test application connectivity.

Example:

```bash
curl https://example.com
```

Useful for:

- Web services
- APIs
- HTTP troubleshooting

---

# Common Network Problems

---

# Cannot Reach Internet

Check:

```bash
ip address

ip route

ping 8.8.8.8
```

---

# DNS Failure

Check:

```bash
cat /etc/resolv.conf

nslookup google.com
```

---

# Service Not Accessible

Check:

```bash
ss -tulnp

systemctl status service-name
```

---

# Firewall Blocking Traffic

Check:

```bash
sudo ufw status

sudo nft list ruleset
```

---

# Practical Lab

The objective of this lab is to troubleshoot network connectivity.

Tasks:

- Check network configuration
- Test connectivity
- Diagnose DNS
- Check services

---

# Lab 1 - View Network Configuration

Run:

```bash
ip address

ip route
```

Record:

- IP address
- Interface
- Gateway

---

# Lab 2 - Test Connectivity

Run:

```bash
ping 8.8.8.8
```

Then:

```bash
ping google.com
```

Compare results.

---

# Lab 3 - Test DNS

Run:

```bash
nslookup google.com
```

Identify:

- DNS server
- Returned IP address

---

# Lab 4 - Check Services

Run:

```bash
ss -tulnp
```

Identify:

- Listening services
- Open ports

---

# Lab Challenge

A user reports:

```text
The website cannot be accessed.
```

The server is running Linux.

Create a troubleshooting plan.

Check:

1. Network interface
2. IP address
3. Gateway
4. DNS
5. Firewall
6. Web service
7. Application logs

Explain how you would identify the failure point.

---

# Summary

In this lesson you learned:

- A structured network troubleshooting approach
- How to check interfaces and IP addresses
- How to test connectivity
- How to troubleshoot DNS
- How to investigate ports and services
- How firewalls affect networking

The next lesson covers:

```text
Lesson 04 - Performance Troubleshooting
```
