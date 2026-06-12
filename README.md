# Enterprise SIEM Lab

A virtualized enterprise lab environment for security monitoring, log ingestion, and threat detection. Built with Windows Active Directory and Splunk SIEM, with room to expand across additional platforms and tools.

## Repository Structure

```
enterprise-siem-lab/
├── README.md
├── docs/
│   ├── 01-lab-architecture.md
│   ├── 02-splunk-overview.md
│   ├── 03-splunk-components.md
│   ├── 04-forwarders.md
│   ├── 05-deployment-architecture.md
│   ├── 06-implementation-guide.md
│   ├── 07-event-log-collection.md
│   ├── 08-spl-queries.md
│   ├── 09-dashboards.md
│   └── screenshots.md
├── spl/
│   ├── authentication.spl
│   ├── kerberos.spl
│   ├── processes.spl
│   ├── privileged-activity.spl
│   └── volume-monitoring.spl
└── screenshots/
```

## Contents

| Document | Description |
|----------|-------------|
| [01-lab-architecture.md](docs/01-lab-architecture.md) | Lab infrastructure, network topology, component roles |
| [02-splunk-overview.md](docs/02-splunk-overview.md) | Splunk Cloud vs Enterprise, deployment models, licensing |
| [03-splunk-components.md](docs/03-splunk-components.md) | Forwarder, Indexer, Search Head — one installer, three roles |
| [04-forwarders.md](docs/04-forwarders.md) | Universal Forwarder vs Heavy Forwarder comparison |
| [05-deployment-architecture.md](docs/05-deployment-architecture.md) | Single instance, distributed, and clustered architectures |
| [06-implementation-guide.md](docs/06-implementation-guide.md) | Step-by-step AD setup, Splunk install, UF configuration |
| [07-event-log-collection.md](docs/07-event-log-collection.md) | Windows Event IDs (4624, 4625, 4768–4771, 4688, etc.), forwarding config |
| [08-spl-queries.md](docs/08-spl-queries.md) | SPL queries for auth, Kerberos, processes, privilege monitoring |
| [09-dashboards.md](docs/09-dashboards.md) | Dashboard design, panel types, sample layouts |
| [screenshots.md](docs/screenshots.md) | Full screenshot index with descriptions |

## Screenshots

See [docs/screenshots.md](docs/screenshots.md) for the complete index. Screenshots follow the naming convention `NN-{category}-{action}-{detail}.png` and are stored in the `screenshots/` directory.

| Category | Count | Scope |
|----------|-------|-------|
| Configuration | 1 | Splunk receiving port setup |
| Search | 8 | Raw events, EventCode filters, WinEventLog, host filter, Kerberos events |
| Statistics | 1 | EventCode count aggregation |
| Visualization | 2 | Bar chart, logon timechart |

## SPL Queries

The [spl/](spl/) directory contains reusable query files organized by security domain:

| File | Focus |
|------|-------|
| `authentication.spl` | Logon success/failure, brute force detection, RDP tracking |
| `kerberos.spl` | TGT requests, service tickets, pre-auth failures |
| `processes.spl` | Process creation, suspicious process detection |
| `privileged-activity.spl` | Privileged service calls, admin logon monitoring |
| `volume-monitoring.spl` | Event volume, daily/hourly trends, event type breakdown |

## Skills

- **Windows Administration**: Active Directory, DNS, DHCP, User/Group Management
- **SIEM Engineering**: Splunk Enterprise, Universal Forwarder, Log Ingestion, Dashboarding
- **Security Monitoring**: Authentication, Process, Kerberos, Privileged Activity Analysis
- **Networking**: DNS, DHCP, Virtual Networking, Client-Server Communication

## Tools

Oracle VirtualBox, Windows Server 2022, Ubuntu Linux, Splunk Enterprise, Splunk Universal Forwarder, AD DS, DNS, DHCP, PowerShell
