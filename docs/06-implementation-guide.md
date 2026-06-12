# Implementation Guide

## 1. Active Directory Deployment

1. Install Windows Server 2022 in VirtualBox
2. Add **Active Directory Domain Services** role via Server Manager
3. Promote server to Domain Controller for `corp.org`
4. Create Organizational Units for logical structuring
5. Create domain users and security groups

## 2. DNS Configuration

- DNS installs automatically with AD DS
- Configure forward lookup zone for `corp.org`
- Configure reverse lookup zone for `192.168.56.0/24`
- Verify name resolution with `nslookup`

## 3. DHCP Configuration

Configure DHCP scope on the Domain Controller:

| Setting | Value |
|---------|-------|
| Scope | 192.168.56.10 - 192.168.56.200 |
| Subnet | 255.255.255.0 |
| Gateway | 192.168.56.1 |
| DNS | 192.168.56.100 |
| Domain | corp.org |

## 4. Splunk Enterprise on Ubuntu

```bash
# Download and install
sudo dpkg -i splunk-9.x.x-linux-2.6-amd64.deb

# First-time start
sudo /opt/splunk/bin/splunk start --accept-license

# Enable at boot
sudo /opt/splunk/bin/splunk enable boot-start

# Access at http://192.168.56.10:8000
```

## 5. Enable Receiver Port

```bash
sudo /opt/splunk/bin/splunk enable listen 9997

# Verify
sudo netstat -tulpn | grep 9997
```

Or via Splunk Web: **Settings** → **Forwarding and Receiving** → **Configure receiving** → **New** (port 9997)

## 6. Universal Forwarder on Windows

1. Download and install Splunk Universal Forwarder
2. During setup, configure:
   - Receiver IP: `192.168.56.10`
   - Receiver Port: `9997`

```powershell
# Verify connectivity
Test-NetConnection -ComputerName 192.168.56.10 -Port 9997

# Add Windows Event Log inputs
& "C:\Program Files\SplunkUniversalForwarder\bin\splunk.exe" add monitor "Security" -index windows
& "C:\Program Files\SplunkUniversalForwarder\bin\splunk.exe" add monitor "System" -index windows
& "C:\Program Files\SplunkUniversalForwarder\bin\splunk.exe" add monitor "Application" -index windows

# Restart forwarder
& "C:\Program Files\SplunkUniversalForwarder\bin\splunk.exe" restart
```

## 7. Verification

In Splunk, run:

```spl
index=windows sourcetype=WinEventLog:Security
| stats count by EventCode
```

This confirms Windows Security events are being ingested.
