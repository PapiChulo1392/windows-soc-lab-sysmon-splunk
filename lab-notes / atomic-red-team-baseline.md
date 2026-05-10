# Atomic Red Team Baseline Note

## Date

4/8/2026

## VM Name

SOC-WN11

## Purpose

Confirm the SOC lab was healthy before running Atomic Red Team tests.

## Baseline Checks Completed

- VM booted normally
- Able to log in successfully
- Sysmon logs visible in Event Viewer
- Splunk receiving Sysmon logs
- Harmless test event generated
- Harmless test event found in Splunk
- Snapshot created before testing

## Harmless Test Event Used

Opened Notepad.

## Splunk Search Used

```spl
index=main source="WinEventLog:Microsoft-Windows-Sysmon/Operational" notepad.exe
```

## Screenshots

![VMware snapshot before Atomic Red Team testing](../screenshots/vmware-snapshot.png)
