# Lab 01 – Sysmon Fundamentals

## Scenario

You have joined a Security Operations Center (SOC) as a Junior SOC Analyst. Your organization wants better visibility into Windows endpoints because the default Windows logs are insufficient for detecting modern attacks.

Your first assignment is to deploy Microsoft Sysmon, verify that it is collecting endpoint telemetry, and understand the types of events it records.

---

# Objective

Install Sysmon, verify its operation, and analyze the endpoint telemetry it generates.

---

# Estimated Time

45–60 minutes

---

# Difficulty

🟢 Beginner

---

# Prerequisites

- Windows 11
- Administrator privileges
- Internet connection

---

# Environment

- Windows 11
- PowerShell
- Event Viewer
- Sysmon

---

# Background Theory

## What is Sysmon?

Sysmon (System Monitor) is a Windows system service and device driver developed by Microsoft Sysinternals. It records detailed information about system activity, such as process creation, network connections, file creation, registry modifications, and DNS queries. These logs help security professionals monitor endpoints and investigate suspicious behavior.

## Why SOC Analysts use Sysmon

SOC analysts use Sysmon because it provides much more detailed endpoint telemetry than the default Windows Event Logs. This additional visibility helps analysts:

Detect suspicious processes.
Monitor network connections.
Investigate malware activity.
Track file creation and modification.
Observe registry changes.
Support threat hunting and incident response.

## Windows Event Logs vs Sysmon

| Windows Event Logs                      | Sysmon                                          |
| --------------------------------------- | ----------------------------------------------- |
| Built into Windows                      | Installed separately                            |
| Records general operating system events | Records detailed security-related events        |
| Limited security visibility             | Enhanced endpoint visibility                    |
| Basic auditing                          | Advanced monitoring for security investigations |




# Lab Preparation

Before beginning this lab:

- Download Sysmon from Microsoft Sysinternals.
- Extract the ZIP file.
- Open PowerShell as Administrator.

---

# Hands-on Tasks

## Task 1 — Download Sysmon

Download the latest Sysmon release from Microsoft's Sysinternals website.

Expected Result:

- Sysmon ZIP downloaded.

---

## Task 2 — Extract Files

Extract the downloaded ZIP.

You should see files similar to:

- Sysmon.exe
- Sysmon64.exe
- EULA

Expected Result:

- Files extracted successfully.

---

## Task 3 — Install Sysmon

Run:

```powershell
.\Sysmon64.exe -i
```

Expected Result:

Sysmon installs successfully.

Evidence:

📸 Screenshot

---

## Task 4 — Verify Installation

Run:

```powershell
Get-Service Sysmon64
```

Expected Result:

Status = Running

Evidence:

📸 Screenshot

---

## Task 5 — Open Event Viewer

Navigate to:

Applications and Services Logs

↓

Microsoft

↓

Windows

↓

Sysmon

↓

Operational

Expected Result:

Sysmon Operational log opens.

Evidence:

📸 Screenshot

---

## Task 6 — Examine Events

Open several events.

Record:

- Event ID
- Process Name
- Command Line
- User
- Timestamp

Expected Result:

Understand the information available in each event.

Evidence:

📸 Screenshot

---

## Task 7 — Generate Activity

Open:

- Notepad
- Calculator
- Command Prompt

Refresh Event Viewer.

Locate the generated events.

Evidence:

📸 Screenshot

---

# Questions

Answer these after completing the lab.

1. What is Sysmon?

2. Which Event IDs did you observe?

3. Which process names appeared?

4. Which user executed them?

5. Why is Sysmon valuable to a SOC Analyst?

---

# Screenshots Required

- sysmon-install.png
- sysmon-service.png
- event-viewer.png
- event-details.png
- process-events.png

---

# Expected Outcome

By the end of this lab you should be able to:

- Install Sysmon.
- Verify its operation.
- Navigate Sysmon logs.
- Understand endpoint telemetry.
- Identify common Sysmon events.

---

# Skills Demonstrated

- Endpoint Monitoring
- Windows Security
- Sysmon
- Event Viewer
- Process Analysis
- Security Documentation
