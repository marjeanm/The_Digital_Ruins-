---
title: Access Governance Assessment
---

<article class="dr-case-study" markdown>
  <header class="dr-case-header"><div><p class="dr-kicker">Case Study // Identity &amp; Access</p><h1>Access Governance Assessment</h1><p class="dr-case-deck">An 18-finding compliance crosswalk translating employee, remote, privileged, application, and file-access observations into evidence and remediation decisions.</p></div><div class="dr-case-status"><span class="dr-status dr-status--available">Available</span><span>Public crosswalk included</span></div></header>

## Overview

This case study uses a completed Access Control Compliance Crosswalk to demonstrate how technical access findings become governance categories, control themes, evidence needs, and remediation priorities. Of the 18 source findings, **14 are marked noncompliant and four compliant**.

## Scenario

The source assessment concerns the fictional Grey Matter organization and its legacy BrainMeld environment. The portfolio document places that source inside the broader AQT scenario wrapper while clearly retaining the original context. Review areas include employee access, a legacy VPN, system-administrator access, web applications, and file services.

> Aegis Quantum Trust is a fictional enterprise environment used across selected portfolio projects to demonstrate governance, risk, compliance, audit, security, and AI governance decision-making in a consistent business context.

## Objective

Preserve the source compliance status and control references while organizing each finding into an audit-ready crosswalk: condition, control issue, control theme, evidence needed, recommended remediation, responsible area, and current status.

## My Approach

1. Preserved all 18 source findings and their stated Yes/No compliance status.
2. Grouped findings by access domain and governance concern.
3. Connected issues to privileged access, remote access, RBAC, centralized control, logging, vendor access, and data governance.
4. Identified evidence that would prove the control state rather than assuming implementation.
5. Built a remediation tracker with priority, responsible area, status, and notes.
6. Labeled interpretive mappings as “Suggested for future polish” and missing source details as “Not stated in source.”

## Frameworks & Methods

- Source control references including AC-1, AC-2, AC-3, AC-4, AC-5, AC-8, AC-9, and AC-10
- Least privilege and role-based access principles
- Privileged-account separation and accountability
- Remote access, MFA, logging, and segmentation review
- Evidence sufficiency and remediation tracking
- NIST CSF-style functions used only as explicitly labeled portfolio framing aids

## Key Findings

- Regular user accounts and departmental directors appear in privileged administrative roles, weakening separation and least privilege.
- The legacy VPN provides broad, same-level access without consistently demonstrated MFA, granular RBAC, or monitoring evidence.
- Shared local-administrator credentials reduce traceability across endpoints.
- Vendor and contractor remote access requires stronger centralized control, business justification, and periodic review.
- Default cloud and mapped-drive visibility exposes more file structure and data than business need requires.
- Four compliant findings are retained as compliant; the case study does not manufacture remediation work where none is needed.

## What This Demonstrates

IAM analysis, access-control assessment, privileged-access review, compliance crosswalking, evidence planning, audit readiness, vendor-access governance, and risk-based remediation.

## Artifact Preview

<div class="dr-evidence-grid" aria-label="Access assessment metrics">
  <div><strong>18</strong><span>Total findings</span></div>
  <div><strong>14</strong><span>Control gaps</span></div>
  <div><strong>04</strong><span>Compliant</span></div>
  <div><strong>05</strong><span>Review areas</span></div>
</div>

<div class="dr-table-scroll" markdown>

| ID | Source area | Control issue | Priority framing | Responsible area |
| --- | --- | --- | --- | --- |
| ACF-01 | Employee Access | Domain credentials retain local-administrator rights | Medium | Identity & Access Governance |
| ACF-07 | Legacy VPN | Privileged remote access lacks documented MFA, separation, and logging | High | Identity & Access Governance |
| ACF-08 | Legacy VPN | Vendors and contractors appear to have broad access | High | Vendor & SaaS Governance |
| ACF-10 | System Administrator Access | Department directors hold Domain Administrator privileges | High | Identity & Access Governance |
| ACF-12 | System Administrator Access | Shared local-administrator account and password | High | Identity & Access Governance |
| ACF-17 | File Services Access | Broad default cloud-file access | High | Data Governance |

</div>

## View / Download Artifact

<div class="dr-artifact-access">
  <div><p class="dr-card-meta">Public artifact</p><h3>Access Control Compliance Crosswalk</h3><p>Download the full 18-finding crosswalk and evidence/remediation tracker.</p></div>
  <div class="dr-download-actions"><a class="dr-button dr-button--primary" href="../../assets/artifacts/AQT_Access_Control_Compliance_Crosswalk.docx" download>Download DOCX</a><button class="dr-button" type="button" onclick="window.print()">Print Case Study</button></div>
</div>

## Source Note / Disclosure

This is a scenario-based, source-derived portfolio artifact—not a client engagement. The source uses fictional Grey Matter and BrainMeld names; AQT is the consistent portfolio wrapper. NIST CSF-style and Technology Operations Governance categories are labeled as interpretive framing where the source did not state a formal mapping. No remediation is presented as complete without evidence.

</article>
