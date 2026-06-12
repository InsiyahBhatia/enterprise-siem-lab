# Windows Event Log Collection

## Collected Log Types

The Universal Forwarder monitors three Windows Event Log channels:

| Log | Description |
|-----|-------------|
| Security | Logon/logoff, privilege use, account changes |
| System | Service state, drivers, system events |
| Application | Application-level events |

## Key Security Event IDs

### Authentication

| Event ID | Description | Use |
|----------|-------------|-----|
| 4624 | Successful Logon | Track user access |
| 4625 | Failed Logon | Detect brute force |
| 4634 | Logoff | Session tracking |
| 4672 | Admin Logon | Privileged access |

### Kerberos

| Event ID | Description |
|----------|-------------|
| 4768 | Kerberos TGT Request |
| 4769 | Kerberos Service Ticket Request |
| 4771 | Kerberos Pre-Authentication Failed |

### Privileged Operations

| Event ID | Description |
|----------|-------------|
| 4673 | Privileged Service Called |
| 4674 | Privileged Operation Attempted |
| 4688 | Process Creation |

### System & Management

| Event ID | Description |
|----------|-------------|
| 7036 | Service State Change |
| 7045 | New Service Installed |
| 1102 | Audit Log Cleared |
| 4720 | User Account Created |

## Inputs Configuration

Located at: `C:\Program Files\SplunkUniversalForwarder\etc\system\local\inputs.conf`

```ini
[WinEventLog://Security]
index = windows
disabled = 0

[WinEventLog://System]
index = windows
disabled = 0

[WinEventLog://Application]
index = windows
disabled = 0
```

## Logon Types Reference

| Type | Value | Description |
|------|-------|-------------|
| Interactive | 2 | Local console login |
| Network | 3 | Network share access |
| Service | 5 | Service startup |
| Unlock | 7 | Workstation unlock |
| RDP | 10 | Remote Desktop |
