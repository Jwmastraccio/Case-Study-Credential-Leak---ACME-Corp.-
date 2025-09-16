# Case-Study-Credential-Leak---ACME-Corp.-

# Recon Case Study – ACME Corp. Credential Leak

This project is part of my **Threat Intelligence Portfolio**, designed to demonstrate OSINT-driven reconnaissance and credential leak analysis. The focus is on identifying, analyzing, and reporting exposed credentials tied to ACME Corp. found on the dark web and breach repositories.

---

## Project Overview
The case study simulates a real-world scenario where cyber threat intelligence analysts discover corporate credentials on underground markets. The goal is to assess risk, map to MITRE ATT&CK techniques, and provide defensive recommendations.

---

## Deliverables
- **[Report.md](./Report.md)** – Full intelligence report, including:
  - Executive Summary  
  - Threat Actor Background  
  - Campaign Analysis  
  - MITRE ATT&CK Mapping  
  - Defensive Recommendations  

- **[IOCs.csv](./IOCs.csv)** – Redacted sample of leaked credentials and associated indicators for safe sharing.  

- **[Sources.pdf](./Sources.pdf)** – References and intelligence sources used for analysis.  

---

## Key Findings
- Approximately **3,500 employee email/password pairs** were identified across multiple historical breaches.  
- Credentials were discovered in **breach dumps and stealer malware logs**.  
- Threats include:  
  - **Account Takeover (ATO)**  
  - **Credential Stuffing Attacks**  
  - **Business Email Compromise (BEC)**  
  - **Ransomware Entry Points**  

---

## MITRE ATT&CK Mapping
| Technique ID | Name | Observed Use |
|--------------|------|--------------|
| T1078 | Valid Accounts | Use of leaked credentials for unauthorized access |
| T1110 | Brute Force / Credential Stuffing | Testing leaked credentials on ACME services |
| T1556 | Modify Authentication Process | Potential abuse of privileged accounts |
| T1589 | Gather Victim Identity Information | Leveraging ACME emails for targeting |

---

## Skills Demonstrated
- Open-source intelligence (OSINT) collection & analysis  
- Mapping adversary techniques to **MITRE ATT&CK**  
- Creating structured **intelligence reports** for stakeholders  
- Producing IOC datasets suitable for SIEM/EDR ingestion  
- Communicating findings in both technical and business language  

---

## How to Use
1. Review **Report.md** for detailed threat analysis.  
2. Open **IOCs.csv** to see structured, redacted IOC examples.  
3. Check **Sources.pdf** for supporting evidence and references.  

---

## Disclaimer
All data has been **redacted or simulated** for educational and portfolio purposes.  
This project does **not** contain live credentials or sensitive corporate data.  
