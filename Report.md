# Recon Case Study – ACME Corp. Credential Leak

## 1. Executive Summary
During routine monitoring of dark web sources and breach repositories, credentials belonging to ACME Corp. employees were discovered. The dataset includes approximately 3,500 unique email/password pairs exposed in multiple historical breaches and stealer malware logs. The presence of plaintext and weakly hashed passwords represents a significant risk for account takeover (ATO), phishing, and ransomware operations if leveraged by malicious actors.

---

## 2. Threat Actor Background
- **Actors:** Unknown cybercriminals operating on underground forums and marketplaces.  
- **Motivation:** Financial gain, credential resale, or initial access for ransomware affiliates.  
- **Methods:**  
  - Aggregation of breached credentials.  
  - Dissemination via dark web forums and marketplaces.  
  - Stealer malware targeting corporate endpoints.  

---
## 3a. Investigation Timeline
- **2025-09-01:** Dark web crawler flagged bulk ACME credential dump.
- **2025-09-02:** Cross-referenced emails in open breach repositories (HIBP, stealer logs).
- **2025-09-03:** Validated sample hashes against ACME domain via OSINT — confirmed live accounts.
- **2025-09-04:** Reported to ACME security team; forced password resets initiated.

## 3b. Campaign Analysis
- **Discovery Source:** Dark web marketplace and open breach repositories.  
- **Dataset Details:**  
  - ~3,500 email/password pairs linked to `@acme.com` domains.  
  - Mix of plaintext and hashed passwords (MD5/SHA1).  
  - Evidence of password reuse across multiple employee accounts.  
- **Potential Impact:**  
  - Unauthorized access to corporate systems.  
  - Business Email Compromise (BEC).  
  - Possible ransomware entry point.  
  - Expansion of social engineering/phishing campaigns.  

---

## 4. MITRE ATT&CK Mapping
| Technique ID | Name | Observed Use |
|--------------|------|--------------|
| T1078 | Valid Accounts | Use of leaked ACME credentials for unauthorized access |
| T1110 | Brute Force / Credential Stuffing | Testing leaked credentials across corporate services |
| T1556 | Modify Authentication Process | Potential abuse of privileged accounts |
| T1589 | Gather Victim Identity Information | Expanded targeting using corporate email addresses |

---

## 5. Indicators of Compromise (IOCs)
| Type | Value | Description | First Seen | Source |
|------|-------|-------------|-------------|--------|
| Email | jdoe@acme.com | Credential in breach dump | 2025-09-01 | BreachCompilation |
| Email | asmith@acme.com | Credential in stealer logs | 2025-09-02 | Underground forum |
| Domain | acme.com | Corporate domain tied to leaked accounts | 2025-09-01 | Dark web marketplace |

*(All credentials are redacted; this table represents the format only)*  

---
## 6a. Detection Examples
- **Splunk search:** detect >5 failed logins followed by success within 10 min  
  ```spl
  index=auth sourcetype=winlogon
  | stats count as failed by user, src_ip, bin(_time,10m)
  | where failed > 5
-SIEM alert: login from geo-location not seen in last 90 days for a given user.
Suricata rule: flag outbound traffic to known phishing domains tied to campaign.
## 6b. Defensive Recommendations
1. **Force password resets** for all affected users.  
2. **Enable MFA** on all accounts, prioritizing email, VPN, and SaaS logins.  
3. **Deploy monitoring** for credential stuffing and brute force attempts.  
4. **Investigate logins** from unusual IPs/geographies tied to ACME accounts.  
5. **Establish continuous dark web monitoring** to detect future leaks.  
6. **Conduct employee awareness training** focused on phishing threats tied to leaked credentials.  

---

## 7. References
- [Have I Been Pwned (HIBP)](https://haveibeenpwned.com)  
- Hudson Rock – Cybercrime Intelligence on Stealer Logs  
- CrowdStrike MITRE ATT&CK Navigator  
- [The Register – 620M hacked accounts sale](https://www.theregister.com/2019/02/11/620_million_hacked_accounts_dark_web/)  

## 8. Lessons Learned
- Credential reuse and weak hashing continue to fuel ATO and phishing.
- Dark-web monitoring plus identity protection reduces dwell time.
- Need for automated ingestion of leaked credential feeds into SIEM for proactive alerts.
