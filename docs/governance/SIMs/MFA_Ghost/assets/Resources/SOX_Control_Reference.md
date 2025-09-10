
# SOX Control Reference – MFA Governance Alignment

This document maps SOX (Sarbanes-Oxley) compliance expectations to the MFA governance and enforcement rollout in this simulation.

## 🎯 Objective
Ensure that identity access controls meet SOX mandates for financial system integrity.

---

## 🛡️ Relevant SOX Sections

| Section | Description                             | MFA Relevance |
|---------|-----------------------------------------|---------------|
| 302     | Corporate Responsibility for Reporting  | MFA ensures executive authentication |
| 404     | Internal Control Effectiveness          | Enforces identity-based internal controls |
| 409     | Real-Time Disclosure                    | Secures real-time access to reporting systems |

---

## 🔐 MFA Governance Controls

- **Control ID:** MFA-001  
  **Description:** All users must register and use MFA for access to corporate systems.  
  **SOX Tie-In:** Internal control under 404

- **Control ID:** MFA-002  
  **Description:** Legacy authentication protocols are blocked to prevent insecure access.  
  **SOX Tie-In:** Prevention of unauthorized disclosure (302)

- **Control ID:** MFA-003  
  **Description:** Admin role access must be confirmed with number-matching and geo validation.  
  **SOX Tie-In:** Mitigates risk of unauthorized changes to financial data

---

## 📎 Reporting and Logging

All policy enforcement events are logged via:
- Entra Sign-In Logs
- Audit Logs
- Risky Sign-In Reports

Recommended: Integrate logs into SIEM for alerting.

