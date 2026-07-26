# Active Directory Configuration

## Overview

This document describes the deployment and configuration of Active Directory Domain Services (AD DS) for the SQL Server lab environment. Active Directory provides centralized authentication, authorization, and directory services for all domain-joined servers. It also enables Windows Authentication, centralized management, and supports enterprise SQL Server features such as Windows Server Failover Clustering (WSFC) and Always On Availability Groups.

---

## Domain Information

| Property | Value |
|----------|-------|
| Forest Name | cyning.com |
| Domain Name | cyning.com |
| NetBIOS Name | CYNING |
| Forest Functional Level | Windows Server 2019 |
| Domain Functional Level | Windows Server 2019 |

---

## Domain Controller

| Property | Value |
|----------|-------|
| Hostname | JITDC |
| Operating System | Windows Server 2019 |
| Installed Roles | Active Directory Domain Services (AD DS), DNS Server |

---

## Organizational Units (OUs)

At the time of writing, the default Active Directory Organizational Unit structure is being used. Dedicated OUs for SQL Server infrastructure will be implemented as the environment expands.

---

## Service Accounts

The following domain service accounts have been created.

| Account | Purpose |
|---------|---------|
| sqlsrvc01 | SQL Server Database Engine Service |
| sqlsagt01 | SQL Server Agent Service |

These accounts will be assigned the minimum permissions required to support SQL Server services in accordance with the principle of least privilege.

---

## Administrative User Accounts

The following administrative accounts have been created.

| User | Purpose |
|------|---------|
| clusteradmin | Windows Server Failover Cluster Administration |
| dbadmin | SQL Server Administration |
| owner | Lab Administration |

---

## Domain Members

| Computer | Role | Domain Joined |
|----------|------|---------------|
| JITDC | Domain Controller | Yes |
| JITSQL01 | SQL Server Node 1 | Yes |
| JITSQL02 | SQL Server Node 2 | Yes |

---

## Domain Join Process

The SQL Server virtual machines were joined to the Active Directory domain using the following process:

1. Assigned static IP addresses.
2. Configured JITDC as the preferred DNS server.
3. Verified network connectivity.
4. Joined JITSQL01 and JITSQL02 to the cyning.com domain.
5. Restarted both servers.
6. Logged on using domain credentials.

---

## Validation

The Active Directory deployment was validated using the following methods.

### Domain Membership

Verified that both SQL Server virtual machines were successfully joined to the domain.

### Authentication

Validated successful authentication using domain user accounts.

### DNS Resolution

Confirmed successful forward name resolution using DNS.

### Connectivity

Confirmed communication between all domain members.

### Validation Commands

```cmd
whoami

echo %USERDOMAIN%

ping JITDC

nslookup JITSQL01

nslookup JITSQL02
```

---

## Screenshots

The following screenshots are included in the Images folder.

- Hyper-V Manager
- Active Directory Users and Computers
- DNS Manager
- JITDC Server Manager
- Domain membership (JITSQL01)
- Domain membership (JITSQL02)
- Successful `whoami`
- Successful `ping`
- Successful `nslookup`

---

## Lessons Learned

- Active Directory centralizes authentication and authorization for SQL Server.
- DNS must be correctly configured before domain joining SQL Server hosts.
- Dedicated service accounts improve security and simplify SQL Server administration.
- Windows Authentication provides secure, centralized access management for SQL Server environments.
