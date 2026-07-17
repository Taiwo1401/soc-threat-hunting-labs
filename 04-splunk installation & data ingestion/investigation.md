# Investigation Report — Lab 04: Splunk Installation & Initial Data Verification

## Investigation Summary

This investigation evaluated the operational status of Splunk Enterprise and verified whether endpoint telemetry from Sysmon was available for analysis. The goal was to determine if the SIEM had been configured to ingest Windows security events.

---

## Objective

To verify Splunk functionality, identify indexed data sources, and determine whether Sysmon logs were available for investigation.

---

## Scenario

Following the deployment of Splunk Enterprise, the SOC team requested verification that Windows endpoint logs were successfully reaching the SIEM before beginning security monitoring activities.

---

## Scope of Investigation

The investigation focused on:

- Splunk Enterprise availability
- Search functionality
- Indexed data
- Internal Splunk logs
- Sysmon event availability

---

## Investigation Steps

1. Logged into Splunk Enterprise.
2. Opened the Search & Reporting application.
3. Executed a search across all indexes.
4. Queried the internal Splunk index.
5. Searched for Sysmon-related events.
6. Compared the returned results.

---

## Evidence Collected

| Evidence | Status |
|----------|--------|
| Splunk Login Successful | ✅ |
| Search & Reporting Accessible | ✅ |
| Internal Logs Available | ✅ |
| Sysmon Events Available | ❌ |
| Windows Event Logs Available | ❌ |

---

## Analysis

The investigation confirmed that Splunk Enterprise was functioning correctly.

Searches against the internal index (`index=_internal`) successfully returned events, demonstrating that Splunk was indexing its own operational data.

However, searches for Windows and Sysmon events returned no results. This indicates that endpoint logs had not yet been configured for ingestion into Splunk.

---

## Findings

- Splunk Enterprise was operational.
- Search functionality worked as expected.
- Internal logs were successfully indexed.
- Windows Event Logs were not present.
- Sysmon Operational logs were not available.
- Endpoint telemetry had not yet been integrated into the SIEM.

---

## Analyst Assessment

The SIEM platform is functioning correctly, but it is currently monitoring only its own internal activity.

To support security monitoring and threat detection, Windows Event Logs and Sysmon Operational logs must be configured as data sources for ingestion.

---

## Challenges Encountered

- Expected Sysmon events to appear automatically after installation.
- Determined that additional configuration is necessary before endpoint logs can be analyzed in Splunk.

---

## Lessons Learned

- Installing Splunk does not automatically collect endpoint logs.
- Installing Sysmon does not automatically forward events to a SIEM.
- Successful security monitoring depends on proper data ingestion and source configuration.
- Verifying available data is an essential first step in any SOC investigation.

---

## Conclusion

The investigation confirmed that Splunk Enterprise was successfully deployed and operational. Internal logs were available for analysis, but Windows and Sysmon logs were not yet being ingested. Configuring endpoint log collection will be the next step before performing threat hunting and security investigations.

---

## Recommendations

- Configure Windows Event Log ingestion.
- Add the Sysmon Operational log as a Splunk data source.
- Verify ingestion using EventCode searches.
- Continue with log analysis after endpoint telemetry becomes available.
