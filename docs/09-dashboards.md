# Dashboard Development

## Final Dashboard

![Windows Event Monitoring & Threat Hunting Dashboard](../screenshots/35-windows-event-monitoring-dashboard.png)

---

## Dashboard Panels

### Panel 1 – Total Events

**Query**
```spl
index=*
| stats count
```

**Visualization:** Single Value

**Purpose:** Shows total events collected.

---

### Panel 2 – Successful Login Attempts

**Query**
```spl
EventCode=4624
| stats count
```

**Visualization:** Single Value

**Purpose:** Displays total successful logins.

---

### Panel 3 – Failed Login Attempts

**Query**
```spl
EventCode=4625
| stats count
```

**Visualization:** Single Value

**Purpose:** Displays failed logins.

---

### Panel 4 – Privileged Logons

**Query**
```spl
EventCode=4672
| stats count
```

**Visualization:** Single Value

**Purpose:** Tracks administrative privilege assignments.

---

### Panel 5 – Top Event IDs

**Query**
```spl
index=*
| stats count by EventCode
| sort - count
| head 10
```

**Visualization:** Horizontal Bar Chart

**Purpose:** Shows most common Windows Event IDs.

---

### Panel 6 – Authentication Activity

**Query**
```spl
EventCode=4624 OR EventCode=4625
| timechart count by EventCode
```

**Visualization:** Line Chart

**Purpose:** Compare successful vs failed logins over time.

---

### Panel 7 – User Login Distribution

**Query**
```spl
EventCode=4624
| stats count by Account_Name
```

**Visualization:** Pie Chart

**Purpose:** Shows most active users.

---

### Panel 8 – Event Distribution Analysis

**Query**
```spl
index=*
| stats count by EventCode
```

**Visualization:** Bubble Chart

**Purpose:** Visualize event frequency distribution.

---

### Panel 9 – Authentication Trend

**Query**
```spl
EventCode=4768 OR EventCode=4769
| timechart count by EventCode
```

**Visualization:** Area Chart

**Purpose:** Monitor Kerberos authentication activity.

---

### Panel 10 – Process Monitoring

**Query**
```spl
EventCode=4688
| stats count by New_Process_Name
| sort - count
| head 10
```

**Visualization:** Horizontal Bar Chart

**Purpose:** Shows most executed processes.

---

### Panel 11 – User Authentication Flow

**Query**
```spl
EventCode=4624 OR EventCode=4625 OR EventCode=4672
| eval Event=case(
EventCode=4624,"Successful Login",
EventCode=4625,"Failed Login",
EventCode=4672,"Admin Privilege Assigned"
)
| stats count as Events by Account_Name Event
```

**Visualization:** Sankey Diagram

**Purpose:** Shows how users flow into successful logins, failed logins, and privileged logons. 

---

## Skills Demonstrated

* Splunk Enterprise Administration
* Splunk Universal Forwarder Configuration
* Windows Event Log Analysis
* Sysmon Monitoring
* SPL Query Development
* Dashboard Creation
* Threat Hunting
* Authentication Monitoring
* Security Event Investigation
* SOC Analyst Workflows
