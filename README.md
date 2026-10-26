# Microsoft 365 AI Internal Audit Toolkit

A checklist for a Microsoft 365 administrator to review AI-related configuration in their own tenant: Copilot, agents, Copilot Studio, third-party AI apps, and the data, identity and logging controls around them. Each check is mapped to NIST AI RMF 1.0, ISO/IEC 42001:2023 and the EU AI Act.

It's written for someone who already knows the organisation's environment and policies. The admin judges each setting against what the organisation has decided, so the sheet doesn't prescribe expected values. The result is one piece of the AI governance picture: what's configured today. It isn't the whole picture (see [What this does not cover](#what-this-does-not-cover)).

**File:** [M365-AI-Config-Snapshot.xlsx](M365-AI-Config-Snapshot.xlsx), one sheet with 70 checks.

| Area | Checks |
|---|---|
| Copilot & Agents | 10 |
| Teams & Meetings | 3 |
| Copilot Studio (Power Platform) | 8 |
| Data Protection (Purview) | 9 |
| Endpoints (Intune / Defender) | 5 |
| SharePoint & OneDrive | 11 |
| Identity & Access (Entra) | 8 |
| App Permissions | 6 |
| Logging & Monitoring | 10 |

## Columns

| Column | Use |
|---|---|
| Ref, Area, Control | What to check |
| Result | Pass / Fail / Partial / Not applicable (drop-down) |
| Observed value / notes | What is configured, why it differs from the control if it does, and a screenshot or export reference |
| Severity | Critical / High / Medium / Low |
| NIST AI RMF, ISO/IEC 42001, EU AI Act | Framework mapping ("—" = no direct mapping) |

## How to use

1. For each row, open the relevant admin portal and look at the setting.
2. Mark **Pass** if it meets the control and your organisation's policy. Mark **Fail** if it doesn't. Mark **Partial** if it's in place for some users, sites or environments but not all, or is in test / report-only mode. Mark **Not applicable** if the feature isn't used (for example, no Copilot Studio). Give the reason in the notes.
3. Record what you saw in **Observed value / notes**, including any documented exception the organisation has approved.
4. Keep a dated screenshot or export for anything you may need to show later.
5. Repeat periodically, and after major Copilot or agent changes, to track drift.

## Access needed

Read access is enough. Nothing in the checklist requires changing a setting.

| Portal / area | Rows | Role |
|---|---|---|
| Microsoft 365 admin center (Copilot settings, agents, connectors, licences, org settings) | CA | Global Reader; some Copilot and agent pages may need AI Administrator |
| Teams admin center | CA, TM | Global Reader or Teams Administrator |
| Power Platform admin center | CS | Power Platform Administrator (Global Reader gives read access to most pages) |
| Microsoft Purview: DLP, labels, retention, DSPM for AI, device onboarding | DP, EP, LM | Global Reader or Compliance Administrator |
| Microsoft Purview: Audit | LM | Audit Reader / View-Only Audit Logs |
| Microsoft Purview: Compliance Manager | LM | Compliance Manager Reader |
| Microsoft Purview: Communication Compliance, Insider Risk Management | LM | Communication Compliance Viewer; Insider Risk Management Auditors |
| Microsoft Purview: eDiscovery | LM | eDiscovery Manager |
| Microsoft Intune admin center | EP | Global Reader or Intune Read Only Operator |
| Microsoft Defender portal: Cloud Apps, app governance, advanced features | EP, AP | Security Reader |
| SharePoint admin center | SP | SharePoint Administrator (there is no read-only SharePoint admin role) |
| Microsoft Entra admin center: Conditional Access, PIM, access reviews, consent, guest settings | IA, AP | Global Reader or Security Reader |
| SIEM (e.g. Microsoft Sentinel) | LM | Microsoft Sentinel Reader or the SIEM's equivalent |

## What this does not cover

This is a **configuration** check at a point in time. It's one input to AI governance. It doesn't cover:

- **Governance and process controls.** These make up most of the three frameworks:
  - AI policy and acceptable use
  - the governance body and roles
  - AI inventory completeness
  - risk and impact assessments (including DPIAs and fundamental rights impact assessments)
  - EU AI Act risk classification, operator role and prohibited-practice screening
  - vendor due diligence and contracts
  - AI literacy training
  - human oversight
  - transparency notices to users and affected people
  - change approval and go / no-go decisions
  - post-deployment monitoring plans
  - incident response and regulatory reporting
  - internal audit and management review
- **Whether settings stayed in place over time.** That needs change history and periodic re-checks.
- **Whether AI output is accurate, fair or safe.** The checklist covers guardrails, not the quality of what Copilot or agents produce.
- **Custom AI built on Azure** (Azure OpenAI, Microsoft Foundry, Azure Machine Learning) and the development lifecycle (evaluation, red teaming, technical documentation).
- **Individual agent design.** Each Copilot Studio or declarative agent's instructions, knowledge sources and actions need their own review.
- **Non-Microsoft AI** used outside the tenant's visibility.
- **Independent assurance.** An admin reviewing their own tenant is a self-assessment. Internal audit or a third party may still need to verify it.

Framework coverage reflects this: the 70 checks map to 23 of 72 NIST AI RMF subcategories, 21 of 51 ISO/IEC 42001 clauses and Annex A controls, and 7 of 33 EU AI Act obligations. **A full set of Pass results isn't framework compliance, ISO/IEC 42001 certification, or a legal opinion on the EU AI Act.**

## Notes

- Microsoft renames and moves admin portal menus often. Search the portal for the feature name if a setting isn't where you expect.
- Framework requirements are paraphrased and mappings are indicative. No ISO text is reproduced. EU AI Act references reflect Regulation (EU) 2026/1744.
- Not affiliated with or endorsed by Microsoft, NIST, ISO/IEC or the European Commission.

## About the author

Created by Adam Buenz, AIGP. The checks and framework mappings reflect the author's professional judgement and are shared to help administrators and governance teams. They are not legal advice.

## Licence

[CC BY 4.0](LICENSE)
