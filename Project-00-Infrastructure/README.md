# Project 00 – Enterprise Infrastructure

## Overview

This project documents the design and deployment of the infrastructure supporting an enterprise Microsoft SQL Server lab environment.

The environment was built using Microsoft Hyper-V, Windows Server 2019, Active Directory Domain Services (AD DS), and DNS. It provides the foundation for SQL Server administration, performance tuning, security, backup and recovery, high availability, and disaster recovery testing.

## Objectives

- Build an enterprise Active Directory environment.
- Deploy Windows Server virtual machines.
- Configure networking and DNS.
- Join SQL Server hosts to the domain.
- Prepare the infrastructure for SQL Server 2022 deployment.

## Technologies

- Hyper-V
- Windows Server 2019
- Active Directory Domain Services
- DNS
- PowerShell
- Windows Networking

## Virtual Machines

| Server | Role |
----------------------
| JITDC    | Domain Controller |
| JITSQL01 | SQL Server Node 1 |
| JITSQL02 | SQL Server Node 2 |

## Project Structure

- Hyper-V Configuration
- Active Directory
- DNS
- Networking
- VM Inventory
- Infrastructure Validation
