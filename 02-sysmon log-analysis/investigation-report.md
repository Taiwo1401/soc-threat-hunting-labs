# Investigation Report — Lab 02: Sysmon Log Analysis

## Investigation Summary

This investigation focused on analyzing Sysmon Process Creation events (Event ID 1) generated on a Windows 11 endpoint. The objective was to understand how Sysmon records process execution, examine parent-child process relationships, and identify whether the observed activity represented normal or suspicious behavior.

---

## Objective

To analyze Sysmon Process Creation events and understand the information available to SOC analysts during endpoint investigations.

---

## Scenario

A user reported unusual activity on their workstation. As a Junior SOC Analyst, I reviewed the Sysmon Operational logs to identify recently executed processes and determine whether the activity required further investigation.

---

## Scope of Investigation

The investigation focused on:

- Process Creation (Event ID 1)
- Parent Process relationships
- Command-line execution
- User account activity
- Process execution timestamps

---

## Investigation Steps

1. Opened Event Viewer.
2. Navigated to the Sysmon Operational log.
3. Filtered the log to display only Event ID 1 (Process Creation) events.
4. Generated endpoint activity by opening:
   - Notepad
   - Calculator
   - Paint
   - Command Prompt
5. Reviewed the newly generated events.
6. Compared multiple Process Creation events.
7. Examined parent-child process relationships.

---

## Evidence Collected

| Evidence | Status |
|----------|--------|
| Sysmon Operational Log | ✅ |
| Event ID 1 Filter Applied | ✅ |
| Generated Process Events | ✅ |
| Event Details Reviewed | ✅ |
| Event Log Exported | ✅ |

---

## Analysis

The Sysmon Operational log successfully recorded each application launched during testing.

Each Process Creation event contained useful forensic information, including:

- Process Name (Image)
- Parent Process (Parent Image)
- Command Line
- User Account
- Process ID
- Process GUID
- UTC Timestamp

The Parent Image field helped identify which application launched the process, providing additional context for the investigation.

---

## Findings

- Event ID 1 entries were successfully generated for each application launched during testing.
- The observed processes matched the expected user activity.
- Parent-child process relationships were successfully identified.
- Command-line information was available for each process.
- No evidence of suspicious or unauthorized process execution was observed.

---

## Analyst Assessment

Based on the available evidence, the recorded activity represents normal Windows user behavior.

The applications executed during the investigation were intentionally launched, and the associated Sysmon events accurately reflected those actions. No indicators of malicious execution or abnormal process behavior were identified.

---

## Challenges Encountered

- Filtering Event ID 1 events from a large number of Sysmon entries.
- Understanding the significance of parent-child process relationships.
- Interpreting the different metadata fields recorded within each event.

---

## Lessons Learned

- Process Creation events provide valuable endpoint telemetry.
- Parent Process information helps reconstruct execution chains.
- Command-line arguments can provide important context during investigations.
- Sysmon significantly improves endpoint visibility compared to default Windows logging.

---

## Conclusion

The investigation successfully demonstrated how Sysmon records Process Creation events and how these logs can be analyzed during a security investigation. The collected telemetry provided sufficient information to understand normal endpoint activity and confirmed that Sysmon is an effective tool for endpoint monitoring and forensic analysis.

---

## Recommendations

- Continue monitoring Process Creation events for unusual activity.
- Deploy a customized Sysmon configuration to capture additional event types.
- Correlate Sysmon logs with a SIEM platform such as Splunk for centralized analysis.
- Regularly review process execution patterns to establish a baseline for normal endpoint behavior.
