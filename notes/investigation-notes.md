# Investigation Notes

## Investigation Summary

Objective:

Validate that Windows Defender Operational events are successfully collected by Wazuh and available for SOC investigations.

---

## Initial Checks

Verified:

- Windows Defender enabled
- Wazuh Agent running
- Sysmon service running
- Endpoint connected to Wazuh Manager

---

## Event Generation

Windows Defender Operational log produced new events.

Observed Event Information:

- Event Source:
  Microsoft-Windows-Windows Defender

- Channel:
  Application

- Event ID:
  16384

- Rules Engine Loaded

---

## Endpoint Validation

PowerShell confirmed new Defender events.

Example command:

```powershell
Get-WinEvent -LogName "Microsoft-Windows-Windows Defender/Operational"
```

---

## Wazuh Investigation

Threat Hunting query located Defender event.

Observed fields included:

- agent.name
- eventID
- eventSourceName
- timestamp
- computer
- data

---

## Timeline

1. Defender generated event
2. Windows Event Log updated
3. Wazuh Agent collected event
4. Manager indexed alert
5. Threat Hunting displayed event
6. Analyst verified metadata

---

## Findings

No malicious activity observed.

Lab confirmed successful ingestion of Defender telemetry into Wazuh.

---

## Analyst Conclusion

Detection pipeline functioning correctly.

Windows Defender telemetry is available for future threat hunting and incident investigations.
