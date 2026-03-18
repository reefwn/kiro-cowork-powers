---
name: "legal"
displayName: "Legal"
description: "Contract review, NDA triage, compliance workflows, legal briefings, and templated responses. Configurable to your organization's playbook and risk tolerances."
keywords: ["contract", "review", "nda", "triage", "compliance", "gdpr", "ccpa", "dpa", "vendor", "agreement", "redline", "playbook", "risk assessment", "briefing", "legal hold", "discovery", "subpoena", "data subject request", "signature", "e-sign"]
author: "reefwn"
---

# Onboarding

## Step 1: Check environment

Look for existing legal context:
- Contract playbook configuration (e.g., `legal.local.md`)
- CLM, CRM, or document management connections
- E-signature platform setup
- Escalation procedures and approval workflows

## Step 2: Gather team context

Ask the user:
```
To personalize your legal workflows, I'd like to know:
1. Your name and role (e.g., Commercial Counsel, Product Counsel, Privacy/Compliance)
2. Your team and company name
3. Your preferred governing law jurisdiction
4. Your standard liability cap position (e.g., 12 months of fees)
5. Your escalation path (who handles senior review, outside counsel engagement)
```

Store responses for use across all workflows.

## Step 3: Report readiness

```
Legal power ready. Available workflows:
- /review-contract — Review a contract against your playbook
- /triage-nda — Rapid NDA pre-screening and classification
- /vendor-check — Vendor agreement status across connected systems
- /brief — Daily, topic, or incident briefings
- /legal-response — Generate templated responses for common inquiries
- /compliance-check — Compliance review for proposed actions
- /signature-request — Prepare and route documents for e-signature

Skills loaded automatically when relevant:
review-contract, triage-nda, compliance-check, legal-response, legal-risk-assessment, meeting-briefing, vendor-check, brief, signature-request
```

# Connectors

This power uses tool categories as placeholders. Any MCP server in that category works.

| Category | Placeholder | Examples |
|----------|-------------|----------|
| Calendar | ~~calendar | Google Calendar, Microsoft 365 |
| Chat | ~~chat | Slack, Microsoft Teams |
| Cloud storage | ~~cloud storage | Box, Egnyte, Dropbox, SharePoint, Google Drive |
| CLM | ~~CLM | Ironclad, Agiloft |
| CRM | ~~CRM | Salesforce, HubSpot |
| Email | ~~email | Gmail, Microsoft 365 |
| E-signature | ~~e-signature | DocuSign, Adobe Sign |
| Office suite | ~~office suite | Microsoft 365, Google Workspace |
| Project tracker | ~~project tracker | Atlassian (Jira/Confluence), Linear, Asana |

# When to Load Steering Files

- Running `/review-contract` or reviewing a contract → `review-contract.md`
- Running `/triage-nda` or screening an NDA → `triage-nda.md`
- Running `/vendor-check` or checking vendor agreements → `vendor-check.md`
- Running `/brief` or preparing a briefing → `brief.md`
- Running `/legal-response` or drafting a templated response → `legal-response.md`
- Running `/compliance-check` or assessing regulatory compliance → `compliance-check.md`
- Running `/signature-request` or routing for e-signature → `signature-request.md`
- Assessing legal risk or classifying risk severity → `legal-risk-assessment.md`
- Preparing for a meeting with legal relevance → `meeting-briefing.md`

# Credits

Ported from [Anthropic's Claude Cowork plugins](https://github.com/anthropics/knowledge-work-plugins) by [@reefwn](https://github.com/reefwn).
