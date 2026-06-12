# Deployment Architecture

## Single Instance

A single Splunk Enterprise server performs all functions: receiving, parsing, indexing, and searching.

- **Pros**: Simple, low cost, minimal maintenance
- **Cons**: Single point of failure, limited scalability
- **Best for**: Lab environments, small teams, <5 GB/day

## Distributed Architecture

Separate servers are dedicated to each function: Forwarders collect, Indexers store, Search Heads query.

- **Pros**: Scalable, load-balanced, fault-tolerant components
- **Cons**: More complex, higher cost
- **Best for**: Enterprise environments, >5 GB/day

## Clustered Architecture

Multiple Indexers and Search Heads work together with replication and high availability. A Cluster Master manages Indexer state, a Deployer manages Search Head configuration, and a License Master tracks licensing.

- **Pros**: High availability, data replication, seamless scaling
- **Cons**: Highest complexity and cost
- **Best for**: Large enterprises, >50 GB/day, mission-critical environments

## Architecture Decision Factors

| Factor | Single Instance | Distributed | Clustered |
|--------|----------------|-------------|-----------|
| Daily ingest | <5 GB/day | 5-50 GB/day | >50 GB/day |
| Users | 1-5 | 5-20 | 20+ |
| High availability | None | Partial | Full |
| Complexity | Low | Medium | High |

This lab uses a **single-instance** Splunk Enterprise deployment for simplicity, with the Windows Domain Controller as a log source via Universal Forwarder.
