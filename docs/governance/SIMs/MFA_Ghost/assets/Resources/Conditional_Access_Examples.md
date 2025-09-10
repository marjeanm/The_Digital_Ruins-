
# Conditional Access Examples

This document outlines example Conditional Access (CA) policies designed to align with Zero Trust principles and enforce strong authentication across identity tiers.

## 🎯 Purpose
To provide structured, risk-aligned examples of Conditional Access configurations that can be applied in Microsoft Entra ID.

---

## 📌 Policy 1: Require MFA for All Users

**Scope:** All users  
**Target Resources:** All cloud apps  
**Conditions:** None  
**Access Controls:** Grant access, require multi-factor authentication

---

## 🔒 Policy 2: Block Legacy Authentication

**Scope:** All users  
**Target Resources:** All cloud apps  
**Conditions:** Client apps = legacy authentication protocols  
**Access Controls:** Block access

---

## 🧠 Policy 3: High-Risk Sign-In Block

**Scope:** All users  
**Target Resources:** All cloud apps  
**Conditions:** Sign-in risk = High  
**Access Controls:** Block access

---

## 🌍 Policy 4: Location-Based MFA

**Scope:** All users  
**Target Resources:** All cloud apps  
**Conditions:** Locations = Outside trusted IP range  
**Access Controls:** Require MFA

---

## 🧪 Policy 5: Pilot Group MFA Exemption

**Scope:** Specific users (pilot group)  
**Target Resources:** All cloud apps  
**Conditions:** None  
**Access Controls:** Grant access (no controls)

