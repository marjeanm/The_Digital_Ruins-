---
title: Cybersecurity Audit & Assessment Playbook
---

<article class="dr-case-study" markdown>
  <header class="dr-case-header dr-case-header--wide-title"><div><p class="dr-kicker">Case Study // Audit &amp; Assurance</p><h1>Cybersecurity Audit &amp; Assessment Playbook</h1><p class="dr-case-deck">A source-backed route from enterprise assessment strategy to evidence, prioritized risks, remediation, and stakeholder reporting.</p></div><div class="dr-case-status"><span class="dr-status dr-status--available">Available</span><span>Two public artifacts</span></div></header>

## Overview

This case study combines an enterprise assessment approach with a cybersecurity key-risk playbook. Together, the documents show how I move from assessment scope and control expectations to a concise risk summary with accountable recommended actions.

The playbook contains **13 scenario-based risks**: three Critical, five High, four Elevated, and one Moderate.

## Scenario

A fictional financial-services environment needs an enterprise security assessment that reaches beyond vulnerability identification. Leadership needs to understand control effectiveness, evidence quality, business impact, remediation ownership, and what should be monitored after the assessment.

> Aegis Quantum Trust is a fictional enterprise environment used across selected portfolio projects to demonstrate governance, risk, compliance, audit, security, and AI governance decision-making in a consistent business context.

## Objective

Create a repeatable, risk-based and compliance-informed assessment method, then translate source observations into a prioritized key-risk playbook that leaders, control owners, and assurance stakeholders can use.

## My Approach

1. Defined assessment scope by domain, system, data type, stakeholder, and control owner.
2. Used a hybrid risk-based and compliance-informed strategy to evaluate enterprise control effectiveness.
3. Connected risk to control expectation, expected evidence, remediation, and continuing monitoring.
4. Reviewed user-domain access, RBAC, zero-trust access, SOP quality, training consistency, and application interactions.
5. Converted technical observations into 13 risk statements with severity, business impact, recommended next step, and responsible area.
6. Preserved evidence limitations and avoided claiming that recommendations had been implemented.

## Frameworks & Methods

- NIST as a flexible enterprise control framework
- OWASP concepts for applications processing sensitive information
- Risk-based assessment scoping
- RBAC, least privilege, MFA, and zero-trust access review
- Evidence planning and control documentation
- Probability-impact severity bands
- Remediation ownership and stakeholder reporting

## Key Findings

- Unsupported SQL Server and Windows Server platforms drive the three Critical risks.
- Default credentials, shared administrative access, and privilege misalignment weaken accountability and increase blast radius.
- Legacy VPN design lacks consistently demonstrated MFA, segmentation, and role-specific access.
- Vendor and contractor connectivity requires business justification, permission review, segmentation, and retained evidence.
- BYOD, broad file-access defaults, weak certificate signatures, and job-role leakage expand the control surface beyond patching alone.

## What This Demonstrates

Audit readiness, enterprise assessment planning, evidence design, risk prioritization, control analysis, remediation thinking, identity and vendor-risk awareness, and technical-to-business communication.

## Artifact Preview

<div class="dr-evidence-grid" aria-label="Audit playbook metrics">
  <div><strong>13</strong><span>Key risks</span></div>
  <div><strong>03</strong><span>Critical</span></div>
  <div><strong>05</strong><span>High</span></div>
  <div><strong>04</strong><span>Elevated</span></div>
</div>

<div class="dr-table-scroll" markdown>

| ID | Band | Risk area | Recommended direction | Owner |
| --- | --- | --- | --- | --- |
| RISK-001 | Critical | Legacy SQL Server platform | Upgrade and migrate to a supported platform | IT / Infrastructure |
| RISK-003 | Critical | HTTP.sys remote-code-execution exposure | Migrate Windows Server and validate web configuration | Systems Engineering |
| RISK-006 | High | Privileged-access misalignment | Separate standard/admin accounts and review Domain Admins | IAM / Security Governance |
| RISK-008 | High | Vendor and contractor remote access | Segment, justify, review, and retain access evidence | Third-Party Risk / IT |
| RISK-010 | Elevated | File-access governance gaps | Centralize controls and reduce default visibility | Data Owners / IAM |

</div>

## View / Download Artifact

<div class="dr-artifact-access">
  <div><p class="dr-card-meta">Public artifacts</p><h3>Assessment method + key-risk playbook</h3><p>Download the methodology document and the corresponding 13-risk executive playbook.</p></div>
  <div class="dr-download-actions"><a class="dr-button dr-button--primary" href="../../assets/artifacts/AQT_Cybersecurity_Audit_Key_Risks_Playbook.docx" download>Download Playbook</a><a class="dr-button" href="../../assets/artifacts/AQT_Enterprise_Assessment_Approach.docx" download>Download Approach</a></div>
</div>

## Source Note / Disclosure

Both documents are scenario-based portfolio artifacts derived from academic/source materials. AQT is fictional. Findings are assessment observations and recommendations, not claims of client work or completed control implementation. Two supplied playbook filenames were byte-for-byte identical; only one public copy is included.

</article>
