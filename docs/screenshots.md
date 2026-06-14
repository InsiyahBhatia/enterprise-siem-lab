# Screenshots

Screenshots are located in the `screenshots/` directory and document the lab setup, configuration, Splunk searches, SPL commands, threat hunting queries, and dashboard.

---

## Configuration

### Splunk Receiving Port Configuration (9997)

![](../screenshots/01-splunk-configuration-receiving-port-9997.png)

---

## Search & Events

### Search All Events

```
index=*
```

![](../screenshots/02-splunk-search-raw-all-events.png)

---

### Search Successful Logons (EventCode=4624)

```
EventCode=4624
```

![](../screenshots/03-splunk-search-event-4624-successful-logon.png)

---

### Search Failed Logons (EventCode=4625)

```
EventCode=4625
```

![](../screenshots/04-splunk-search-event-4625-failed-logon.png)

---

### Search Windows Security Event Log Source

```
sourcetype=WinEventLog:Security
```

![](../screenshots/05-splunk-search-source-win-event-log-security.png)

---

### Search Events from Host CENTRAL-SRV

```
host=CENTRAL-SRV
```

![](../screenshots/06-splunk-search-host-central-server.png)

---

### Search Kerberos TGT Requests (EventCode=4768)

```
EventCode=4768
```

![](../screenshots/07-splunk-search-event-4768-kerberos-ticket-request.png)

---

### Search Kerberos Service Tickets (EventCode=4769)

```
EventCode=4769
```

![](../screenshots/08-splunk-search-event-4769-kerberos-service-ticket.png)

---

### Search Kerberos Pre-Auth Failures (EventCode=4771)

```
EventCode=4771
```

![](../screenshots/09-splunk-search-event-4771-kerberos-pre-auth-failure.png)

---

## Statistics & Visualizations

### Event Code Count Statistics

```
index=* | stats count by EventCode
```

![](../screenshots/10-splunk-statistics-event-code-count.png)

---

### Bar Chart — Event Code Distribution

```
index=* | stats count by EventCode | sort - count
```

![](../screenshots/11-splunk-visualization-event-code-bar-chart.png)

---

### Timechart — Successful vs Failed Logons

```
EventCode=4624 OR EventCode=4625 | timechart count by EventCode
```

![](../screenshots/12-splunk-visualization-logon-timechart.png)

---

## SPL Commands

### 1. stats — Aggregate and Summarize Data

**Example:** `EventCode=4672 | stats count by host`

![](../screenshots/13-privilege-use-event-count-by-host.png)

**Example:** `EventCode=4672 OR EventCode=4673 OR EventCode=4674 | stats count by Account_Name`

![](../screenshots/16-privilege-use-stats-account-names.png)

**Example:** `EventCode=4 | stats count`

![](../screenshots/19-directory-service-events-stats.png)

**Example:** `EventCode=5156 | stats count by Action`

![](../screenshots/20-firewall-events-pie-chart.png)

---

### 2. table — Display Selected Fields

**Example:** `EventCode=4624 | table Account_Name`

![](../screenshots/24-account-enumeration-table-command.png)

**Example:** `EventCode=4673 OR EventCode=4674 | table _time Account_Name`

![](../screenshots/28-privilege-operations-event-list.png)

---

### 3. sort — Sort Results Ascending or Descending

**Example:** `EventCode=4624 | stats count by Account_Name | sort - count`

![](../screenshots/15-privilege-use-top-account-names.png)

**Example:** `EventCode=4624 | chart count by Account_Name | sort - count`

![](../screenshots/29-account-activity-chart-command.png)

**Example:** `EventCode=4624 | fields host | top limit=20 host`

![](../screenshots/31-host-summary-top-limit.png)

---

### 4. where — Filter Results After Aggregation

**Example:** `EventCode=4624 | stats count by Account_Name | where count>10`

![](../screenshots/26-account-enumeration-filtered-count.png)

---

### 5. eval — Create New Calculated Fields

**Example:** `EventCode=4624 | stats count by Account_Name | eval Risk=if(count>100,"HIGH","LOW")`

![](../screenshots/27-account-enumeration-risk-evaluation.png)

---

### 6. timechart — Time-Based Visualizations

**Example:** `EventCode=4672 | timechart count by EventCode`

![](../screenshots/14-privilege-use-timechart-by-date.png)

**Example:** `EventCode=7036 OR EventCode=7045 | timechart count by EventCode`

![](../screenshots/17-service-events-timechart-by-eventcode.png)

**Example:** `EventCode=7036 | chart count over host`

![](../screenshots/18-service-events-column-chart.png)

---

### 7. search — Filter Events by Keywords or Field Values

**Example:** `search Account_Name=Administrator`

![](../screenshots/32-administrator-logon-events.png)

**Example:** `EventCode=7045`

![](../screenshots/22-service-installation-raw-events.png)

---

### 8. fields — Display Only Specified Fields

**Example:** `EventCode=4688 | fields host New_Process_Name`

![](../screenshots/21-process-creation-table-view.png)

---

## Additional SPL Examples

### Deduplicate Events (dedup)

**Example:** `EventCode=4624 | dedup Account_Name`

![](../screenshots/25-account-enumeration-deduplicated.png)

---

### Extract Fields with Regex (rex)

**Example:** `EventCode=4688 | rex field=CommandLine "(?<Executable>\w+\.exe)"`

![](../screenshots/23-logon-events-extract-executable.png)

---

### Group Events into Sessions (transaction)

**Example:** `EventCode=4624 OR EventCode=4634 | transaction Account_Name`

![](../screenshots/30-logon-events-transaction-view.png)

---

## Threat Hunting

### Network Tool Detection

```
wget OR curl
```

Detect potential unauthorized network tool usage.

![](../screenshots/33-wget-curl-network-activity.png)

---

### Process Creation Monitoring

```
EventCode=4688
```

Track newly created processes.

![](../screenshots/34-process-creation-all-events.png)

---

## Dashboard

### Windows Event Monitoring & Threat Hunting Dashboard

The final dashboard includes 11 panels: Total Events, Successful Logins, Failed Logins, Privileged Logons, Top Event IDs, Authentication Activity, User Login Distribution, Event Distribution Analysis, Authentication Trend, Process Monitoring, and User Authentication Flow.

![](../screenshots/35-windows-event-monitoring-dashboard.png)
