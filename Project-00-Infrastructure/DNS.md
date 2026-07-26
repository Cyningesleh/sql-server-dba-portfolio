# DNS Configuration

## Overview

This document describes the Domain Name System (DNS) configuration for the SQL Server lab environment.

DNS is hosted on the Domain Controller (JITDC) and provides name resolution for all domain-joined servers. Proper DNS configuration is critical for Active Directory, SQL Server authentication, Windows Server Failover Clustering (WSFC), and Always On Availability Groups.

---

# DNS Server Information

| Property | Value |
|----------|-------|
| Server Name | JITDC |
| Operating System | Windows Server 2019 |
| DNS Role | Installed |
| Active Directory Integrated | Yes |

---

# Forward Lookup Zones

The following Forward Lookup Zones were configured.

| Zone | Purpose |
|------|---------|
| Cyning.com | Primary Active Directory DNS Zone |
| _msdcs.Cyning.com | Active Directory Service Location Records |

The `_msdcs` zone was automatically created during the Active Directory installation to support domain controller location and replication.

---

# Reverse Lookup Zone

| Zone | Purpose |
|------|---------|
| 0.168.192.in-addr.arpa | Reverse DNS Lookup |

The Reverse Lookup Zone enables reverse name resolution from IP addresses to hostnames and assists with network troubleshooting and validation.

---

# DNS Records

The DNS server maintains host records for all domain-joined systems.

Current hosts include:

- JITDC
- JITSQL01
- JITSQL02

---

# DNS Client Configuration

All SQL Server virtual machines were configured to use JITDC as their preferred DNS server.

This enables:

- Active Directory authentication
- Hostname resolution
- Windows Authentication
- SQL Server connectivity
- Cluster communication

---

# Validation

The DNS configuration was validated using the following commands.

## Name Resolution

```cmd
nslookup JITDC

nslookup JITSQL01

nslookup JITSQL02
```

## Connectivity

```cmd
ping JITDC

ping JITSQL01

ping JITSQL02
```

Successful responses confirmed proper DNS resolution and communication between all servers.

---

# Screenshots

Included in the Images folder:

- DNS Manager
- Forward Lookup Zones
- Reverse Lookup Zone
- nslookup Results
- ping Results

---

# Lessons Learned

- DNS is a core dependency for Active Directory.
- SQL Server environments rely on accurate DNS records for connectivity.
- Reverse Lookup Zones improve troubleshooting and network administration.
- Proper DNS configuration is essential before implementing Windows Server Failover Clustering and Always On Availability Groups.
