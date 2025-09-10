# SIM Project : MFA Rollout + Token Lifecycle Governance

**Author:** Marjean Mayo-Baker  
**Status:**  Complete (Phase 1–3)  
**Frameworks:** NIST SP 800-53 Rev. 5, SOX, MITRE ATT&CK for Mobile  
**Project Type:** Governance Simulation (No-code, Real-world Replication)

---

## Objective

This simulation documents a full Zero Trust-aligned Multi-Factor Authentication (MFA) governance rollout using Microsoft Entra ID. It includes a forensic deep dive into token leakage, stale authenticator behavior, recovery loop failure, and policy enforcement breakdowns. All outputs are compliance-aligned and ready for executive, audit, or engineering handoff.

---

## Directory Overview

### `Phase_1_Identity_Access`

| File | Purpose |
|------|---------|
| `Entra ID MFA Rollout.md` | Main rollout strategy and policy enforcement plan |
| `MFA Rollout Project - Entra ID (conditional access).md` | Audit-aligned summary of Entra policy deployment |
| `ZeroTrust_Design_Memo.md` | Core ZTNA enforcement principles (least privilege, deny-by-default) |
| `IAM_Audit_Report.md` | Role-based access grouping, tier model, and audit data |
| `BYOD MFA Token Collision Risk Policy.md` | BYOD device behavior controls for token isolation |

---

### `Phase_2_Threat_Endpoint`

| File | Purpose |
|------|---------|
| `Audit_Log_Playbook.md` | Guide to log coverage, NIST AU-2 mapping, and event granularity |
| `Secure_Device_Baseline.md` | Device-level compliance requirements (BitLocker, AV, logging) |
| `Ghost_MFA_Removal_SOP.pdf` | SOP for removing stale or ghosted authenticator tokens |
| `SOP_MFA_ReRegistration_Issue (1).pdf` | Re-authentication failure and remediation SOP |
| `Entra_Personal_Account_Access_Error.pdf` | Error encountered during guest account usage in Entra |

---

### `Phase_3_Reporting`

| File | Purpose |
|------|---------|
| `Executive_Risk_Brief.md` | For executive review — policy gaps, token risk summary, and next steps |

---

### `Evidence Artifacts`

| File | Purpose |
|------|---------|
| `MFA_Ghost_Test_Compilation.pdf` | Annotated screenshot guide of MFA token behavior tests |
| `MFA_Ghost_Token_Case_Report.pdf` | Full incident-style case report for token leakage |
| `MITRE ATT&CK for Mobile – Policy Control Mapping.md` | Threat behavior mapped to mobile policy controls |
| `MITRE_Mobile_Policy_Mapping.csv` | Raw CSV version of mapping matrix |
| `Pasted image 20250805180138.png` | UI capture of duplicate token issue |

---

### `Folder Placement mfa artifacts real life simulation`

| File | Purpose |
|------|---------|
| `SSPR Token Loop Test – Entra ID Labtled.md` | Test replication of stale token and blocked SSPR recovery |
| `Governance in Action Building Controls That Actually Work.md` | Field notes and internal analysis on practical governance application |

---

### `reference_pack_Framework`

| File | Purpose |
|------|---------|
| `Framework Crosswalks by Phase.md` | Phase-by-phase control mapping to NIST, SOX, MITRE |

### `Resources`

| File | Purpose |
|------|---------|
| `Conditional_Access_Examples.md.md` | Policy snippets and real-world CA logic |

---

## Simulation Highlights

- **Real Entra ID tenant** used for testing token ghost behavior
- Simulated **SSPR recovery loop failure** and stale MFA token residue
- Aligned all artifacts to **NIST SP 800-53**, SOX, and **MITRE ATT&CK (Mobile)**
- Emphasis on *governance maturity, operational clarity, and reproducibility*
- Recommendations provided for Zero Trust, cloud sync disablement, backup lockout, and RBAC enforcement

---

## How to Use

- Present to security leadership as an end-to-end MFA risk scenario
- Replicate for internal lab training (Red vs Blue + Audit)
- Import into Notion, GitHub, or Obsidian as part of the `Forge_SIM` library
- ✍🏽 Use as writing samples for GRC roles or cybersecurity job applications

---

> “This is what happens when security isn’t just policy—it’s practiced, tested, and documented.”

---
**Maintained by:** Marjean Mayo-Baker | Digital Ruins / NullCypher
