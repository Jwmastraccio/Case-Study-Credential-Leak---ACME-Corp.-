# Hunt Case Study: ACME Corp. Credential Leak

## Executive Summary
In this simulation we hunted for malicious use of leaked credentials
against ACME Corp.’s environment. We identified suspicious logon
activity followed by lateral movement.

## Hunt Objectives
- Detect use of known leaked accounts / IOCs
- Detect abnormal authentication patterns (brute-force then success)
- Detect lateral movement using remote execution tools

## Data Sources
- Synthetic logs (`/data/sample_logs.csv`)
- IOCs from initial intel (`/data/IOCs.csv`)

## Methodology
1. IOC-based hunt query to locate initial access
2. Behavioral hunt to identify failed login bursts followed by success
3. Pivot to process lineage and network activity
4. Enrichment with public intel

## Findings
- Compromised user **jsmith** authenticated from external IP 203.0.113.55
- Shortly after, used **psexec** to move laterally to file server
- Executed suspicious **powershell** from internal host to external IP 198.51.100.88

## MITRE ATT&CK Mapping
- T1078 – Valid Accounts
- T1021 – Remote Services
- T1059 – Command and Scripting Interpreter (PowerShell)

## Recommendations
- Enforce MFA on external logins
- Monitor for anomalous process launches from new hosts
- Add detection for use of PsExec by standard users

## Evidence
Screenshots in `/visuals`
