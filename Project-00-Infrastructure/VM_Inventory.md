# VM Inventory

## Overview

This document provides an inventory of the virtual machines used to build the SQL Server 2019 Enterprise lab environment.

---

## Virtual Machine Specifications

| Server | Role | Operating System | SQL Version | vCPU | RAM | Disk | IP Address | Domain |
|---------|------|------------------|-------------|------|-----|------|------------|--------|
| JITDC | Domain Controller | Windows Server 2019 | N/A | 1 | 2 GB | 100 GB | 192.168.0.2 | Cyning.com |
| JITSQL01 | Primary SQL Server | Windows Server 2019 | SQL Server 2019 Enterprise | 1 | 4 GB | 100 GB | 192.168.0.3 | Cyning.com |
| JITSQL02 | Secondary SQL Server | Windows Server 2019 | SQL Server 2019 Enterprise | 1 | 4 GB | 100 GB | 192.168.0.4 | Cyning.com |

---

## Server Roles

### JITDC

Purpose:

- Active Directory Domain Services (AD DS)
- DNS Server
- Domain authentication
- User and Group Management
- SQL Server service account authentication

---

### JITSQL01

Purpose:

- Primary SQL Server 2019 Enterprise instance
- SQL Server administration
- Backup and Restore
- Performance tuning
- Security administration
- High Availability configuration
- Disaster Recovery testing

---

### JITSQL02

Purpose:

- Secondary SQL Server 2019 Enterprise instance
- Always On Availability Groups
- Windows Server Failover Clustering (WSFC)
- Disaster Recovery validation
- Failover testing

---

## Environment Summary

| Component | Configuration |
|----------|---------------|
| Hypervisor | Microsoft Hyper-V |
| Domain | Cyning.com |
| Active Directory | Windows Server 2019 |
| DNS | JITDC |
| SQL Server Version | SQL Server 2019 Enterprise Edition |
| Authentication | Windows Authentication |
| Network | Static IPv4 |

---

## Validation

The inventory was validated using:

```cmd
hostname

systeminfo

ipconfig /all
```

---

## Lessons Learned

- Dedicated SQL Server nodes simplify High Availability and Disaster Recovery testing.
- Static IP addressing ensures consistent communication between SQL Server instances and the Domain Controller.
- Documenting virtual machine specifications provides a baseline for future troubleshooting, capacity planning, and infrastructure changes.
