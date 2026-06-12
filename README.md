# Enterprise Active Directory Monitoring with Splunk SIEM

A virtualized enterprise lab environment simulating a real-world Windows Active Directory infrastructure integrated with Splunk SIEM for security monitoring and threat detection.

## Repository Structure

```
splunk-lab/
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
| [01-lab-architecture.md](docs/01-lab-architecture.md) | Lab infrastructure, network topology, components |
| [02-splunk-overview.md](docs/02-splunk-overview.md) | Splunk Cloud vs Enterprise, deployment models |
| [03-splunk-components.md](docs/03-splunk-components.md) | Forwarder, Indexer, Search Head roles |
| [04-forwarders.md](docs/04-forwarders.md) | Universal vs Heavy Forwarder comparison |
| [05-deployment-architecture.md](docs/05-deployment-architecture.md) | Single instance vs distributed architecture |
| [06-implementation-guide.md](docs/06-implementation-guide.md) | Step-by-step AD and Splunk setup |
| [07-event-log-collection.md](docs/07-event-log-collection.md) | Windows Event IDs, forwarding configuration |
| [08-spl-queries.md](docs/08-spl-queries.md) | Search Processing Language reference |
| [09-dashboards.md](docs/09-dashboards.md) | Dashboard design and development |
| [screenshots.md](docs/screenshots.md) | Lab screenshot index |

## Screenshots

See [docs/screenshots.md](docs/screenshots.md) for the full screenshot index. All screenshots are stored in the `screenshots/` directory with descriptive names following the pattern:

- `0X-splunk-{action}-{details}.png`
- **Configuration** screenshots for Splunk settings
- **Search** screenshots showing raw SPL queries and event results
- **Statistics** screenshots showing `stats` aggregations
- **Visualization** screenshots showing charts and timecharts

## Skills Covered

- **Windows Administration**: Active Directory, DNS, DHCP, User/Group Management
- **SIEM Engineering**: Splunk Enterprise, Universal Forwarder, Log Ingestion, Dashboards
- **Security Monitoring**: Authentication, Process, Kerberos, Privileged Activity Analysis
- **Networking**: DNS, DHCP, Virtual Networking, Client-Server Communication

## Tools

Oracle VirtualBox, Windows Server 2022, Ubuntu Linux, Splunk Enterprise, Splunk Universal Forwarder, AD DS, DNS, DHCP, PowerShell
