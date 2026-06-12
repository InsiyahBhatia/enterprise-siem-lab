# Screenshots

Screenshots are located in the `screenshots/` directory and document the lab setup, configuration, and Splunk operations.

## Configuration

| Screenshot | Description |
|------------|-------------|
| [01-splunk-configuration-receiving-port-9997.png](../screenshots/01-splunk-configuration-receiving-port-9997.png) | Splunk receiving port configuration (9997) |

## Search & Events

| Screenshot | Description |
|------------|-------------|
| [02-splunk-search-raw-all-events.png](../screenshots/02-splunk-search-raw-all-events.png) | Search all events with `index=*` |
| [03-splunk-search-event-4624-successful-logon.png](../screenshots/03-splunk-search-event-4624-successful-logon.png) | Search successful logons (EventCode=4624) |
| [04-splunk-search-event-4625-failed-logon.png](../screenshots/04-splunk-search-event-4625-failed-logon.png) | Search failed logons (EventCode=4625) |
| [05-splunk-search-source-win-event-log-security.png](../screenshots/05-splunk-search-source-win-event-log-security.png) | Search Windows Security event log source |
| [06-splunk-search-host-central-server.png](../screenshots/06-splunk-search-host-central-server.png) | Search events from host CENTRAL-SRV |
| [07-splunk-search-event-4768-kerberos-ticket-request.png](../screenshots/07-splunk-search-event-4768-kerberos-ticket-request.png) | Search Kerberos TGT requests (EventCode=4768) |
| [08-splunk-search-event-4769-kerberos-service-ticket.png](../screenshots/08-splunk-search-event-4769-kerberos-service-ticket.png) | Search Kerberos service tickets (EventCode=4769) |
| [09-splunk-search-event-4771-kerberos-pre-auth-failure.png](../screenshots/09-splunk-search-event-4771-kerberos-pre-auth-failure.png) | Search Kerberos pre-auth failures (EventCode=4771) |

## Statistics

| Screenshot | Description |
|------------|-------------|
| [10-splunk-statistics-event-code-count.png](../screenshots/10-splunk-statistics-event-code-count.png) | Statistics table of EventCode counts |

## Visualizations

| Screenshot | Description |
|------------|-------------|
| [11-splunk-visualization-event-code-bar-chart.png](../screenshots/11-splunk-visualization-event-code-bar-chart.png) | Bar chart visualization of EventCode distribution |
| [12-splunk-visualization-logon-timechart.png](../screenshots/12-splunk-visualization-logon-timechart.png) | Timechart comparing successful vs failed logons |
