# Network Configuration

## Overview

This document describes the network configuration for the SQL Server 2019 lab environment hosted on Microsoft Hyper-V.

The environment consists of one Domain Controller and two SQL Server virtual machines connected through a dedicated Hyper-V virtual network. Static IPv4 addressing was implemented to provide consistent network communication and support Active Directory, DNS, SQL Server, and future Windows Server Failover Clustering (WSFC) configuration.

---

## Network Architecture

The environment contains the following servers:

| Server | Role |
|---------|------|
| JITDC | Active Directory Domain Controller and DNS Server |
| JITSQL01 | Primary SQL Server 2019 Enterprise |
| JITSQL02 | Secondary SQL Server 2019 Enterprise |

---

## IP Addressing

| Server | IPv4 Address | Subnet Mask | DNS Server | DHCP |
|---------|--------------|-------------|------------|------|
| JITDC | 192.168.0.2 | 255.255.255.0 | 192.168.0.2 | Disabled |
| JITSQL01 | 192.168.0.3 | 255.255.255.0 | 192.168.0.2 | Disabled |
| JITSQL02 | 192.168.0.4 | 255.255.255.0 | 192.168.0.2 | Disabled |

---

## DNS Configuration

The Domain Controller (JITDC) hosts the DNS Server role and provides name resolution for all domain-joined virtual machines.

All SQL Server nodes are configured to use JITDC (192.168.0.2) as their preferred DNS server.

---

## Network Configuration

- Static IPv4 addressing configured on all servers.
- DHCP disabled on all network adapters.
- NetBIOS over TCP/IP enabled.
- Microsoft Hyper-V Network Adapter installed on each virtual machine.
- All servers successfully joined to the Cyning.com Active Directory domain.

---

## Network Validation

The following tests were completed successfully:

### IP Configuration

```cmd
ipconfig /all
```

### Connectivity

```cmd
ping JITDC

ping JITSQL01

ping JITSQL02
```

### DNS Resolution

```cmd
nslookup JITDC

nslookup JITSQL01

nslookup JITSQL02
```

All validation tests confirmed successful communication between the domain controller and SQL Server nodes.

---

## Screenshots

- JITDC IP Configuration
- JITSQL01 IP Configuration
- JITSQL02 IP Configuration
- Successful Ping Test
- Successful nslookup Test

---

                    Hyper-V Host
                          │
                    Virtual Switch
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
        │                 │                 │
   +------------+   +--------------+   +--------------+
   |   JITDC    |   |  JITSQL01    |   |  JITSQL02    |
   |------------|   |--------------|   |--------------|
   | AD DS      |   | SQL Server   |   | SQL Server   |
   | DNS        |   | Enterprise   |   | Enterprise   |
   |192.168.0.2 |   |192.168.0.3   |   |192.168.0.4   |
   +------------+   +--------------+   +--------------+

## Lessons Learned

- Static IP addresses are recommended for infrastructure servers to ensure reliable communication.
- SQL Server environments rely on Active Directory and DNS for Windows Authentication and name resolution.
- Consistent network configuration simplifies future implementation of Windows Server Failover Clustering and Always On Availability Groups.
