# Chrome Process Investigation

## Date

3/30/2026 5:51:06.840 PM

## Scenario

I opened Google Chrome and searched for the corresponding Sysmon event in Splunk.

## Summary

A Sysmon Event ID 1 process creation event for `chrome.exe` was identified in Splunk on host `SOC-WN11`.

## Evidence

- Event ID: 1
- Image: `C:\Program Files\Google\Chrome\Application\chrome.exe`
- CommandLine: `C:\Program Files\Google\Chrome\Application\chrome.exe`
- User: `SOC-WN11\PapiChulo`
- ParentImage: `C:\Windows\explorer.exe`
- Host: `SOC-WN11`

## Timeline

I opened Google Chrome. A Sysmon Event ID 1 record was identified in Splunk. The event was reviewed and documented.

## IOCs

None identified in the fields reviewed.

## Severity

Informational

## Escalation Decision

Activity was reviewed in Splunk and validated as user activity. No escalation needed.

## Next Steps

Practice true positive versus false positive analysis using the completed investigation notes.

## Screenshot

![Chrome process investigation](../screenshots/chrome-investigation.png)
