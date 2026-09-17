# Windows Authentication Investigation with Splunk

## Overview

This project demonstrates a Windows authentication investigation using
Splunk Enterprise and Windows Security Event Logs.

The investigation focuses on identifying failed authentication attempts,
analyzing authentication details, and correlating failed logons with
subsequent successful logons.

This project was completed in a controlled home lab environment to
practice foundational Security Operations Center (SOC) investigation
techniques.

---

## Investigation Objective

The objective of this investigation was to:

- Identify failed Windows authentication attempts.
- Determine which account was involved.
- Analyze the source and workstation associated with the events.
- Examine Windows authentication event details.
- Correlate failed authentication attempts with successful logons.
- Create an authentication timeline.
- Document investigation findings and recommended SOC response actions.

---

## Lab Environment

| Component | Technology |
|---|---|
| Operating System | Windows 11 |
| SIEM | Splunk Enterprise 10.4.2 |
| Log Collection | Splunk Universal Forwarder 10.4.2 |
| SIEM Server | Ubuntu 24.04 LTS |
| Virtualization | Oracle VirtualBox |
| Log Source | Windows Security Event Logs |
| Query Language | Splunk Search Processing Language (SPL) |

---

## Investigation Methodology

The investigation followed a basic SOC workflow:

1. Collect Windows Security Event Logs.
2. Search Splunk for failed authentication events.
3. Identify affected accounts.
4. Examine authentication event details.
5. Analyze source network information.
6. Search for successful authentication events.
7. Correlate failed and successful authentication activity.
8. Build an authentication timeline.
9. Document findings and recommended response actions.

---

## Windows Event IDs Investigated

### Event ID 4625 — Failed Logon

Event ID 4625 was used to identify failed Windows authentication attempts.

### Event ID 4624 — Successful Logon

Event ID 4624 was used to identify successful Windows authentication events
following the failed attempts.

---

## Key Investigation Findings

Five Event ID 4625 records were identified during the investigation period.

The activity involved the `SOCAdmin` account and the `SOC-WINDOWS`
workstation.

Where a source network address was recorded, the source was:

```text
127.0.0.1
