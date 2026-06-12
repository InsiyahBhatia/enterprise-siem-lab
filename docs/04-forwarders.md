# Forwarder Types

## Universal Forwarder

A lightweight agent installed directly on endpoints (Windows Server, Linux, etc.) to collect local logs.

| Feature | Description |
|---------|-------------|
| Footprint | Small (low CPU/RAM) |
| Parsing | None |
| License | Free |
| Installation | On OS (Windows, Linux, Solaris, AIX, macOS) |
| Use case | Collect local logs from servers and workstations |

**Cannot** be installed on network devices (routers, firewalls). These devices send logs via syslog to a Heavy Forwarder or directly to an Indexer.

## Heavy Forwarder

A full Splunk Enterprise instance deployed on a dedicated server that acts as a centralized collection and processing layer.

| Feature | Description |
|---------|-------------|
| Footprint | Full Splunk installation |
| Parsing | Full event parsing |
| Filtering | Can drop unnecessary events |
| License | Requires Splunk Enterprise license |
| Use case | Central collection, syslog aggregation, parsing layer |

**Key responsibilities**:
- Receive logs from Universal Forwarders
- Pull logs from network devices via syslog
- Parse and filter events before forwarding to Indexer
- Reduce load on Indexers by preprocessing data

## Why Both?

Universal Forwarders run directly on endpoints to access local Windows Event Logs and files. Heavy Forwarders aggregate and preprocess data from multiple sources, reducing the parsing burden on Indexers. In smaller deployments, Universal Forwarders can forward directly to the Indexer. In larger environments, a Heavy Forwarder layer is recommended.
