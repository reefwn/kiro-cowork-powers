---
name: "customer-support"
displayName: "Customer Support"
description: "Triage tickets, draft responses, escalate issues, and build your knowledge base. Research customer context and turn resolved issues into self-service content."
keywords: ["triage", "ticket", "support", "customer", "escalate", "escalation", "draft response", "kb article", "knowledge base", "research", "bug report", "feature request", "billing", "SLA", "P1", "P2", "priority", "routing", "helpdesk"]
---

# Onboarding

## Step 1: Check environment

Look for existing support context:
- Support platform configuration
- Knowledge base or wiki
- CRM and customer data sources
- Escalation procedures and SLA definitions

## Step 2: Gather team context

Ask the user:
```
To personalize your support workflows, I'd like to know:
1. Your name and role (e.g., Support Agent, Support Lead)
2. Your team and company name
3. Your support platform (e.g., Intercom, Zendesk, Freshdesk)
4. Your SLA targets (response and resolution times by priority)
5. Your escalation path (who handles L2, engineering, product escalations)
```

Store responses for use across all workflows.

## Step 3: Report readiness

```
Customer support power ready. Available workflows:
- /triage — Categorize, prioritize, and route tickets
- /research — Multi-source research on customer questions
- /draft-response — Draft customer-facing responses
- /escalate — Package escalations for engineering/product/leadership
- /kb-article — Draft knowledge base articles from resolved issues

Skills loaded automatically when relevant:
ticket-triage, customer-research, response-drafting, escalation, knowledge-management
```

# Connectors

This power uses tool categories as placeholders. Any MCP server in that category works.

| Category | Placeholder | Examples |
|----------|-------------|----------|
| Chat | ~~chat | Slack, Microsoft Teams |
| Email | ~~email | Microsoft 365, Gmail |
| Cloud storage | ~~cloud storage | Microsoft 365 |
| Support platform | ~~support platform | Intercom, Zendesk, Freshdesk, HubSpot Service Hub |
| CRM | ~~CRM | HubSpot, Salesforce, Pipedrive |
| Knowledge base | ~~knowledge base | Guru, Notion, Confluence, Help Scout |
| Project tracker | ~~project tracker | Atlassian (Jira/Confluence), Linear, Asana |

# When to Load Steering Files

- Running `/triage` or categorizing/prioritizing a ticket → `triage.md`
- Running `/research` or investigating a customer question → `research.md`
- Running `/draft-response` or writing a customer reply → `draft-response.md`
- Running `/escalate` or packaging an issue for another team → `escalate.md`
- Running `/kb-article` or documenting a resolved issue → `kb-article.md`
- Categorizing tickets, assessing priority, or routing decisions → `ticket-triage.md`
- Researching customer questions or account context → `customer-research.md`
- Drafting any customer-facing communication → `response-drafting.md`
- Assessing whether to escalate or structuring an escalation → `escalation.md`
- Writing or maintaining knowledge base content → `knowledge-management.md`
