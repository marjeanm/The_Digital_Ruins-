# Purpose

This policy outlines requirements and guidance for securely using Microsoft Authenticator on personal (BYOD) devices in the context of Entra ID Conditional Access–based MFA enforcement. It mitigates risks of token collision, push notification misrouting, and user privacy concerns by establishing guardrails around identity separation and device configuration.

---

## Scope

Applies to all employees, contractors, and vendors who access organizational systems using personal mobile devices and are required to enroll in Multi-Factor Authentication (MFA) via Microsoft Authenticator.

---

## Risk Summary

Authenticator apps like Microsoft Authenticator support multiple accounts, including both work and personal identities. However, without clear separation, this can introduce risks such as:

- Cross-account push notification confusion

- Token overwrite or sync failures during re-enrollment
- Enforcement issues caused by shared aliases or cached credentials
- User resistance due to privacy fears on personal devices

---

## Policy Requirements

1. **Separate Identity Domains**
   - Employees must not use the same email address for both personal and work Microsoft accounts.
   - Personal Microsoft accounts must not list the corporate email as an alias or recovery method.

2. **Profile Separation**
   - Where possible, users must enroll their work account using a **Work Profile** or **App Protection Policies (MAM)** to contain the authentication environment.
   - Entra Conditional Access will be configured to detect and enforce MAM compliance on unmanaged devices.

3. **App Labeling**
   - Users must clearly label Authenticator entries (e.g., " Work – Marjean" vs "Personal – Marjean") to reduce push notification confusion.

4. **No Shared Authenticator Apps on Shared Devices**
   - Shared tablets or kiosks must not be used for personal Authenticator enrollment.
   - If shared use is required, user profiles must be enforced at the OS level.

5. **No Enforcement Without Transparency**
   - Users must be provided with an MFA Setup Guide clarifying:
     - What data is accessed (none from personal accounts)
     - How to install without affecting personal tokens
     - What happens in the event of a policy wipe

---

## Support Guidance

Users experiencing issues with Microsoft Authenticator on BYOD devices should contact the IT Service Desk. Troubleshooting may include:

- Reviewing app install location (personal vs work profile)

- Checking for push notification mismatches

- Verifying conditional access device compliance
- Re-enrolling tokens if necessary

---

## Related Documents

- `MFA_Rollout_Plan.md`
- `Access_Control_Policy.md`
- `User_Communication_Email.md`
- `MFA_Troubleshooting_Guide.md` (in progress)

---

 *This document supports Phase 1 – Identity & Access hardening under the Security Engineer SIM Project.*