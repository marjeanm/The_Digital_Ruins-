# Zero Trust Policy Memo

**To:** Internal Security Stakeholders  
**From:** Marjean Mayo-Baker, Security Engineer  
**Subject:** Zero Trust Design Principles – Enforcement, Exceptions, and Access Controls  
**Date:** [Insert Date]

---

## Purpose

- Microsoft Authenticator must be deployed in a manner that prevents unauthorized changes to authentication on personal devices, whether made intentionally by the user or caused by a compromised device.

---

## Core Zero Trust Principles to Enforce

## **Explicit Verification:**  

### In alignment with Zero Trust design, the following enforcement controls must be applied to all identity systems, with no exceptions based on role or risk score

- **Re-authentication is prohibited**  

  Once a user is locked out due to MFA failure or device compromise, credentials must only be re-enabled by an authorized Service Desk technician or administrator. Self-service re-enrollment is disabled by policy.

- **Authenticator Lockout Threshold**  
  Microsoft Authenticator must enforce a lockout policy aligned with standard Windows security baselines. Repeated failed attempts will result in account lockdown until administrative unlock is performed.

- **Centralized Logging Enforcement**  
  All authentication events must be logged and transmitted according to company-wide logging policy. Logs must include time, device ID, user ID, event type, and result, and must remain compliant with disclosures outlined in the EULA and Acceptable Use Policy (AUP).

- **No Risk-Based Access Models Allowed**  
  This organization treats **all MFA challenges as high-risk** events. There is no behavioral or tier-based bypass model permitted. Every authorization attempt is treated uniformly to minimize exploit surface.

- **Signed Policy Acknowledgment Required**  
  All users must have a signed copy of the AUP and EULA on file, verified during onboarding, and retained for the duration of employment to preserve the chain of command and policy accountability.

- **Least Privilege Access:**  
 All users must only be granted the **minimum security rights necessary** to perform their assigned job duties. No account — administrative or general — should retain permissions beyond what is explicitly required for their role.

The organization will implement a formal review of all access control policies to ensure:

- Security groups and permission sets are clearly defined by business function
- Role-based access control (RBAC) models are aligned to actual operational needs
- No shared or inherited permissions are granted without documented justification

> The goal of least privilege is to ensure that every user, at every level, has the **right access at the right time — and nothing more**. This reduces attack surface, limits lateral movement, and enforces accountability across systems.

Security policies will be reviewed and updated to reflect this standard, including:

- Group membership audits
- Role definition and documentation
- Automated alerts for privilege escalation events

Exceptions must be approved through documented change control procedures and reviewed quarterly.

- **Deny by Default:**  
 This organization enforces a strict **Deny by Default** posture for all user, system, and process access — no subject is granted permissions unless explicitly provisioned through a controlled role-based access model (RBAC). Access is mediated by policy-based controls that define allowed actions between subjects and objects.

RBAC enforcement ensures:

- Subjects (users, devices,
services) are only granted access aligned to their job role
- Objects (systems, data, apps) are protected by policy — not assumption
- No implicit access is permitted across inherited groups, default roles, or federated trust

### Controls Audited Under Default Deny

Subjects that have been granted access will be **routinely audited** to ensure they are **explicitly denied** from performing the following actions unless authorized by exception:

- **Downloading or persisting data locally** on non-sanctioned devices or locations (e.g., hard drives), unless through a secure provisioning method (e.g., Software Center, Intune) or direct administrative approval  
- **Delegating privileges** to other subjects or hosts (e.g., sharing access, forwarding tokens, granting roles)  
- **Modifying security attributes**, including access roles, device posture, or identity flags  
- **Altering governance structures** such as changing access control rules, security groups, Conditional Access policies, or audit logging configurations

All governance modifications and privilege escalations must be traceable through a **chain of custody log**, reviewed by the security team, and aligned to change control procedures.

---

 NIST Alignment:

- AC-2 (Account Management)
- AC-3 (Access Enforcement)
- AC-6 (Least Privilege)
- AC-16 (Security Attributes)
- PL-2 (System Security Planning)
- SP 800-207 (ZTA Tenets: No Implicit Trust, Dynamic Access Control)

- **Segmentation and Device Binding:**  

## Segmentation and Device Binding

As part of the organization’s Zero Trust posture, all access must be **contextually bound to the security posture of the originating device** and **limited to only the network segments or applications explicitly permitted** by policy.

### Device Binding Requirements

- Device must be **enrolled, compliant, and trusted** via approved endpoint management (e.g., Intune, JAMF, or MDM/MAM profile)
- Access tokens must be cryptographically linked to the device identity (device compliance + certificate-based auth if applicable)
- Cloud sync or session forwarding from untrusted devices is explicitly prohibited
- Devices not in compliance must be blocked or quarantined via Conditional Access policies

> All access decisions must evaluate both the user’s role and the device's current compliance status before authorizing entry to any protected resource.

---

### Segmentation Enforcement

- Default network posture is **deny-all inbound and outbound traffic**, except for explicitly allowed paths (firewall and NAC enforced)
- Workloads must be logically segmented (e.g., HR apps, Financial data, Security tools) using micro segmentation or network-based ACLs
- Admin tools and privileged systems must reside in **Tier 0 or Tier 1** networks with no direct access from unmanaged or guest endpoints
- Guest Wi-Fi, BYOD zones, and unmanaged endpoints must be firewalled from all production workloads

---

### NIST & ZTA Alignment

- **AC-4:** Information Flow Enforcement  
- **SC-7:** Boundary Protection  
- **AC-17:** Remote Access  
- **SP 800-207 Section 3.4:** Device compliance, PEP/PA enforcement points  
- **PL-8:** Baseline Configuration

> Segmentation and device trust must work in tandem to prevent lateral movement and reduce blast radius. A trusted user on an untrusted device is **still a compromised surface**.

---

## Violations Observed

---

## Recommendations

### Threat Model Alignment – MITRE ATT&CK for Mobile

This Zero Trust policy is informed by real-world adversary behavior documented in the MITRE ATT&CK for Mobile matrix. Specific techniques addressed by this policy include:

- **T1476 – Deliver Malicious App via Authorized App Store**  
  Enforcing app protection and lockout thresholds mitigates scenarios where an attacker replaces or tampers with MFA apps on BYOD devices.

- **T1406 – Credential Access via Input Capture**  
  Disabling self-service reauthentication prevents mobile malware from capturing sensitive reset flows.

- **T1435 – Remote Access Tools**  
  All account recovery must be performed by administrators. This reduces the likelihood of privilege escalation through compromised RAT access. Covered under Acceptable Use Policy (AUP) and access control enforcement.

- **T1513 – Screen Capture**  
  App protection policies must prevent screen capture of authentication prompts, QR code enrollments, and token-based challenges.

- **T1410 – Application Layer Protocol Manipulation**  
  Conditional Access and logging controls detect and restrict unauthorized protocol-level access attempts.

- **T1477 – Supply Chain Compromise**  
  Mandatory signed AUP and EULA acknowledgement ensures users are aware of risk boundaries and security responsibilities when using mobile apps for authentication.

> This policy enforces Zero Trust through explicit controls, administrative gatekeeping, and mobile threat modeling — not assumptions or role-based leniency.

### References

- NIST SP 800-207 – Zero Trust Architecture  
- Microsoft Zero Trust Maturity Model  
- [Optional: anything else you want to cite]

---

✍🏽 *This document is a strategic layer supporting the IAM hardening initiative under the MFA Rollout Project.*
