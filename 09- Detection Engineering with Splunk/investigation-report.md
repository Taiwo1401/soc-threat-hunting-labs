# Investigation Report — Lab 09

## Investigation Summary

This investigation focused on developing and validating detection rules for Windows authentication events using Splunk Enterprise. SPL queries were used to identify successful logins, failed login attempts, privileged logons, and authentication patterns. To verify the effectiveness of the detection logic, controlled failed login attempts were intentionally generated on the Windows endpoint.

---

## Investigation Objective

The objectives of this investigation were to:

- Develop authentication detection rules using Splunk Search Processing Language (SPL).
- Detect successful and failed login attempts.
- Validate detection logic using controlled testing.
- Analyze authentication activity recorded in Windows Security Event Logs.
- Understand how detection engineering supports continuous security monitoring.

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

The investigation analyzed the following authentication events:

- Successful logons (Event ID 4624)
- Failed logons (Event ID 4625)
- Privileged logons (Event ID 4672)
- Authentication statistics by user
- Windows Security Event metadata

---

## SPL Queries Executed

### Detect Failed Logons

```spl
source="WinEventLog:Security" EventCode=4625
```

---

### Count Failed Logons by User

```spl
source="WinEventLog:Security" EventCode=4625
| stats count by Account_Name
```

---

### Detect Successful Logons

```spl
source="WinEventLog:Security" EventCode=4624
```

---

### Count Successful Logons by User

```spl
source="WinEventLog:Security" EventCode=4624
| stats count by Account_Name
```

---

### Detect Privileged Logons

```spl
source="WinEventLog:Security" EventCode=4672
```

---

### Display Top Event Codes

```spl
index=* | top EventCode
```

---

### Detection Rule Validation

```spl
source="WinEventLog:Security" EventCode=4625
| stats count by Account_Name
| where count >= 5
```

---

## Investigation Findings

The investigation confirmed that:

- Windows Security Event Logs successfully recorded authentication activity.
- Successful login events were identified using Event ID 4624.
- Failed login events were identified using Event ID 4625.
- Privileged logons were identified using Event ID 4672.
- SPL statistical commands effectively summarized authentication events by user.
- The custom detection rule successfully identified repeated failed login attempts.

---

## Detection Validation

To verify the effectiveness of the detection rule, a controlled test was performed.

The Windows login screen was intentionally used to enter an incorrect password multiple times. This generated failed authentication events (Event ID 4625), which were successfully collected by Splunk Enterprise.

The detection query:

```spl
source="WinEventLog:Security" EventCode=4625
| stats count by Account_Name
| where count >= 5
```

successfully identified the repeated failed login attempts.

This confirmed that the detection logic functioned as expected and could be used to identify potential brute-force or password guessing attacks.

---

## Security Analysis

Repeated failed login attempts are commonly associated with:

- Password guessing attacks
- Brute-force attacks
- Credential stuffing attempts
- Users entering incorrect passwords

Although the failed logins in this investigation were intentionally generated for testing purposes, the same detection could be used in a production environment to identify genuine authentication attacks.

---

## Challenges Encountered

During the investigation:

- Some authentication-related events were only generated after performing controlled testing.
- Understanding Windows Event IDs and their security significance required additional research.
- Detection accuracy depends on proper log collection and Windows auditing configuration.

---

## Security Impact

Authentication detection rules help SOC analysts:

- Detect brute-force attacks.
- Identify compromised accounts.
- Monitor privileged account usage.
- Investigate suspicious authentication behavior.
- Improve incident detection and response.

---

## Recommendations

Based on this investigation, the following recommendations are made:

- Enable continuous monitoring of failed authentication events.
- Configure alerts for excessive failed login attempts.
- Review privileged account activity regularly.
- Periodically test detection rules to ensure they continue to function correctly.
- Retain Security Event Logs to support forensic investigations.

---

## Lessons Learned

This investigation reinforced several important concepts:

- Detection engineering is an essential part of SOC operations.
- SPL can be used to create effective authentication detections.
- Controlled testing is a valuable way to validate detection logic.
- Windows Security Event Logs provide reliable evidence for authentication investigations.
- Detection rules should be tested regularly to ensure they remain effective.

---

## Conclusion

This investigation successfully demonstrated the creation and validation of authentication detection rules using Splunk Enterprise. Controlled failed login attempts were intentionally generated to verify that the detection logic correctly identified repeated authentication failures. The investigation strengthened practical skills in detection engineering, authentication monitoring, and SIEM-based security analysis.
