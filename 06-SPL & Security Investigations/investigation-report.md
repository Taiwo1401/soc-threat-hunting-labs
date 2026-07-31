# Investigation Report — Lab 06

## Investigation Summary

This investigation focused on learning the fundamentals of Splunk Search Processing Language (SPL) by searching, filtering, and analyzing Windows Event Logs collected by Splunk Enterprise. The objective was to understand how security analysts use SPL to investigate system activity and identify relevant security events.

---

## Investigation Objective

The objectives of this investigation were to:

- Learn the basics of Splunk Search Processing Language (SPL).
- Search and filter indexed Windows Event Logs.
- Understand event metadata such as host, source, sourcetype, and timestamp.
- Examine individual events to identify useful forensic information.
- Build a foundation for future threat hunting and security investigations.

---

## Lab Environment

| Component | Description |
|----------|-------------|
| Operating System | Windows 11 |
| SIEM Platform | Splunk Enterprise |
| Data Source | Windows Event Logs |
| Search Language | SPL |

---

## Evidence Collected

The following Windows Event Logs were analyzed during the investigation:

- Application
- Security
- System

Evidence consisted of indexed Windows events collected by Splunk.

---

## SPL Queries Executed

### View all indexed events

```spl
index=*
```

---

### View events stored in the main index

```spl
index=main
```

---

### Search Windows Security Events

```spl
source="WinEventLog:Security"
```

---

### Search Windows System Events

```spl
source="WinEventLog:System"
```

---

### Search Windows Application Events

```spl
source="WinEventLog:Application"
```

---

### Display events containing a host field

```spl
index=* host=*
```

---

### Display available sourcetypes

```spl
index=* sourcetype=*
```

---

## Investigation Findings

The investigation revealed that:

- Splunk successfully indexed Windows Event Logs.
- SPL queries quickly filtered large volumes of events.
- Security logs contained authentication and security-related activities.
- System logs recorded operating system events.
- Application logs contained software-generated events.
- Every event included useful metadata such as:
  - Timestamp
  - Host
  - Source
  - Sourcetype
  - Raw event data

This metadata is essential for forensic analysis and incident investigations.

---

## Event Analysis

One event was expanded and examined in detail.

The following information was identified:

- Host name
- Event source
- Sourcetype
- Event timestamp
- Raw event contents

Reviewing individual events provides valuable context that helps analysts understand exactly what occurred on the endpoint.

---

## Challenges Encountered

During the investigation:

- Learning the structure of SPL queries required practice.
- Understanding the difference between **source**, **host**, and **sourcetype** was initially challenging.
- Filtering events correctly became easier after experimenting with different search queries.

---

## Security Impact

Searching and filtering logs efficiently enables SOC analysts to:

- Investigate suspicious activity.
- Review authentication events.
- Detect abnormal system behavior.
- Identify application errors.
- Perform rapid incident investigations.
- Reduce the time required to locate relevant evidence.

---

## Lessons Learned

This investigation reinforced several important concepts:

- SPL is the primary language used for searching data in Splunk.
- Windows Event Logs contain valuable security information.
- Filtering search results improves investigation efficiency.
- Event metadata provides important context during incident response.
- Understanding log structure is fundamental for every SOC analyst.

---

## Conclusion

This investigation successfully demonstrated the fundamentals of Splunk Search Processing Language (SPL). Basic searches, filters, and event analysis were performed against Windows Event Logs, providing practical experience with log analysis and strengthening foundational SOC analyst skills.
