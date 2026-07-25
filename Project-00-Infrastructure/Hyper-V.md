# Hyper-V Configuration

## Host Environment

- Host Operating System: Windows 10 pro
- Hyper-V Version: Microsoft Hyper-v
- Processor: Intel core i5-7300HQ
- Installed Memory: 16 GB RAM
- Storage: 512 GB SSD

## Virtual Switch

- Type: Internal
- Purpose: Provide communication between the Hyper-V host and all virtual machines for the SQL Server lab environment.
- Connected Virtual Machines: - JITDC, JITSQL01, JITSQL02

## Virtual Machines

Describe the virtual machines created and the role of each.

### JITDC

Role:
Primary Domain Controller

Responsibilities:

- Active Directory Domain Services
- DNS Server
- Domain Authentication
- Centralized User Management

### JITSQL01

Role:
Primary SQL Server

Responsibilities:

- SQL Server 2019
- Database Administration
- Performance Tuning
- Backup and Recovery
- High Availability Testing

### JITSQL02

Role:
Secondary SQL Server

Responsibilities:

- SQL Server 2019
- Always On Availability Groups
- Failover Testing
- Disaster Recovery
