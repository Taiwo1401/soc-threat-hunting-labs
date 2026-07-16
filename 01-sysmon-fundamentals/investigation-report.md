# Investigation Report – Lab 01

## Investigation Summary

Microsoft Sysmon was successfully installed on a Windows 11 endpoint to improve endpoint visibility. After installation, endpoint activity was generated and the resulting Sysmon events were reviewed using Event Viewer.

---

## Objective

Verify that Sysmon is functioning correctly and determine what information it records about endpoint activity.

---

## Investigation Steps

1. Installed Sysmon using PowerShell.
2. Verified the Sysmon service was running.
3. Opened the Sysmon Operational log in Event Viewer.
4. Generated endpoint activity by launching:
   - Notepad
   - whatsapp
5. Reviewed the generated events.

---

## Evidence Collected

| Evidence | Status |
|----------|--------|
| Sysmon Installed | ✅ |
| Sysmon Service Running | ✅ |
| Event Viewer Accessible | ✅ |
| Process Creation Events Generated | ✅ |

---

## Events Observed

| Event ID | Description | Observed |
|----------|-------------|----------|
| 1 | Process Creation | ✅ |
| 3 | Network Connection | ✅ |
| 5 | Process Terminated | ✅|
| 7 | Image Loaded | ✅|
| 11 | File Created | ✅ |
| 13 | Registry Value Set | ✅|
| 22 | DNS Query | ☐ |


---

## Processes Observed

| Process | Observed |
|----------|----------|
| notepad.exe | ✅ |
| application.exe | ✅ |


---

## Key Findings

- Sysmon successfully captured process creation events.
- Each event contained valuable information including the process name, parent process, user account, command line, and timestamp.
- The generated activity matched the actions performed during the lab.
- No suspicious or unexpected activity was observed.

---

## Analyst Assessment

The observed events represent normal user activity. The endpoint behaved as expected, and Sysmon successfully recorded the generated processes.

This confirms that Sysmon is functioning correctly and is capable of providing detailed endpoint telemetry for future investigations.

---

## Challenges Encountered

- Understanding the structure of Sysmon events required reviewing several log entries.
- Some Event IDs were not generated because the default Sysmon configuration does not log every type of activity.

---

## Lessons Learned

- Sysmon provides significantly more detailed logging than standard Windows Event Logs.
- Process Creation (Event ID 1) is one of the most valuable events for SOC investigations.
- Event Viewer is useful for validating that Sysmon is collecting endpoint telemetry.
- Endpoint visibility is essential for effective threat hunting and incident response.

---

## Conclusion

The objective of this investigation was achieved. Sysmon was installed successfully, endpoint activity was generated, and Process Creation events were analyzed. The collected telemetry demonstrates how Sysmon enhances Windows logging and supports SOC analysts during security investigations.
