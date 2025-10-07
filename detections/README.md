# Detections

This folder contains **hunt queries and detection logic** used in the ACME Credential-Leak case study.

## Files
- `hunt_ioc_query.spl` – Splunk-style query for matching leaked accounts/IPs
- `hunt_behavioral_query.spl` – heuristic query for suspicious login & lateral movement
- `hunt_behavioral_sigma.yml` – Sigma rule equivalent
- `enrichment_notebook.ipynb` – optional Python enrichment demo

Each query is documented with:
- ATT&CK technique(s) addressed
- Usage notes
- Expected output (screenshots in `/visuals`)
