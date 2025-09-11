# Audit Log Playbook (v0.1)

**Goal:** Make investigations fast, reliable, and repeatable.

## What to Log

- Identity flows: enrollment, reset, CA decisions
- Admin actions: policy changes, break-glass usage
- Vendor events: auth, token exchanges, webhook failures

## Review Cadence

- Daily: high-severity signals
- Weekly: anomalies & failed CA evals
- Monthly: completeness coverage ≥95%

## Triggers & Actions

- Trigger: Voice-only reset attempt → Action: block + verify via phishing-resistant MFA
- Trigger: Vendor token scope expansion → Action: TPRM review + CA policy diff
