# Dashboard Development

## Dashboard Overview

The lab includes dashboards for monitoring core security domains:

1. **Authentication Activity** - Login success/failure trends
2. **Failed Login Monitoring** - Brute force detection
3. **Kerberos Activity** - TGT and service ticket analysis
4. **Process Creation** - New process tracking and anomaly detection
5. **Event Volume** - Ingest health monitoring
6. **User Activity** - Login patterns and session tracking

## Panel Types

| Panel | Use |
|-------|-----|
| Statistics Table | Detailed event listing |
| Time Chart | Trends over time |
| Bar/Column Chart | Comparisons |
| Single Value | Key metric (total count, unique users) |
| Pie Chart | Distribution breakdown |

## Sample Dashboard Layout

### Authentication Dashboard

**Panel 1 - Time Chart**: Login success vs failure over time
```
index=windows sourcetype=WinEventLog:Security (EventCode=4624 OR EventCode=4625)
| eval status = if(EventCode=4624, "Success", "Failure")
| timechart count by status
```

**Panel 2 - Bar Chart**: Top users by login count
```
index=windows sourcetype=WinEventLog:Security EventCode=4624
| stats count by Account_Name
| sort - count
| head 10
```

**Panel 3 - Pie Chart**: Logon type distribution
```
index=windows sourcetype=WinEventLog:Security EventCode=4624
| stats count by Logon_Type
| eval Logon_Type_Label = case(
    Logon_Type=2, "Interactive (Console)",
    Logon_Type=3, "Network",
    Logon_Type=5, "Service",
    Logon_Type=10, "Remote Desktop",
    1=1, "Other")
```

### Failed Login Dashboard

```
# Brute force detection
index=windows sourcetype=WinEventLog:Security EventCode=4625
| bucket _time span=5m
| stats count by _time, Account_Name, Source_Network_Address
| where count > 5

# Top failed accounts
index=windows sourcetype=WinEventLog:Security EventCode=4625
| stats count by Account_Name
| sort - count
| head 10

# Source IP analysis
index=windows sourcetype=WinEventLog:Security EventCode=4625
| stats count by Source_Network_Address
| sort - count
| head 10
```

## Creating Dashboards in Splunk Web

1. **Dashboards** → **Create New Dashboard**
2. Choose **Dashboard Studio** (visual editor) or **Classic** (XML)
3. Add panels using the search queries above
4. Configure time range picker for user flexibility
5. Add inputs (dropdowns, text boxes) for interactive filtering
6. Save and set permissions

## Best Practices

- Use consistent color schemes (red for failures, green for success)
- Set appropriate time ranges for each panel
- Add descriptions to explain what each panel represents
- Use drilldowns to enable investigation from dashboard panels
- Schedule dashboard PDF delivery for recurring reports
