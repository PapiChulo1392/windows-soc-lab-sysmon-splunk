# PowerShell Process Investigation

## Date

3/30/2026 1:52:42.285 AM

## Scenario

I opened PowerShell and searched for the corresponding Sysmon event in Splunk.

## Summary

A Sysmon Event ID 1 process creation event for `powershell.exe` was identified in Splunk on host `SOC-WN11`.

## Evidence

- Event ID: 1
- Image: `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`
- CommandLine: `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`
- User: `SOC-WN11\PapiChulo`
- ParentImage: `C:\Windows\explorer.exe`
- Host: `SOC-WN11`

## Timeline

I opened PowerShell. A Sysmon Event ID 1 record was identified in Splunk. The event was reviewed and documented.

## IOCs

None identified in the fields reviewed.

## Severity

Informational

## Escalation Decision

Activity was reviewed in Splunk and validated as user activity. No escalation needed.

## Next Steps

Update the project tracker with the completed Command Prompt, Notepad, and PowerShell investigations.

## Screenshot

![PowerShell process investigation](../screenshots/powershell-investigation.png)
