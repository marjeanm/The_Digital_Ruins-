# Forge SIM Framework Crosswalks by Phase

This document provides per-phase framework mapping for Forge-style cybersecurity simulations. Each control or security objective is aligned with:

- NIST SP 800-53 (primary)

- CIS Controls v8

- ISO 27001

- MITRE ATT&CK (where applicable)

- Regulatory tie-ins (SOX, HIPAA, PCI)

Use this doc to support:

- SIM writeups

- Obsidian memory chunks

- Governance templates

- Audit references

---

## Phase 1: Identity & Access Hardening

| Control Area       | NIST 800-53 | CIS v8    | ISO 27001 | MITRE ATT&CK | Notes                                               |
| ------------------ | ----------- | --------- | --------- | ------------ | --------------------------------------------------- |
| MFA Enforcement    | IA-2, IA-5  | 6.3, 6.6  | A.9.4.2   | T1110, T1556 | Use Conditional Access + push fatigue protection    |
| Least Privilege    | AC-6        | 4.6       | A.9.1.2   | T1078        | Role-based access controls only; no shared creds    |
| Deny by Default    | AC-3        | 4.4       | A.9.1.1   | T1021, T1548 | Set baseline deny on all assets, escalate by need   |
| Auth Logging       | AU-2, AU-6  | 8.1, 8.2  | A.12.4.1  | T1005, T1082 | Forward to SIEM or MDR solution for centralization  |
| Risk-Based Tiering | PM-11, RA-3 | 6.1, 14.2 | A.8.2.1   | T1203        | Tiered user groups (e.g. Admins, HR, Staff, Guests) |
| User Comms & AUP   | PL-4, AT-2  | 14.1      | A.7.2.2   | –            | Signed EULA, onboarding training, and audit trail   |

---

## Phase 2: Segmentation & Device Binding

|Control Area|NIST 800-53|CIS v8|ISO 27001|MITRE ATT&CK|Notes|
|---|---|---|---|---|---|
|Network Segmentation|SC-7, AC-4|13.1, 13.3|A.13.1.1|T1071|Use logical and physical boundaries; VLANs, subnets|
|Device Binding|CM-6, IA-3|1.2, 5.4|A.6.2.2|T1200|Enforce workstation identity to specific accounts|
|Cloud Sync Restriction|SC-12, SI-7|10.4|A.13.2.3|T1530|Disable auto sync via GPO or MDM|
|Role-Based Segmentation|AC-2, AC-5|4.1|A.9.1.1|T1557|Separate domains/zones by function + risk|
|Remote Admin Lockdown|AC-17, SC-12|13.3|A.13.1.3|T1071.001|Restrict RDP/VPN to defined devices only|

---
