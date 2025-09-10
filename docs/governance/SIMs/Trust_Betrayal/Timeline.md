# Trust_Betrayal – Timeline

**Incident ID:** SIM-TRUST-2025-01  
**Date:** [Insert Date]  
**Author:** Marjean Mayo-Baker | GRC Simulation Architect  

---

## Event Log

**09:02** – End user reports slow login + unresponsive system.  
**09:08** – Analyst initiates credential reset without verifying logs.  
**09:10** – SOC alert triggers: **527 brute-force login attempts** detected against account.  
**09:12** – Login script anomaly observed (missing/delayed execution).  
**09:15** – Incident owner escalates to SOC with ticket ID + justification.  
**09:18** – Analyst displays defensiveness when corrected on login script impacts.  
**09:22** – SOC Manager accepts escalation, validates brute-force pattern, and signs escalation record.  
**09:30** – Account locked; brute-force source IP range blocked.  
**09:45** – Escalation chain-of-custody documented in governance register.  

---

## Notes

- Initial reset request mishandled by analyst due to lack of validation.  

- Escalation was delayed by cultural defensiveness but ultimately accepted.  
- Event mirrors **ShinyHunters (Google/Salesforce 2025)** breach pattern: trust assumed, not verified.  
- Proper chain-of-custody escalation ensured incident was contained before full compromise.  

---

## Chain-of-Custody Sign-Off

- **Incident Owner:** __________________________  
- **SOC Manager:** __________________________  
- **GRC Oversight:** __________________________  
