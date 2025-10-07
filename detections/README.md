# Detections

This folder contains hunt logic used in the ACME credential-leak case study.

## Files
- `hunt_ioc_query.spl` — Finds events linked to leaked users/IPs (IOC hunt).
- `hunt_behavioral_query.spl` — Flags brute-force → success → lateral movement.
- `hunt_behavioral_sigma.yml` — Sigma version of the behavioral hunt.

## Data Assumptions
We load `data/sample_logs.csv` into a Splunk index called `acme_logs` for demo. If you’re not using Splunk, treat the SPL as pseudocode and use the Sigma rule.

## MITRE ATT&CK
- T1078 (Valid Accounts)
- T1110 (Brute Force)
- T1021 (Remote Services – PsExec)
- T1059 (PowerShell)
