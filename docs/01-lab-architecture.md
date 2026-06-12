# Lab Architecture

## Infrastructure Overview

The lab consists of virtualized systems connected through an internal VirtualBox network, simulating a small enterprise environment with centralized SIEM monitoring.

| Component | Role | IP Address |
|-----------|------|------------|
| Windows Server 2022 | Active Directory / DNS / DHCP | 192.168.56.100 |
| Ubuntu Server | Splunk Enterprise SIEM | 192.168.56.10 |
| Windows Client | Domain-joined endpoint | DHCP (192.168.56.x) |

**Domain**: corp.org
**Network**: 192.168.56.0/24

## Data Flow

The Splunk Universal Forwarder installed on the Domain Controller collects Windows Event Logs (Security, System, Application) and forwards them to the Splunk Indexer on port 9997/TCP. The SOC analyst accesses Splunk Web on port 8000 to search, create dashboards, and investigate events.

```
Windows Domain Controller  --->  Universal Forwarder  --->  Splunk Indexer
    (generates logs)              (collects & sends)        (192.168.56.10:9997)
                                                                    |
                                                          Splunk Web UI :8000
                                                                    |
                                                              SOC Analyst
```

## Component Responsibilities

- **Active Directory**: Authentication, authorization, group policy
- **DNS**: Name resolution for corp.org
- **DHCP**: Automatic IP assignment to clients
- **Splunk Enterprise**: Log ingestion, indexing, search, dashboarding
- **Universal Forwarder**: Lightweight log collection agent on Windows
