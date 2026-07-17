# Investigation Report — Lab 03: Advanced Sysmon Configuration

## Investigation Summary

This investigation evaluated the deployment of a custom Sysmon configuration using the SwiftOnSecurity Sysmon configuration file. The objective was to determine how a customized configuration improves endpoint visibility compared to the default Sysmon installation.

---

## Objective

To deploy a custom Sysmon configuration, verify that it was successfully applied, and assess how it enhances endpoint telemetry for security monitoring.

---

## Scenario

The organization requires improved endpoint visibility to support threat detection and incident response. The default Sysmon configuration provides limited logging, so a community-maintained configuration was deployed to capture additional security-relevant events.

---

## Scope of Investigation

The investigation focused on:

- Sysmon configuration deployment
- XML configuration analysis
- Endpoint telemetry
- Event Viewer verification
- Additional event categories enabled by the new configuration

---

## Investigation Steps

1. Downloaded the SwiftOnSecurity Sysmon configuration.
2. Reviewed the XML configuration file.
3. Identified key monitoring sections:
   - ProcessCreate
   - NetworkConnect
   - FileCreate
   - RegistryEvent
   - DnsQuery
4. Updated the existing Sysmon installation with the custom configuration.
5. Generated endpoint activity by:
   - Opening Notepad
   - Opening Command Prompt
   - Browsing a website
   - Creating a text file
6. Reviewed the Sysmon Operational log to observe the generated events.

---

## Evidence Collected

| Evidence | Status |
|----------|--------|
| Configuration Downloaded | ✅ |
| XML Configuration Reviewed | ✅ |
| Sysmon Configuration Updated | ✅ |
| New Endpoint Activity Generated | ✅ |
| Sysmon Operational Log Reviewed | ✅ |

---

## Analysis

The SwiftOnSecurity configuration expands the number of activities monitored by Sysmon compared to the default configuration.

During testing, Sysmon continued to record endpoint activity after the configuration update. The XML configuration includes rules for monitoring process execution, network connections, DNS queries, registry modifications, and file creation, providing analysts with richer telemetry for investigations.

The configuration was successfully applied without errors, confirming that Sysmon accepted the updated XML configuration.

---

## Findings

- The custom Sysmon configuration was successfully applied.
- The XML configuration included monitoring rules for multiple categories of endpoint activity.
- Sysmon continued logging events after the update.
- The custom configuration provides broader visibility than the default configuration.
- Enhanced logging supports more effective threat hunting and incident response.

---

## Analyst Assessment

The deployment was successful and improved the quality of endpoint telemetry available for analysis.

A customized Sysmon configuration is more suitable for production environments because it captures a wider range of security-relevant events while helping analysts investigate suspicious activity more effectively.

---

## Challenges Encountered

- Understanding the structure of the XML configuration file.
- Identifying the purpose of each monitored event category.
- Comparing the capabilities of the default and customized configurations.

---

## Lessons Learned

- Sysmon behavior is controlled by its XML configuration.
- Custom configurations significantly improve endpoint visibility.
- Community-maintained configurations provide a strong starting point for enterprise deployments.
- Proper endpoint logging is essential for threat hunting, detection engineering, and incident response.

---

## Conclusion

The objective of this investigation was achieved. The custom Sysmon configuration was successfully deployed, verified, and tested. The updated configuration provides enhanced endpoint telemetry, making Sysmon a more effective tool for detecting, investigating, and responding to security incidents.

---

## Recommendations

- Continue using a maintained Sysmon configuration rather than the default settings.
- Periodically review and update the configuration to align with emerging threats.
- Forward Sysmon logs to a SIEM such as Splunk or Microsoft Sentinel for centralized monitoring and correlation.
- Develop detection rules based on the additional telemetry collected by the custom configuration.
