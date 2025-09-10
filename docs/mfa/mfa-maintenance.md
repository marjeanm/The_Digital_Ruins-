---
title: MFA Maintenance 
---


Operational guardrails to keep MFA healthy, auditable, and resilient.

> Goal: phishing-resistant MFA enforced by policy, continuously verified by telemetry, and recoverable during auth outages.

---

## 1 Scope & Objectives

- **Scope**: Entra ID MFA, Conditional Access (CA), device compliance signals, SSPR, FIDO2/security keys, Authenticator.
- **Objectives**:
  1. Maintain **deny-by-default** with least privilege.
  2. Detect and correct **policy drift** within 24h.
  3. Keep **break-glass** usable but locked down.
  4. Preserve **SOX evidence** of control operation.

---

## 2 Roles (RACI)

| Activity | SecEng | IAM | Helpdesk | Audit/GRC |
|---|---|---|---|---|
| CA policy changes | **R** | C | I | A |
| Break-glass rotation | **R** | C | I | A |
| Token reset SOP | C | **R** | **R** | I |
| Evidence pack | **R** | C | I | **A** |
| App MFA onboarding | **R** | **R** | I | I |

**R**=Responsible, **A**=Accountable, **C**=Consulted, **I**=Informed

---

## 3 Monitoring & Alerts (what to watch)

- **Sign-in risk spikes** (Impossible travel, unfamiliar sign-ins)
- **MFA prompt fatigue / surge** (>3 denials per user/day)
- **CA policy evaluation errors**
- **Break-glass sign-ins** (should be near-zero)
- **SSPR reset failures** / lockouts
- **Disabled MFA methods** (user tampering, device wipe)

> Route critical alerts to: SecEng on-call + IAM channel.

---

## 4 Health KPIs & Targets

- **MFA Coverage**: ≥ 99.5% active users protected
- **FIDO2 adoption** (Tier-1 users): ≥ 80%
- **Prompt-bomb false accepts**: 0
- **Break-glass use**: ≤ 1 per quarter (with ticket & RCA)
- **Policy drift MTTR**: < 24h
- **SSPR success rate**: ≥ 95%

---

## 5 Cadence Checklist

### Daily

- Review **Risky sign-ins** & **MFA failures**
- Verify no **new exclusions** were added to CA
- Triage **alert spikes** (prompt fatigue, unfamiliar sign-ins)

### Weekly

- Export **CA policy diff** vs baseline (store in evidence)
- Sample **10 users**: confirm effective controls (sign-in logs)
- Validate **break-glass credentials** _without interactive sign-in_ (see Runbook)

### Monthly

- Rotate **Authenticator notification** to **number-matching** required (enforced)
- **Hardware key inventory** check (lost/retired keys revoked)
- **SSPR flow test** with non-privileged account
- Update **evidence pack** (see Section 9)

### Quarterly

- **Break-glass rotation** (password + recovery secrets)
- **CA policy attestation** (owners re-approve)
- **App review**: ensure all enterprise apps have MFA enforcement
- **Tabletop**: MFA outage / IdP failover drill

---

## 6 Change Management (CA & MFA)

- All changes require:
  - **Change ticket** + risk summary
  - **Before/after policy snapshot** (YAML/JSON export or screenshot)
  - **Test plan** (pilot group, rollback path)
  - **Post-change verification**: sample sign-in results
- **Never** deploy new exclusions globally; scope to **security groups** with expiry.

---

## 7 Exceptions & Temporary Bypass

- **Who can approve**: IAM Manager + SecEng (time-boxed, max 7 days)
- **How to enforce**:
  - Add user/device to **“MFA-Exception-7d”** group with **Access Review** enabled
  - Auto-expire membership; alerts on renewal
- **Evidence**: ticket link, justification, expiration, compensating controls

---

## 8 Break-Glass Runbook (High Level)

- **Accounts**: 2 cloud-only Global Admins, strong passwords, **no MFA**, sign-in restricted by **named locations**.
- **Storage**: Passwords + recovery sealed in enterprise vault with dual-control checkout.
- **Weekly non-interactive check**: confirm the accounts still **exist & are enabled** (do not sign in).
- **Quarterly rotation**: new passwords, re-confirm named locations, test sign-in only during scheduled window with observers + ticket.

---

## 9 SOX / Audit Evidence (what to save)

- Monthly **CA policy exports** (or screenshots) + diff report

- **Risky sign-ins** & **MFA failure** trend charts (90 days)
- **Access Reviews** results for admin & exception groups
- **Break-glass rotation** proof (vault logs, ticket, witness)
- **Change tickets** with test results & rollback notes
- **App inventory** with MFA status per app

> Store under: `evidence/MFA/<YYYY-MM>/…`

---

## 10 New App Onboarding (MFA Enforcement)

1. Classify data sensitivity & user tier.

2. Prefer **OIDC/SAML** with IdP-initiated SSO.
3. Test with **pilot** group under standard CA policies.
4. Block legacy/basic auth; require **compliant device** where applicable.
5. Document app entry in **App Register** (owner, contact, scopes, MFA posture).

---

## 11 Incident Snippets (quick actions)

### MFA Prompt Bombing

- Force **sign-out** for user sessions

- Require **password reset + method re-bind**
- Move user to **FIDO2 only** (temporarily disable push)
- Open RCA; hunt for token theft (impossible travel, TOR/VPN)

### Auth Outage / IdP Degradation

- Activate **contingency CA** (reduced friction policy for core SaaS)

- Post status to users, freeze non-essential changes
- Use **break-glass** only for restoration tasks
- After recovery: reconverge to baseline, document variance

---

## 12 Useful Queries & Cmdlets (placeholders)

> Replace filters with your tenant specifics before use.

**Entra sign-ins (failed MFA, last 24h)**  

Prompt fatigue detector

```markdown

SigninLogs
| where ResultType in ("50074","500121","50097")  // MFA failures
| where TimeGenerated > ago(24h)
| summarize count() by UserPrincipalName, ResultType

```

```powershell
Get-MgUserAuthenticationMethod -UserId user@domain.com
```

```powershell

# Get-MgIdentityConditionalAccessPolicy | ConvertTo-Json | Out-File ".\evidence\MFA\$(Get-Date -f yyyy-MM)\ca_policies.json"
```

## 13 Baseline Guardrails

- Require number-matching + show geographic context in Authenticator.

- Prefer FIDO2 security keys for admins &     Tier-1 users.

- Block legacy/basic auth everywhere.

- Restrict admin sign-ins to named locations & compliant devices.

- No permanent MFA exclusions.Ever
