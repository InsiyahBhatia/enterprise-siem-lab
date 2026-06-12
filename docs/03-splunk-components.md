# Splunk Core Components

Splunk has three primary components that work together to collect, store, and analyze data.

## 1. Forwarder

The Forwarder is responsible for collecting data from source machines and forwarding it to the Indexer. It performs three functions:

- **Receiving**: Collects logs from network devices, servers, and applications
- **Parsing**: Breaks raw logs into individual events with structured fields
- **Filtering**: Drops unnecessary events to optimize bandwidth and storage

A forwarder has a **persistent queue** (cache) that temporarily stores logs if the Indexer becomes unavailable. Once the Indexer recovers, the forwarder resumes sending.

Raw logs appear as a continuous stream of text. Parsing separates this stream into discrete events with identified timestamps and fields, making the data searchable and readable.

## 2. Indexer

The Indexer receives data from forwarders and manages its lifecycle:

1. **Receive**: Accept data from forwarders or directly from devices
2. **Parse** (if not already done by forwarder): Break into events
3. **License meter**: Track daily ingest volume
4. **Compress**: Reduce storage footprint
5. **Index**: Organize into searchable buckets on disk
6. **Store**: Retain for the configured retention period

Indexers are the licensed component of Splunk. They store data for long-term retention based on compliance, audit, or forensic requirements (months to years).

## 3. Search Head

The Search Head provides the user interface for querying indexed data. Users run searches, create reports, dashboards, and visualizations through the Search Head, which distributes queries across Indexers and aggregates results.

**Splunk Enterprise Security (ES)** is a premium application installed on the Search Head that enables:
- Real-time security monitoring
- Correlation across data sources
- Alerting on suspicious activity
- Incident investigation workflows

## Key Insight: One Installer, Multiple Roles

All three components (Heavy Forwarder, Indexer, Search Head) use the **same Splunk Enterprise installer**. The role is determined by configuration:

| Component | Receiving | Indexing | Searching |
|-----------|-----------|----------|-----------|
| Heavy Forwarder | Yes | No | No |
| Indexer | Yes | Yes | No |
| Search Head | No | No | Yes |

A **single-instance deployment** combines all three roles in one server. A **distributed deployment** separates them for scalability and fault tolerance.
