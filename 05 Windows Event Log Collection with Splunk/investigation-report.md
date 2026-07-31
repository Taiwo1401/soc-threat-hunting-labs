# Investigation Report — Lab 05

## Investigation Summary

This investigation focused on configuring Splunk Enterprise to collect Windows Event Logs from the local Windows machine and verifying that the logs could be searched using Splunk Search Processing Language (SPL).

---

## Investigation Objective

The objective of this investigation was to:

- Configure Splunk Enterprise for Windows Event Log collection.
- Verify successful log ingestion.
- Perform basic searches using SPL.
- Understand how Windows Event Logs support security monitoring and incident investigations.

---

## Environment

| Component | Description |
|-----------|-------------|
| Operating System | Windows 11 |
| SIEM Platform | Splunk Enterprise |
| Data Source | Windows Event Logs |
| Search Language | SPL |
| Endpoint Monitoring | Microsoft Sysmon |

---

## Evidence Collected

The following Windows Event Logs were configured for collection:

- Application
- Security
- System

Evidence included:

- Splunk configuration
- Indexed events
- Windows Security logs
- Windows System logs
- Windows Application logs

---

## SPL Queries Executed

### Display all indexed events

```spl
index=*
```

---

### Search the main index

```spl
index=main
```

---

### Display Security Events

```spl
source="WinEventLog:Security"
```

---

### Display System Events

```spl
source="WinEventLog:System"
```

---

### Display Application Events

```spl
source="WinEventLog:Application"
```

---

## Investigation Findings

The investigation confirmed that:

- Splunk Enterprise successfully accepted Windows Event Log configuration.
- Windows Event Logs could be searched using SPL.
- Security events contained authentication and security-related activity.
- System events recorded operating system activities.
- Application events contained software-generated logs.
- Event metadata included timestamps, host information, source, sourcetype, and event details useful during investigations.

---

## Challenges Encountered

During this investigation, several issues were encountered:

- The original Splunk installation generated an internal **"Oops"** error when opening the Local Event Log Collection page.
- The issue was resolved by uninstalling and reinstalling Splunk Enterprise.
- Microsoft-Windows-Sysmon/Operational was present in Windows Event Viewer but was not available in Splunk's Local Event Log configuration.

These issues highlighted the importance of validating SIEM deployments before beginning log analysis.

---

## Security Impact

Windows Event Logs provide valuable forensic evidence that enables analysts to:

- Detect failed login attempts.
- Monitor user authentication.
- Investigate system errors.
- Track application activity.
- Support incident response.
- Identify suspicious behavior across endpoints.

---

## Lessons Learned

Throughout this investigation I learned that:

- Proper log collection is the foundation of every SIEM deployment.
- Windows Event Logs provide multiple perspectives of system activity.
- SPL allows analysts to quickly search and filter large volumes of events.
- Troubleshooting SIEM configuration issues is an important skill for SOC analysts.
- Successful investigations depend on accurate and complete log ingestion.

---

## Conclusion

This investigation successfully configured Splunk Enterprise to collect Windows Event Logs and demonstrated how SPL can be used to search and analyze security-relevant events. The lab strengthened my understanding of SIEM administration, Windows logging, and the role of centralized log analysis in a Security Operations Center (SOC).
