# Windows Authentication Investigation

## Investigation Overview

This investigation analyzed Windows Security authentication events collected
from a Windows 11 workstation and forwarded to Splunk Enterprise.

## Objective

Identify and analyze repeated failed authentication attempts and determine
whether the activity represented suspicious or malicious behavior.

## Tools Used

- Windows 11
- Splunk Enterprise 10.4.2
- Splunk Universal Forwarder 10.4.2
- Windows Security Event Logs
- Splunk Search Processing Language (SPL)

## Investigation Findings

Five Event ID 4625 records were identified during the investigation period.
These events represented failed authentication attempts involving the
SOCAdmin account.

The failed authentication events were associated with the SOC-WINDOWS
workstation. Where a source address was recorded, the source was
127.0.0.1, which represents the local Windows system.

The failed authentication events included Sub-Status 0xC000006A,
which is associated with an incorrect password.

A subsequent Event ID 4624 successful authentication was identified
following the failed authentication attempts.

## Timeline

| Time | Event | Source | Workstation |
|---|---|---|---|
| 17:02:13 | Failed Login | Local/unspecified | SOC-WINDOWS |
| 17:40:28 | Failed Login | 127.0.0.1 | SOC-WINDOWS |
| 17:40:30 | Failed Login | 127.0.0.1 | SOC-WINDOWS |
| 17:40:32 | Failed Login | 127.0.0.1 | SOC-WINDOWS |
| 17:40:35 | Failed Login | 127.0.0.1 | SOC-WINDOWS |
| 17:40:48 | Successful Login | 127.0.0.1 | SOC-WINDOWS |

## Conclusion

The authentication events were generated as part of a controlled
security lab exercise. The activity demonstrated how repeated failed
authentication attempts can be identified and correlated with a
subsequent successful authentication using Splunk.

Because the source address was 127.0.0.1 and the activity was intentionally
generated during testing, the evidence does not establish an external
brute-force attack.

## Recommended SOC Response

If similar activity were observed in a production environment, a SOC
analyst should:

1. Validate whether the successful authentication was authorized.
2. Investigate the source address and affected account.
3. Review surrounding Windows Security events for additional activity.
4. Determine whether the account requires additional protection.
5. Continue monitoring for repeated authentication failures.
