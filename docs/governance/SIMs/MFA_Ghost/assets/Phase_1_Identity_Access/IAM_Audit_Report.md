# IAM Audit Report – Phase

## Meta Data

**Project:** Security Engineer SIM  
**Phase:** Phase 1 – Identity & Access Hardening  
**Author:** Marjean Mayo-Baker  
**Status:** Draft  
**Date:** August 2025  

## Overview

This audit identifies gaps, risks, and misalignments in current identity and access configurations within the organization’s Microsoft Entra ID environment. The goal is to enforce least privilege and prepare for policy-based Conditional Access enforcement.

## Access Tier Inventory

| Tier     | Group                      | Description                                        | Risk Level | Notes                                                                                                                                                                                |
|----------|----------------------------|----------------------------------------------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1        | `SecurityOpsFinanceSecure` | Access to SIEM, financial tools, admin dashboards  | 🔴 High    | Access to security controls and admin tools. This should be a privileged account per person, separate from general access, making logs and audits easier to manage and trace.       |
| 2        | `HRTeam`                   | Access to employee data, onboarding tools, payroll | 🔴 High    | Access to PII and payroll data. Must follow SOX and NIST controls strictly — these users are high-value targets and must be locked down.                                             |
| 3        | `AllEmployees`             | Baseline access to Teams, Outlook, SharePoint      | 🟡 Medium  | This is not low-risk. Any access to the network is a potential attack path. Zero Trust architecture and 'deny by default' principles should still apply here.                        |
| External | `GuestAccess` | External vendor/project access                     | 🔴 High| |

Contractor access must follow Zero Trust principles.
Expiration, review cycles, and limited scope are critical due to external entity involvement.                                  |

## Notable Findings

- 🔴 **No automated revocation process for inactive accounts.**  
  Users placed on leave or pending termination are not immediately removed from access groups. A control should be in place to suspend access until the account is fully re-verified or reactivated.

- 🔴 **MFA enforcement is incomplete across Tier 2 and Tier 3.**  
  HRTeam and AllEmployees groups are not consistently covered by Conditional Access policies. This increases the risk of credential-based compromise, especially in phishing or credential stuffing attacks.

- 🔴 **Legacy Authentication is still enabled in key workloads.**  
  Some mixed environments (e.g., older HR and finance tools) still allow legacy protocols such as IMAP, SMTP AUTH, or POP3. This bypasses Conditional Access enforcement and undermines Zero Trust design.

- 🔴 **Shared credentials were detected in a legacy vendor portal.**  
  This violates basic IAM hygiene and should be deprecated immediately. Access must be tied to individual identities and restricted by device or MAC address where possible.

- 🟡 **Deny-by-default is not uniformly applied.**  
  Default access posture still allows implicit permissions in shared folders, Teams channels, or internal SharePoint sites. This misalignment opens lateral movement pathways post-compromise.
