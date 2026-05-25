# Incident Response Report: MidnightSwap Multi-Stage Attack

**Client:** Reyts Fintech  
**Analyst:** Obu Chukwuemeka Godwin  
**Date:** Monday, 30th March 2026  
**Case ID:** CS01 – MidnightSwap Multi-Stage Attack  

---

## Executive Summary

A comprehensive investigation of authentication and system logs revealed a **multi-stage cyber-attack** involving phishing, account takeover, privilege escalation, and ransomware deployment.

The attacker successfully compromised user credentials, gained unauthorized access, escalated privileges, and executed ransomware, causing significant security impact.

---

## Key Findings

### Phishing Campaign
- **48 phishing link clicks detected**
- **18 credential harvesting events**

Users were successfully tricked into revealing credentials.

![Phishing Campaign - Splunk Dashboard](images/screenshot-phishing.png)

### Account Takeover
- Over **7,500 login events** observed
- High activity from suspicious IPs:
  - `10.0.0.47`
  - `77.91.85.97`
  - `194.165.16.11`

Indicates compromised accounts and automated attack behaviour.

![Account Takeover - Splunk Logs](images/screenshot-account-takeover.png)

### MidnightSwap Attack
- Significant abnormal activity observed between **00:00 and 04:00**, consistent with the MidnightSwap attack pattern.
- Deliberate exploitation of low-monitoring hours.

![MidnightSwap Activity - Splunk](images/screenshot-midnightswap.png)

### Advanced Intrusion Activity
Detailed log analysis revealed advanced attacker behavior beyond initial compromise:

- Multiple privilege escalation attempts
- Successful administrative panel access
- Execution of database schema dump operations
- Confirmed data exfiltration activity

These actions demonstrate the attacker successfully transitioned from initial access to **deep system-level control**.

![Advanced Intrusion - Splunk](images/screenshot-advanced-intrusion.png)

### Ransomware Execution
Analysis confirmed a fully executed ransomware attack with the following indicators:

- `RANSOMWARE_ENCRYPTION_STARTED`
- Over **200 file encryption events**
- `SHADOW_COPIES_DELETED` (backups wiped)
- Deployment of a ransom note

The sequence and volume of events demonstrate a **complete ransomware lifecycle**.

![Ransomware Logs - Splunk](images/screenshot-ransomware.png)

---

## Attack Timeline

| Time                      | Activity                                      |
|---------------------------|-----------------------------------------------|
| Early Nov 14              | Phishing Campaign initiated                   |
| Midday                    | Multiple failed login attempts detected       |
| Afternoon                 | Successful logins from unusual IPs            |
| Evening                   | Account Takeover Confirmed                    |
| Late Night (00:00–04:00)  | MidnightSwap transactions executed            |

---

## Impact Assessment

- Unauthorized system access
- Sensitive data exposure
- File encryption and operational disruption
- Financial fraud risk

---

## Root Cause

- Lack of Multi-Factor Authentication (MFA) enforcement
- Poor phishing awareness among users
- Insufficient anomaly detection

---

## Recommendations

### Immediate Actions
- Reset all compromised accounts
- Block malicious IP addresses
- Isolate infected systems

### Security Improvements
- Enforce **MFA across all users**
- Deploy SIEM alert rules for:
  - Midnight activity
  - Multiple failed logins
  - Suspicious IP behaviour

### Long-Term Strategy
- Security awareness training
- Endpoint Detection & Response (EDR)
- Regular penetration testing

---

## Conclusion

The investigation confirms a **highly coordinated multi-stage attack** combining social engineering, credential compromise, and ransomware deployment.

**Immediate remediation and stronger monitoring controls are required to prevent recurrence.**

---

## Repository Contents

- `INCIDENT-RESPONSE-REPORT.md` → This file (full report)
- `/images/` → All Splunk dashboard screenshots from the original PDF
- `/logs/` → (Optional) Raw log samples (if available)
- `/recommendations/` → Detailed remediation playbook

---

**Prepared by:** Obu Chukwuemeka Godwin  
**For:** Reyts Fintech Security Team  

