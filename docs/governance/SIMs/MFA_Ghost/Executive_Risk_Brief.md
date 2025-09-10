# Executive Risk Brief: MFA Governance + Token Leakage Findings

## Summary

This Executive Risk Brief outlines the findings and recommendations related to the observed behavior of Microsoft Authenticator token reuse, token persistence after deletion, and ghosted MFA artifacts during re-registration. The documented test scenarios stem from an internal sandbox environment using Microsoft Entra ID and Azure Conditional Access.

## Objective

To evaluate and document risk exposure related to misconfigured or lingering MFA configurations within Entra ID that could:

- Compromise Zero Trust enforcement
- Obstruct account recovery
- Allow unauthorized or persistent access to outdated credentials

## Incident Overview: Token Leakage and Ghosted Artifacts

### Discovery Context

- During leave, MFA re-registration attempts failed for the same user account.

- Once back on the network, MFA re-registration was possible — yet stale authenticator tokens remained visible in the Microsoft 365 Security Info page.

- Even after deleting and re-adding MFA tokens through Entra ID, the original authentication method remained in the background and re-synced based on device behavior.

### Conditions That Caused Persistence:

- MFA token was backed up to cloud storage on primary phone

- Authenticator app had not been fully reset, even across devices

- Manual re-registration did not fully override existing entries

## Risk Statement

Residual authenticator tokens create hidden identity artifacts that:

- May allow shadow access or spoofed push notifications
- Prevent clear governance enforcement of Conditional Access
- Create inconsistency in audit trail, incident response, and forensic clarity
- Undermine device-to-user binding in Zero Trust environments

## Tested Scenarios (Screenshots Documented)

- ✅ Deleting MFA token from Entra ID UI
- ✅ Re-adding from tablet device

- ✅ Cloud backup toggled ON vs. OFF
- ✅ Browser (Chrome regular & incognito)
- ✅ Removal through Security Info page vs. Authenticator app
- ✅ Security info visibility showing duplicate/mirrored tokens

## Recommendations

1. **Policy Enforcement:**
    - Disable Authenticator cloud backups on managed devices

    - Enforce Conditional Access policies to require MFA device binding

    - Disallow re-registration of MFA unless prior tokens are purged by IT

2. **Administrative SOPs:**

    - Create step-by-step removal SOP for ghost entries (Device + Security Info)

    - Include Entra ID + Microsoft Authenticator + AUP coverage
3. **Governance Alignment:**

    - Integrate AU-2 (Event Logging), AC-2 (Account Management), and IA-2 (Identification & Authentication) NIST controls

    - Require signed AUP and tracking of MFA enrollment changes

4. **Forensic Controls:**
    
    - Store deletion timestamps and device metadata
        
    - Flag duplicate tokens or backup restores for admin review
        

## Business Impact

If unaddressed, lingering MFA token entries could result in:

- Failed login audits
    
- Incorrect incident attribution
    
- Elevated risk of impersonation or lateral movement
    
- Noncompliance with SOX, HIPAA, or internal AUP
    

## Conclusion

MFA governance must account for hidden persistence mechanisms across Microsoft Authenticator deployments. This brief calls for an updated SOP, token hygiene enforcement, and executive visibility into Zero Trust enforcement gaps.



