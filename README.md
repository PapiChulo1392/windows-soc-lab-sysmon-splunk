# Windows SOC Lab: Sysmon and Splunk Enterprise

## Project Overview

This project documents a beginner Security Operations Center home lab built with a Windows 11 virtual machine, Microsoft Sysmon, and Splunk Enterprise. The goal of the lab was to generate endpoint telemetry, ingest Windows security events into a SIEM, and practice basic SOC analyst investigation workflows.

The lab was used to review Sysmon process creation events, validate log ingestion in Splunk, and write simple case notes for common user activity such as Command Prompt, Notepad, PowerShell, and Google Chrome execution.

## Tools Used

| Tool | Purpose |
|---|---|
| Windows 11 Virtual Machine | Lab endpoint used to generate activity |
| VMware Workstation | Virtual machine platform |
| Microsoft Sysmon | Endpoint telemetry and process monitoring |
| Windows Event Viewer | Local event log review |
| Splunk Enterprise | SIEM log ingestion, searching, and event analysis |
| Atomic Red Team Preparation | Baseline preparation before running security tests |

## Skills Demonstrated

- Built a Windows 11 SOC home lab in VMware
- Installed and configured Microsoft Sysmon
- Reviewed Sysmon logs in Windows Event Viewer
- Ingested Sysmon logs into Splunk Enterprise
- Used basic SPL searches to review endpoint activity
- Validated SIEM log ingestion by source
- Investigated Sysmon Event ID 1 process creation events
- Documented findings using beginner SOC case notes
- Practiced evidence based investigation writing
- Created a clean VM snapshot before security testing
- Prepared the lab for future Atomic Red Team testing

## Lab Summary

I built a beginner SOC home lab using a Windows 11 virtual machine, Sysmon, and Splunk Enterprise to generate, ingest, and review security logs. I verified successful SIEM log ingestion from the lab host and used the environment to practice log analysis, event review, and basic investigation workflows.

## Sysmon Verification

Sysmon was installed and verified through Windows Event Viewer. The lab successfully generated endpoint telemetry including process creation, registry activity, and DNS related events.

## Splunk Log Review and Basic SPL

Splunk Enterprise was used to search, filter, and summarize SIEM data from the Windows 11 lab host. I used basic SPL to validate ingestion, review Sysmon events, and investigate process creation activity.

### Validate log ingestion by source

```spl
index=main
| stats count by source
```

This search was used to confirm that Splunk was receiving logs from different Windows sources, including Sysmon.

### Search Sysmon logs only

```spl
index=main source="WinEventLog:Microsoft-Windows-Sysmon/Operational"
```

This search narrowed the results to Sysmon telemetry so I could focus on endpoint activity from the lab machine.

### Review Sysmon process creation events

```spl
index=main source="WinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=1
| table _time, host, Image, CommandLine, User, ParentImage
```

This search was used to review process creation events and identify what executable ran, how it ran, who ran it, what launched it, and where it happened.

### Search for Command Prompt activity

```spl
index=main source="WinEventLog:Microsoft-Windows-Sysmon/Operational" cmd.exe
| table _time, host, Image, CommandLine, User, ParentImage
```

This search was used to find and document the Command Prompt process creation event in Splunk.

### Search for PowerShell activity

```spl
index=main source="WinEventLog:Microsoft-Windows-Sysmon/Operational" powershell.exe
| table _time, host, Image, CommandLine, User, ParentImage
```

This search was used to find and document the PowerShell process creation event in Splunk.

## Process Investigation Case Notes

The following process creation events were reviewed using Sysmon Event ID 1 and Splunk.

| Investigation | Description |
|---|---|
| Command Prompt | Reviewed cmd.exe process creation from Windows Explorer |
| Notepad | Reviewed Notepad.exe process creation from Windows Explorer |
| PowerShell | Reviewed powershell.exe process creation from Windows Explorer |
| Google Chrome | Reviewed chrome.exe process creation from Windows Explorer |

## Example Finding

A Sysmon Event ID 1 process creation event for `cmd.exe` was identified in Splunk on host `SOC-WN11`. The event showed the executable path, command line, user, parent process, and host. The activity was reviewed and documented as normal user activity in the lab environment.

## Atomic Red Team Baseline Preparation

Before running Atomic Red Team tests, I confirmed that the lab was healthy and ready for testing.

Baseline checks completed:

- VM booted normally
- Able to log in successfully
- Sysmon logs visible in Event Viewer
- Splunk receiving Sysmon logs
- Harmless test event generated
- Harmless test event found in Splunk
- Snapshot created before testing

Snapshot name:

```text
Clean-Before-Atomic-Red-Team
```
## PowerShell Preparation

I checked the current PowerShell execution policy using:

```powershell
Get-ExecutionPolicy -List
```

The `CurrentUser` scope was changed to `Bypass` so Atomic Red Team PowerShell scripts could run inside the lab VM. The change was confirmed by rerunning the execution policy check.

## What I Learned

Through this project, I learned how endpoint activity appears in Sysmon, how to search those events in Splunk, and how to document basic investigation findings in a SOC style format. I also practiced writing fact based summaries without assuming malicious activity unless the evidence supports it.

## Project Summary

This project demonstrates my ability to build a basic SOC lab, collect endpoint telemetry, search logs in Splunk, and document findings using a structured investigation format. The lab will continue to be expanded with additional detection testing, Atomic Red Team activity, and more advanced SOC analyst workflows.
