# ENV-005 — Logging and Auditing Configuration

## Objective

Configure centralized Windows security telemetry for the Active Directory lab in order to support threat detection, SOC investigation, and incident analysis.

## Advanced Audit Policy

A dedicated Group Policy Object named:

`AD-Lab-Advanced-Auditing`

was created and linked to the Domain Controllers OU.

The following audit categories were enabled:

### Account Logon
- Kerberos Authentication Service — Success and Failure
- Kerberos Service Ticket Operations — Success and Failure
- Credential Validation — Success and Failure

### Account Management
- User Account Management — Success and Failure
- Security Group Management — Success and Failure

### Logon / Logoff
- Logon — Success and Failure
- Account Lockout — Failure

### Directory Service Access
- Directory Service Changes — Success
- Directory Service Access — Success and Failure

### Policy Change
- Audit Policy Change — Success and Failure

These settings provide visibility into authentication activity, Kerberos operations, account changes, privileged group modifications, and Active Directory object activity.

## Sysmon Deployment

Microsoft Sysmon was deployed on:

- DC01-AD-LAB
- CLIENT01
- CLIENT02

The SwiftOnSecurity Sysmon configuration was used to provide enhanced endpoint telemetry including process creation and other security-relevant system activity.

Sysmon events are generated under:

`Microsoft-Windows-Sysmon/Operational`

## Splunk Universal Forwarder

Splunk Universal Forwarder is installed on all monitored Windows systems.

Events are forwarded to:

`10.0.20.40:9997`

and stored in the dedicated Splunk index:

`ad_lab`

The following Windows Event Log channels are collected:

- Security
- System
- Directory Service (Domain Controller)
- Microsoft-Windows-Sysmon/Operational

## Sysmon Input Configuration

Example Splunk Universal Forwarder configuration:

```ini
[WinEventLog://Microsoft-Windows-Sysmon/Operational]
disabled = 0
index = ad_lab
renderXml = true
