# Investigation Report — Lab 08

## Investigation Summary

This investigation focused on performing a basic threat hunting exercise using Splunk Enterprise. Windows Event Logs were proactively analyzed to identify suspicious activities, review available log sources, and determine whether any indicators of compromise (IOCs) or abnormal system behavior were present.

---

## Investigation Objective

The objectives of this investigation were to:

- Perform proactive threat hunting using Splunk Search Processing Language (SPL).
- Identify available Windows Event Logs for analysis.
- Investigate Security, System, and Application logs.
- Examine event metadata and log sources.
- Determine whether suspicious activity or anomalies existed within the collected logs.

---

## Lab Environment

| Component | Description |
|-----------|-------------|
| Operating System | Windows 11 |
| SIEM Platform | Splunk Enterprise |
| Data Source | Windows Event Logs |
| Search Language | Splunk Search Processing Language (SPL) |

---

## Evidence Collected

The investigation analyzed events from the following Windows Event Logs:

- Security
- System
- Application

Additional evidence included:

- Indexed events
- Log sources
- Sourcetypes
- Event metadata
- Individual event details

---

## SPL Queries Executed

### View All Indexed Events

```spl
index=*
```

---

### Display Top Sources

```spl
index=* | top source
```

---

### Display Top Sourcetypes

```spl
index=* | top sourcetype
```

---

### Review Security Events

```spl
source="WinEventLog:Security"
```

---

### Review System Events

```spl
source="WinEventLog:System"
```

---

### Review Application Events

```spl
source="WinEventLog:Application"
```

---

## Investigation Findings

The investigation determined that:

- Splunk successfully collected Windows Event Logs.
- Multiple log sources were available for analysis.
- Security events contained authentication-related activities.
- System events recorded operating system activity.
- Application events contained software-generated logs.
- Event metadata included timestamps, hosts, sources, sourcetypes, and detailed event messages.

No clear indicators of malicious activity were identified during the investigation.

---

## Event Analysis

A detailed review of an individual event revealed:

- Event timestamp
- Hostname
- Source log
- Sourcetype
- Event ID (where available)
- Raw event message

Analyzing individual events provided valuable context for understanding normal system behavior and identifying any unusual activity.

---

## Threat Hunting Hypothesis

The investigation was based on the following hypothesis:

> If malicious or abnormal activity has occurred on the endpoint, evidence should be present within Windows Security, System, or Application Event Logs and can be identified through targeted SPL searches.

After reviewing the available logs, no evidence was found to support this hypothesis.

---

## Challenges Encountered

During the investigation:

- Some advanced threat hunting queries returned no results because detailed endpoint telemetry, such as Sysmon process creation events, was not yet being ingested into Splunk.
- The investigation relied primarily on standard Windows Event Logs.
- Understanding the available data sources before beginning the hunt proved essential.

---

## Security Impact

Threat hunting enables Security Operations Center (SOC) analysts to proactively identify potential threats before they escalate into security incidents.

The techniques used in this investigation support the detection of:

- Unauthorized login attempts
- Abnormal system behavior
- Application errors
- Suspicious user activity
- Potential indicators of compromise (IOCs)

---

## Recommendations

Based on this investigation, the following recommendations are made:

- Continue monitoring Windows Event Logs on a regular basis.
- Configure Sysmon log ingestion into Splunk to improve endpoint visibility.
- Develop additional SPL searches for common attack techniques.
- Configure alerts for unusual authentication patterns and critical Windows events.
- Regularly review newly indexed logs for abnormal activity.

---

## Lessons Learned

This investigation reinforced several important concepts:

- Threat hunting begins with understanding the available data.
- SPL enables efficient searching and filtering of large log datasets.
- Event metadata provides valuable context for investigations.
- Standard Windows Event Logs provide a solid foundation for introductory threat hunting.
- Not every investigation will identify malicious activity, but documenting normal findings is an important part of security operations.

---

## Conclusion

This investigation successfully demonstrated the fundamentals of threat hunting using Splunk Enterprise. Windows Event Logs were analyzed using SPL to identify available log sources, investigate security-relevant events, and evaluate potential indicators of compromise. Although no suspicious activity was identified, the investigation strengthened practical skills in proactive security monitoring, log analysis, and threat hunting within a Security Operations Center (SOC).
