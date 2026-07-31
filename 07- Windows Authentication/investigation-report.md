# Investigation Report — Lab 07

## Investigation Summary

This investigation focused on analyzing Windows authentication events collected by Splunk Enterprise. Using Splunk Search Processing Language (SPL), Security Event Logs were examined to identify successful logins, failed login attempts, privileged logons, and user account activity.

---

## Investigation Objective

The objectives of this investigation were to:

- Analyze Windows authentication events.
- Identify successful and failed login attempts.
- Investigate privileged logons.
- Summarize authentication activity using SPL.
- Understand how authentication logs support incident investigations.

---

## Lab Environment

| Component | Description |
|-----------|-------------|
| Operating System | Windows 11 |
| SIEM Platform | Splunk Enterprise |
| Data Source | Windows Security Event Logs |
| Search Language | Splunk Search Processing Language (SPL) |

---

## Evidence Collected

The investigation examined Windows Security Event Logs, including:

- Successful logon events
- Failed logon events
- Privileged logon events
- User authentication activity
- Statistical summaries of login events

---

## Windows Event IDs Investigated

| Event ID | Description |
|----------|-------------|
| 4624 | Successful Logon |
| 4625 | Failed Logon |
| 4634 | Logoff |
| 4672 | Special Privileges Assigned to New Logon |
| 4648 | Logon Using Explicit Credentials |
| 4720 | User Account Created |
| 4726 | User Account Deleted |
| 4732 | User Added to Security Group |

---

## SPL Queries Executed

### Successful Logons

```spl
source="WinEventLog:Security" EventCode=4624
```

---

### Failed Logons

```spl
source="WinEventLog:Security" EventCode=4625
```

---

### Privileged Logons

```spl
source="WinEventLog:Security" EventCode=4672
```

---

### Count Successful Logons

```spl
source="WinEventLog:Security" EventCode=4624 | stats count
```

---

### Top User Accounts

```spl
source="WinEventLog:Security" EventCode=4624 | top Account_Name
```

---

## Investigation Findings

The investigation determined that:

- Windows Security Event Logs successfully recorded authentication activity.
- Successful logons generated Event ID **4624**.
- Failed authentication attempts generated Event ID **4625** when present.
- Administrative or privileged logons generated Event ID **4672**.
- SPL statistical commands provided a quick summary of authentication activity.
- User account information, timestamps, and host details were available for each event.

---

## Event Analysis

Authentication events contained valuable information including:

- Username
- Hostname
- Event ID
- Logon type
- Timestamp
- Source
- Sourcetype

Reviewing these fields enables analysts to determine who logged into a system, when the activity occurred, and whether the authentication appeared legitimate.

---

## Challenges Encountered

During the investigation:

- Learning the purpose of different Windows Event IDs required research.
- Understanding SPL filtering techniques improved with practice.
- Some Event IDs may not appear if the associated activity has not occurred on the endpoint.
- Interpreting authentication events required careful examination of event fields.

---

## Security Impact

Authentication monitoring is essential because it helps analysts:

- Detect brute-force attacks.
- Identify unauthorized access attempts.
- Monitor administrator logins.
- Track user account activity.
- Investigate compromised accounts.
- Support incident response investigations.

Authentication events are among the most valuable data sources within a Security Operations Center.

---

## Recommendations

Based on this investigation, the following recommendations are made:

- Continuously monitor authentication events for abnormal login activity.
- Review failed login attempts regularly to detect password attacks.
- Monitor privileged account usage for unauthorized administrative access.
- Configure alerts for excessive failed logons or unusual authentication patterns.
- Retain Security Event Logs to support future forensic investigations.

---

## Lessons Learned

This investigation reinforced several important concepts:

- Windows Security Event Logs are critical for authentication monitoring.
- Event IDs provide a fast method for locating specific security events.
- SPL enables efficient searching and filtering of authentication logs.
- Statistical commands help summarize large datasets.
- Authentication investigations form a core responsibility of SOC analysts.

---

## Conclusion

This investigation successfully analyzed Windows authentication events using Splunk Enterprise and SPL. Authentication logs were examined to identify successful logins, failed authentication attempts, privileged logons, and user account activity. The investigation demonstrated how Windows Security Event Logs support security monitoring, threat detection, and incident response within a Security Operations Center (SOC).
