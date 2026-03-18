---
name: "human-resources"
displayName: "Human Resources"
description: "Streamline people operations — recruiting, onboarding, performance reviews, compensation analysis, and policy guidance. Maintain compliance and keep your team running smoothly."
keywords: ["draft offer", "onboarding", "performance review", "policy lookup", "comp analysis", "people report", "recruiting", "candidate pipeline", "interview prep", "scorecard", "org planning", "headcount", "reorg", "PTO policy", "benefits", "compensation", "offer letter", "calibration", "self-assessment", "hiring"]
author: "reefwn"
---

# Onboarding

## Step 1: Check environment

Look for existing HR context:
- Employee handbook or policy documents
- Compensation bands or benchmarks
- Org charts or headcount plans
- Existing onboarding checklists

## Step 2: Gather company context

Ask the user:
```
To personalize your HR workflows, I'd like to know:
1. Your name and role
2. Your company name and headquarters location
3. Approximate employee count
4. Benefits overview (health insurance, PTO policy, parental leave)
5. Compensation structure (currency, equity type, vesting schedule)
```

Store responses for use across all workflows.

## Step 3: Report readiness

```
Human Resources power ready. Available workflows:
- /draft-offer — Draft an offer letter with comp details
- /onboarding — Generate onboarding checklist and first-week plan
- /performance-review — Structure performance reviews and calibration
- /policy-lookup — Find and explain company policies
- /comp-analysis — Compensation benchmarking and band analysis
- /people-report — Headcount, attrition, diversity, and org health reports

Skills loaded automatically when relevant:
recruiting-pipeline, interview-prep, org-planning
```

# Connectors

This power uses tool categories as placeholders. Any MCP server in that category works.

| Category | Placeholder | Examples |
|----------|-------------|----------|
| HRIS | ~~HRIS | Workday, BambooHR, Rippling, Gusto |
| ATS | ~~ATS | Greenhouse, Lever, Ashby, Workable |
| Compensation data | ~~compensation data | Pave, Radford, Levels.fyi |
| Chat | ~~chat | Slack, Microsoft Teams |
| Calendar | ~~calendar | Google Calendar, Microsoft 365 |
| Email | ~~email | Gmail, Microsoft 365 |
| Knowledge base | ~~knowledge base | Notion, Confluence, Guru, Coda |

# When to Load Steering Files

- Running `/draft-offer` or assembling a comp package → `draft-offer.md`
- Running `/onboarding` or planning a new hire's first week → `onboarding.md`
- Running `/performance-review` or preparing self-assessments, manager reviews, calibration → `performance-review.md`
- Running `/policy-lookup` or asking about PTO, benefits, expenses, remote work → `policy-lookup.md`
- Running `/comp-analysis` or benchmarking compensation → `comp-analysis.md`
- Running `/people-report` or pulling headcount, attrition, diversity metrics → `people-report.md`
- Discussing recruiting pipeline, candidate status, or hiring funnel → `recruiting-pipeline.md`
- Preparing interview plans, questions, or scorecards → `interview-prep.md`
- Discussing org planning, headcount plans, team structure, or reorgs → `org-planning.md`

# Credits

Ported from [Anthropic's Claude Cowork plugins](https://github.com/anthropics/knowledge-work-plugins) by [@reefwn](https://github.com/reefwn).
