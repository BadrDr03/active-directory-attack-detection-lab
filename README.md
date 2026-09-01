# Active Directory Attack Detection & Incident Investigation Lab

## Overview

This project simulates realistic Active Directory attack chains in an enterprise-style Windows domain environment.

The objective is to investigate identity-based attacks from a SOC analyst perspective by correlating authentication events, Active Directory changes, endpoint telemetry, and SIEM data.

Each scenario follows the workflow:

Attack → Telemetry → Detection → Investigation → Timeline → MITRE ATT&CK → Evidence → Verdict → Incident Response

## Project Objectives

- Build a realistic Active Directory enterprise environment.
- Simulate interconnected Active Directory attack chains.
- Collect and analyze Windows and Active Directory security telemetry.
- Develop detection logic for identity-based attacks.
- Perform SOC-style incident investigations.
- Build incident timelines and identify evidence and IOCs.
- Map attacker behavior to MITRE ATT&CK.
- Document containment and remediation actions.

## Planned Attack Chains

1. Compromised Domain User → AD Enumeration → Kerberoasting
2. Password Spraying → Account Compromise → Lateral Authentication
3. Privilege Escalation → Privileged Group Modification → Persistence
4. DCSync / Domain Credential Theft (Advanced)

## Documentation Methodology

Every implementation phase is documented immediately after completion.

Each case study includes:

- Objective
- Attack context
- Telemetry
- Detection logic
- Investigation
- 5W1H analysis
- Timeline
- MITRE ATT&CK mapping
- Evidence / IOCs
- Verdict
- Incident response and remediation
