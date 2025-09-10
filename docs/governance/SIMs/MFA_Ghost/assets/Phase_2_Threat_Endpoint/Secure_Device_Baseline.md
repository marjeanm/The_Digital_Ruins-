# Purpose

To establish a minimum security configuration standard for all organizational devices (laptops, desktops, mobile, virtual machines) accessing corporate resources. This baseline enforces core principles of Zero Trust, device hygiene, and access control.

## Framework Alignment

- **NIST SP 800-53 Rev. 5**
  - CM-6: Configuration Settings
  - CM-7: Least Functionality
  - AC-19: Access Control for Mobile Devices
  - SC-28: Protection of Information at Rest
  - SC-12: Cryptographic Key Establishment
- **CIS Controls v8**
  - Control 4: Secure Configuration of Enterprise Assets and Software
  - Control 5: Account Management
  - Control 10: Malware Defenses

## Required Controls

### 1. Identity & Access

- MFA enforced (Microsoft Authenticator only)

- No re-authentication overrides allowed
- Lockout threshold must be enforced and controlled by admin or service desk
- RBAC enforced on all privileged applications

### 2. Device Configuration

- BitLocker (or equivalent) must be enabled for all endpoints
- Local administrator rights prohibited except for authorized IT staff
- BIOS and bootloader password protection enabled
- USB and peripheral access restricted to policy-based exceptions

### 3. Endpoint Protection

- Microsoft Defender or corporate AV must be installed and active
- Real-time protection and auto-remediation enabled
- Device must pass compliance checks before accessing any enterprise application

### 4. Logging & Monitoring

- Logging must be enabled and forwarded to central log collector
- Events: Authentication attempts, privilege escalation, USB insertions, cloud sync attempts
- Logs retained per retention policy (90 days minimum)

### 5. Cloud Sync & Data Loss Prevention

- OneDrive and iCloud sync must be disabled by default
- Clipboard, screen capture, and print redirection restricted in VDI or BYOD environments
- File transfers monitored and restricted by policy

## Exceptions & Waivers

All deviations from the secure device baseline must:

- Be approved by the Security Governance team
- Include a documented business justification
- Be reviewed every 90 days

## Enforcement

Non-compliant devices will be denied access via Conditional Access Policy.
User remediation will occur through Service Desk or automated compliance workflows.

## Artifacts

- Screenshot: BitLocker enabled
- Screenshot: Conditional Access Policy with device filter
- Screenshot: Defender compliance portal view

## Related Policies

- [MFA Governance Policy](../MFA_Governance/README.md)
- [Executive Risk Brief](../Executive_Risk_Brief/README.md)

---
*Maintained by Governance
Engineering — Last Reviewed:
