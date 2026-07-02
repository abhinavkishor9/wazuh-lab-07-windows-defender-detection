# Troubleshooting Notes

## Problem 1

No Windows Defender events appeared.

### Cause

No recent Defender activity.

### Resolution

Generate a Defender event or wait for scheduled Defender operations.

---

## Problem 2

Threat Hunting returned no results.

### Cause

Incorrect query.

### Resolution

Search using:

- eventID
- eventSourceName
- Windows Defender

Increase time range if necessary.

---

## Problem 3

PowerShell returned no events.

### Cause

Wrong log name.

### Resolution

Use:

```powershell
Get-WinEvent -LogName "Microsoft-Windows-Windows Defender/Operational"
```

---

## Problem 4

No alerts inside Wazuh.

### Cause

Agent disconnected.

### Resolution

Verify:

```powershell
Get-Service WazuhSvc
```

Restart if necessary.

---

## Problem 5

Sysmon not running.

### Resolution

```powershell
Get-Service Sysmon64
```

Start service if stopped.

---

## Problem 6

Timestamp mismatch.

### Cause

UTC conversion between endpoint and Wazuh.

### Resolution

Compare event timestamps allowing for timezone differences.

---

## Problem 7

No Threat Hunting data.

### Cause

Incorrect time window.

### Resolution

Expand search to:

- Last 24 Hours
- Last 7 Days

---

## Lessons Learned

- Defender logs are collected through Windows Event Logs.
- Wazuh indexes Defender telemetry successfully.
- Time synchronization is important during investigations.
- Event correlation should always be validated using endpoint logs.
