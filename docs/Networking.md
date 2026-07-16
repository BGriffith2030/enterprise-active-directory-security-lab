# Network Configuration

# Overview

This document describes the network design and configuration implemented for the Active Directory Domain Controller Lab.

Reliable networking is a fundamental requirement for Active Directory. Before deploying Active Directory Domain Services (AD DS), the virtual environment was configured with static IP addressing, Host-Only networking, and DNS services to provide consistent communication between infrastructure components.

The network was intentionally isolated from the production environment to provide a safe and repeatable testing platform.

---

# Network Objectives

The networking configuration was designed to:

- Isolate the lab from the production network.
- Provide reliable communication between virtual machines.
- Support Active Directory Domain Services.
- Provide DNS name resolution.
- Use static IP addressing for infrastructure services.
- Create a repeatable enterprise-style network.

---

# Virtual Network

The lab uses Oracle VirtualBox Host-Only Networking.

Host-Only networking creates a private network shared between the host computer and virtual machines while preventing direct access to the external network.

Benefits include:

- Safe testing environment
- Predictable addressing
- Simplified troubleshooting
- Isolation from production systems
- Reliable communication between virtual machines

---

# IP Addressing

The Domain Controller was configured with a static IPv4 address.

| Device | Hostname | IPv4 Address | Purpose |
|---------|----------|--------------|---------|
| Domain Controller | DC01 | 192.168.56.101 | Active Directory & DNS |

Subnet Mask

```
255.255.255.0
```

Using a static IP address ensures that Active Directory and DNS services remain consistently reachable by client systems.

---

# DNS Configuration

The Domain Controller also serves as the DNS server for the environment.

DNS responsibilities include:

- Name resolution
- Active Directory service discovery
- Domain authentication support

Without properly configured DNS, Active Directory clients cannot locate or communicate with the Domain Controller.

---

# Network Adapter Configuration

The Domain Controller virtual machine was configured using Oracle VirtualBox virtual network adapters.

The Host-Only adapter was used to provide communication between virtual machines while maintaining network isolation.

Network configuration included:

- Host-Only Adapter
- Static IPv4 assignment
- DNS configuration
- Connectivity verification

---

# Network Verification

After configuration, several tests were performed to verify proper network operation.

## IP Configuration

The following command was used to verify network configuration.

```cmd
ipconfig
```

This confirmed:

- IPv4 address
- Subnet mask
- DNS configuration

---

## Connectivity Testing

Network communication was verified using:

```cmd
ping
```

Successful ping responses confirmed that the Domain Controller was reachable over the virtual network.

---

## DNS Testing

DNS functionality was verified using:

```cmd
nslookup
```

This confirmed that the DNS service could resolve the Active Directory domain and respond to client queries.

---

# Why Networking Matters in Active Directory

Active Directory depends heavily on networking.

Core services require:

- Reliable IP addressing
- Proper DNS configuration
- Stable communication between systems

If networking is incorrectly configured, common issues include:

- Clients unable to locate the Domain Controller
- Authentication failures
- Group Policy failures
- DNS resolution errors
- Domain join failures

Understanding these relationships is critical for Windows Server administration and enterprise troubleshooting.

---

# Troubleshooting Performed

During deployment, several networking issues were identified and resolved.

Examples included:

- Incorrect virtual adapter selection
- Static IP configuration verification
- DNS configuration testing
- Connectivity verification using ping
- DNS verification using nslookup

Documenting these troubleshooting steps provided valuable experience with diagnosing enterprise network issues.

---

# Lessons Learned

Key networking concepts reinforced during this project include:

- Static IP addresses should be used for infrastructure servers.
- DNS is essential for Active Directory functionality.
- Host-Only networking provides an excellent environment for isolated testing.
- Basic network tools such as ipconfig, ping, and nslookup are critical for troubleshooting.
- Proper planning simplifies deployment and reduces configuration errors.

---

# Summary

The networking configuration established a reliable foundation for the Active Directory deployment.

By combining Host-Only networking, static IP addressing, DNS, and systematic connectivity testing, the lab successfully simulated the networking fundamentals required for a Windows Server domain environment.

This network design also provides a scalable foundation for future enhancements, including Windows client integration, Group Policy deployment, file sharing, and additional enterprise infrastructure components.
