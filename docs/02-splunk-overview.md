# Splunk Deployment Models

## Splunk Cloud vs Splunk Enterprise

Splunk offers two deployment models:

### Splunk Cloud (SaaS)

All components are hosted and managed by Splunk. The customer configures data inputs and uses the platform without managing infrastructure.

| Aspect | Detail |
|--------|--------|
| Management | Fully managed by Splunk |
| Deployment | Pre-deployed; configure only |
| Time to value | Fast |
| Customization | Limited |
| Best for | Organizations wanting to avoid operational overhead |

### Splunk Enterprise (On-Premises)

The customer deploys and manages all Splunk components on their own infrastructure.

| Aspect | Detail |
|--------|--------|
| Management | Self-managed |
| Deployment | Requires infrastructure planning |
| Time to value | Slower |
| Customization | Full control |
| Best for | Enterprises with compliance, data residency, or custom requirements |

## License Model

Splunk Enterprise licensing is based on **daily ingest volume** measured in GB/day. The license meter tracks how much data is indexed per day. The Universal Forwarder does not require a license when used solely for forwarding (no local indexing).
