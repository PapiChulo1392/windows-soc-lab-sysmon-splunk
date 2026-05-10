# Command Prompt Process Investigation

## Date

3/30/2026 12:33:56.999 AM

## Scenario

I opened Command Prompt and searched for the corresponding Sysmon event in Splunk.

## Summary

A Sysmon Event ID 1 process creation event for `cmd.exe` was identified in Splunk on host `SOC-WN11`.

## Evidence

- Event ID: 1
- Image: `C:\Windows\System32\cmd.exe`
- CommandLine: `C:\WINDOWS\system32\cmd.exe`
- User: `SOC-WN11\PapiChulo`
- ParentImage: `C:\WINDOWS\explorer.EXE`
- Host: `SOC-WN11`

## Timeline

I opened Command Prompt. A Sysmon Event ID 1 record was identified in Splunk. The event was reviewed and documented.

## IOCs

None identified in the fields reviewed.

## Severity

Informational

## Escalation Decision

Activity was reviewed in Splunk and validated as user activity. No escalation needed.

## Next Steps

Review and document a PowerShell process creation event.

## Screenshot

![Command Prompt process investigation](../screenshots/command-prompt-investigation.png)
