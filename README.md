# 🔐 Cybersecurity Homelab Portfolio

## Overview

This project documents the design, deployment, and troubleshooting of a multi-system cybersecurity homelab built to develop hands-on experience in system administration, security monitoring, networking, virtualization, and defensive security operations.

The lab simulates a small enterprise environment consisting of Active Directory, Windows endpoints, Linux servers, and security monitoring platforms. Throughout the project, significant emphasis was placed on troubleshooting real-world infrastructure issues involving DNS, routing, authentication, virtualization, service deployment, and SIEM integration.

---

# 🏗️ Lab Architecture

```text
                    Internet
                        │
                   NAT Adapter
                        │
          ┌─────────────┴─────────────┐
          │                           │
     Ubuntu Server               Future Kali Linux
      (Wazuh/Splunk)            (Security Testing)
          │
─────────────────────────────────────────────
      Host-Only Internal Network
          │
    ┌───────────┬────────────┐
    │           │            │
Windows Server  Windows 10   Metasploitable
(AD/DC/DNS)     Workstation  Vulnerable Host
```

---

# 💻 Technologies Used

### Operating Systems
- Windows Server
- Windows 10
- Ubuntu Linux
- Metasploitable 2

### Security Tools
- Wazuh
- Splunk
- Nmap
- Wireshark

### Infrastructure
- VMware Workstation
- Active Directory
- DNS
- Group Policy
- PowerShell
- Bash

---

# 📁 Project 1: Active Directory Deployment

## Objective

Create and administer an enterprise-style Active Directory environment to gain experience with centralized identity and access management.

## Tasks Completed

- Installed Windows Server
- Deployed Active Directory Domain Services (AD DS)
- Promoted server to Domain Controller
- Configured DNS services
- Created domain users and groups
- Joined Windows 10 workstation to the domain
- Verified domain authentication
- Organized resources with Organizational Units (OUs)
- Implemented Role-Based Access Control (RBAC)

## Skills Demonstrated

- Active Directory Administration
- Identity and Access Management (IAM)
- DNS Administration
- Windows Server Management
- User and Group Management
- Authentication Services

## Outcome

Successfully deployed a functional Active Directory domain capable of managing users, systems, and authentication through centralized administration.

---

# 🔒 Project 2: Group Policy Security Hardening

## Objective

Implement centralized security controls across the Active Directory environment.

## Tasks Completed

- Created Organizational Units (OUs)
- Configured security groups
- Designed Role-Based Access Control structure
- Created and linked Group Policy Objects (GPOs)
- Configured password complexity requirements
- Configured account lockout policies
- Tested policy deployment to domain clients

## Security Controls Implemented

### Password Policy

- Password complexity enabled
- Minimum password length requirements
- Password aging controls

### Account Security

- Account lockout thresholds
- Lockout duration policies
- Authentication protections

## Skills Demonstrated

- Group Policy Administration
- Windows Security Hardening
- Access Control
- Enterprise Security Management

## Outcome

Established centralized security management and policy enforcement across the domain environment.

---

# 🌐 Project 3: VMware Networking and Infrastructure Troubleshooting

## Objective

Troubleshoot connectivity issues preventing software deployment and communication across lab systems.

## Challenges Encountered

### Issue 1: Ubuntu Could Reach Domain Resources But Not The Internet

Symptoms:

```text
Can ping Domain Controller
Cannot ping 8.8.8.8
Cannot resolve external hosts
Cannot download Wazuh packages
```

## Investigation

Used Linux networking tools:

```bash
ip addr
ip route
cat /etc/resolv.conf
ping
curl
```

## Root Cause

The Ubuntu VM only possessed a Host-Only network adapter.

Routing table contained:

```text
192.168.56.0/24
```

but lacked a:

```text
default gateway
```

## Resolution

Added a second VMware NAT adapter while maintaining the Host-Only adapter for internal communication.

Final configuration:

```text
Adapter 1: Host-Only
Adapter 2: NAT
```

## Outcome

Successfully restored Internet access while maintaining isolated internal lab communications.

---

# 🐧 Project 4: Ubuntu Linux Administration and Troubleshooting

## Objective

Deploy Ubuntu Linux as a centralized security operations platform.

## Challenges Encountered

### DNS Resolution Failures

Observed:

```text
Temporary failure in name resolution
```

### Connectivity Validation

Performed testing with:

```bash
ping
curl
resolvectl
```

### Wazuh Installation Failure

Installer terminated with:

```text
Current system does not match with list of recommended systems
```

## Investigation

Reviewed installation logs:

```bash
/var/log/wazuh-install.log
```

Determined:

```text
Ubuntu 26.04.1
```

was not currently supported by the Wazuh installation assistant.

## Skills Demonstrated

- Linux Administration
- DNS Troubleshooting
- Routing Analysis
- Service Deployment
- Log Analysis
- Infrastructure Troubleshooting

## Outcome

Successfully identified and documented compatibility limitations while validating all prerequisite networking and connectivity requirements.

---

# 📊 Project 5: SIEM and Security Monitoring

## Objective

Develop a Security Operations Center (SOC) style monitoring platform for centralized event collection and analysis.

## Planned Monitoring Use Cases

### Authentication Monitoring

- Successful Logons
- Failed Logons
- Account Lockouts

### Active Directory Monitoring

- User Creation
- Password Changes
- Group Membership Changes
- Privilege Escalation Activities

### Security Operations

- Alert Creation
- Event Correlation
- Incident Investigation
- Log Management

## Skills Developed

- SIEM Concepts
- Event Analysis
- Security Monitoring
- Threat Detection
- Log Management

---

# 🎯 Project 6: Vulnerable Host Administration

## Objective

Create realistic targets for future security testing exercises.

## Tasks Completed

- Deployed Metasploitable 2
- Troubleshot network interfaces
- Configured networking
- Investigated DHCP issues
- Tested static IP assignments
- Verified lab connectivity

## Skills Demonstrated

- Linux Networking
- Vulnerability Research
- Infrastructure Troubleshooting
- Virtual Machine Administration

---

# 🛠️ Notable Troubleshooting Experience

Throughout the lab build process, several real-world issues were diagnosed and resolved:

✅ Active Directory domain join failures

✅ DNS configuration issues

✅ Ubuntu name resolution failures

✅ Missing default gateway configuration

✅ VMware networking misconfigurations

✅ Service startup failures

✅ Disk space limitations

✅ Splunk deployment troubleshooting

✅ Wazuh deployment troubleshooting

✅ Virtual machine connectivity issues

✅ Static IP addressing problems

✅ Authentication and domain communication issues

---

# 📚 Key Skills Developed

### Security Operations

- SIEM Administration
- Threat Detection
- Event Monitoring
- Incident Analysis

### Systems Administration

- Active Directory
- Windows Server
- Ubuntu Linux
- DNS Services
- Group Policy

### Networking

- TCP/IP
- Routing
- DNS
- VMware Virtual Networking
- Connectivity Troubleshooting

### Cybersecurity

- Identity and Access Management
- Security Hardening
- Security Monitoring
- Vulnerability Assessment Fundamentals

---

# 🚀 Future Enhancements

- Deploy Wazuh on a supported Ubuntu LTS release
- Integrate Domain Controller event logs into SIEM
- Deploy Kali Linux attack platform
- Perform Active Directory enumeration exercises
- Conduct vulnerability assessments using Nmap
- Create SOC detection and alerting rules
- Implement centralized incident response workflows

---

# 📈 Lessons Learned

This homelab provided practical experience building and troubleshooting enterprise-style infrastructure from the ground up. Through repeated problem-solving exercises involving networking, authentication, virtualization, Linux administration, and Active Directory management, I developed technical skills directly applicable to Security Operations Center (SOC), Cybersecurity Analyst, and Systems Administration roles.

The project reinforced the importance of systematic troubleshooting, documentation, and understanding how foundational technologies such as DNS, Active Directory, routing, and virtualization impact overall security operations.
