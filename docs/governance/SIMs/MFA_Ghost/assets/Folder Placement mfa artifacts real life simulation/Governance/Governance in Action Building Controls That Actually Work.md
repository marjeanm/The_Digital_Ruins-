# Purpose

Governance isn't just paperwork. It's the system that keeps power, data, and people in check — and I learned to build it from the ground up.

## Project Focus

**Simulation:** Forge SIM – Identity, Access & Policy Governance  

**Duration:** Phase 1–2, spanning 3 weeks  

**Tools Used:** Microsoft Entra ID, Conditional Access, NIST SP 800-53, MITRE ATT&CK, Markdown policy templates, custom Notion dashboards  

**Artifacts Created:**

- Zero Trust Policy Memo

- Access Control Policy

- MITRE to Policy Mapping Table

- MFA Ghost Token SOP (PDF)

- Audit Log Playbook (in progress)

## Scenario

You stepped into a security team that lacked documentation for enforcing identity governance. The environment had ghost MFA tokens, guest access misconfiguration, stale Authenticator keys, and no formal control mapping to risk frameworks. You identified, documented, and resolved key gaps using a Zero Trust approach.

## Controls Implemented

### 1. Least Privilege & Deny by Default

- RBAC applied across Entra groups: `SecurityOpsFinanceSecure`, `HRTeam`, etc.  

- Default access removed from `AllEmployees` and `GuestAccess`  

- **Controls:** NIST AC-2, AC-6

### 2. MFA Enforcement via Conditional Access

- CA policy scoped to specific Entra groups  

- Lockout thresholds, no re-authentication without admin/service desk  

- Token ghosting resolved through device logging + re-registration SOP  

- **Controls:** IA-2, IA-5, SC-12

### 3. Audit Logging (In Progress)

- Purpose section drafted  

- **Framework:** NIST SP 800-53 Rev. 5 – AU-2  

- Event types, coordination, frequency to be documented

### 4. MITRE ATT&CK to Policy Mapping

- Mobile threats like `T1519` (Screen Capture) and `T1406` (Remote Access Tools) linked directly to CA enforcement and EULA restrictions  

- Used MITRE for mobile to build preventative controls into governance

## Technical Outcome

- Recreated stale token scenario via Entra sandbox  

- Tested MFA registration workflows across devices  

- Confirmed cloud backup causes ghost entries  

- Documented SOP for stale token removal and prevention  

- Created a write-up suitable for team escalation and training

## Lessons Learned

- MFA enforcement without stale token cleanup causes access denial  

- Governance must address both **technical controls** and **human processes**  

- Even small oversights (e.g., reused Authenticator slots) create long-tail vulnerabilities  

- Documentation isn’t an afterthought — it’s the only evidence you did it right

## Your Role

You acted as Governance Analyst, IAM tester, and Policy Architect — proactively identifying a security flaw, recreating it in a test lab, mapping it to compliance frameworks, and delivering a fully written SOP that protects your team and company from repeat incidents.

## Folder Placement

Store in:

- `Forge_SIMs/Governance/`

- `Evidence_Artifacts/MFA_Ghost_Token_SOP.pdf`

- `Policies/ZeroTrust_Memo.md`

- `Controls/MITRE_Policy_Map.md`

- `Audit_Log_Playbook.md`

---
