# SSPR token Loop test

**Author:** Marjean Mayo-Baker  
**Phase:** Phase 2 – Incident Replication & Recovery Analysis  
**Project:** Forge SIM – MFA + Recovery Risk Modeling  
**Tag:** [EntraID, MFA, TokenLeakage, ZeroTrust, SSPR, IncidentResponse]  

---

## Purpose

This simulation replicates a previously observed **authentication loop** during password reset and token recovery scenarios in Microsoft Entra ID. The goal is to validate whether **Self-Service Password Reset (SSPR)** can recover accounts when MFA tokens on personal devices are stale, missing, or invalid — and to highlight the **risk of token leakage and policy misalignment**.

---

## Test Setup

### Test User Account

- Username: `test.

```markdown
employee@yourdomain.onmicrosoft.com
```

- Group Membership: `AllEmployees`  

- MFA Config: Microsoft Authenticator App (Primary)

### Policies Applied

- Conditional Access: Require MFA
- SSPR Enabled:  Yes  
- Auth Methods: Phone + Authenticator  
- Token Persistence Setting: (Record what you chose)

---

## Test Actions

| Step | Action | Expected Result | Actual Result | Notes |
|------|--------|------------------|----------------|-------|
| 1 | Log in with working MFA | Successful login|
| 2 | Simulate lost access to Authenticator | Remove device or uninstall app | Should trigger fallback | |
| 3 | Trigger SSPR | Visit https://aka.ms/sspr | SSPR prompts for alternate auth | |
| 4 | Attempt reset | Enter backup method | Password reset succeeds/fails | |
| 5 | Re-login post-reset | MFA required again? | Token reissued? | |
| 6 | Inspect logs | Azure Sign-in logs | Show failure loop? | |

---

## Failure Observation

> _"User could not regain access after MFA reset due to stale token still cached or enforced by CA. SSPR failed to break the cycle."_  

Summarize exactly what broke and what couldn't be reset. Include screenshots if possible.

---

## Root Cause

- Token tied to compromised/unavailable device
- SSPR required MFA, which user couldn’t complete
- No alternate recovery
- No policy to revoke stale tokens on logout or reset
- Conditional Access had no bypass in place for SSPR failures

---

## Governance Impact

| Area | Risk | Impact |
|------|------|--------|
| Identity Recovery | High | User permanently locked out |
| Incident Response | Moderate | Manual intervention required |
| Token Lifecycle Control | High | Persistent session across devices |
| Audit & Logging | Medium | Logs show failure loop but no resolution |

---

## Recommendations

1. **Enforce token revocation** on password reset (Session Control).
2. Add **secondary MFA method** that does not rely on same device.
3. Document escalation path for recovery failures.
4. Log all failed MFA and SSPR attempts with enhanced telemetry.
5. Require service desk unlock when MFA fails.
6. Disable token reuse outside org-owned device binding.

---

## Reference Controls

- **NIST SP 800-53 Rev. 5**
  - IA-2: Identification and Authentication
  - IA-11: Device Authentication
  - AC-12: Session Termination
  - AU-14: Non-Repudiation

- **Microsoft Docs**
  - [Configure SSPR](https://learn.microsoft.com/en-us/entra/identity/users/user-password-reset)
  - [SSPR and MFA overlap](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-methods)
  - [Token Lifetime Policies](https://learn.microsoft.com/en-us/entra/identity/conditional-access/howto-conditional-access-session-lifetime)

---

## Evidence Artifacts

- `screenshots/login_failures/`
- `sign_in_logs.csv`
- `token_reset_behavior.md`
- `Conditional_Access_Config.json`

---

> Prepared for internal review by Security Governance.  
> Demonstrates risk of token dependency in Entra environments using hybrid MFA + SSPR models.

