# Windows Event ID 4624 Authentication Investigation

## Objective

Analyze Windows Security Event Logs to identify and interpret authentication events as a SOC Tier 1 analyst.

The objective is to determine whether authentication activity is expected or potentially suspicious based on user, logon type, process, and context.

---

## Environment

- Operating System: Windows
- Log Source: Windows Event Viewer
- Log: Security
- Event ID Analyzed: 4624 - Successful Logon

---

# Event 1 - Cached Interactive Logon

## Event Details

| Field | Value |
|---|---|
| Event ID | 4624 |
| Logon Type | 11 - Cached Interactive |
| User | CAMI\camip |
| Account Domain | MicrosoftAccount |
| Date/Time | 24-07-2026 18:40:34 |
| Workstation Name | CAMI |
| Process Name | C:\Windows\System32\svchost.exe |
| Process ID | 0x5cc |

---

## Analysis

The event shows a successful authentication performed by the user account CAMI\camip.

The Logon Type 11 indicates a Cached Interactive Logon, meaning Windows authenticated the user using locally cached credentials.

The associated process is svchost.exe located in the Windows System32 directory, which is a legitimate Windows system process.

No suspicious indicators were identified during this analysis.

---

# Event 2 - Service Logon

## Event Details

| Field | Value |
|---|---|
| Event ID | 4624 |
| Logon Type | 5 - Service |
| User | SYSTEM |
| Account Domain | NT AUTHORITY |
| Date/Time | 31-07-2026 13:23:47 |
| Workstation Name | - |
| Computer | Cami |
| Process Name | C:\Windows\System32\services.exe |

---

## Analysis

The event shows a service authentication performed by the built-in Windows SYSTEM account.

The Logon Type 5 indicates that a Windows service started or requested authentication.

The associated process, services.exe, is the Windows Service Control Manager responsible for managing system services.

This behavior is expected in a normal Windows environment.

---

# Findings

Two successful authentication events were analyzed:

- A user authentication using Cached Interactive Logon.
- A system service authentication using the SYSTEM account.

Both events were consistent with normal Windows activity.

---

# Risk Assessment

Severity: Informational

Verdict: Benign

No indicators of compromise were identified from the analyzed events.

---

# Conclusion

The investigation demonstrated the ability to analyze Windows Security Event ID 4624, identify different authentication types, and determine whether events represent normal or suspicious activity.

The analyzed events were classified as legitimate Windows behavior.