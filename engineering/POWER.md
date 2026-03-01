---
name: "engineering"
displayName: "Engineering"
description: "Streamline engineering workflows — standups, code review, architecture decisions, incident response, and technical documentation. Works with your existing tools or standalone."
keywords: ["standup", "code review", "review", "debug", "architecture", "incident", "deploy", "deploy checklist", "ADR", "postmortem", "tech debt", "testing strategy", "system design", "documentation", "runbook", "code quality", "refactor", "production down", "outage", "SEV1"]
---

# Onboarding

## Step 1: Check environment

Look for existing engineering context:
- Project source code and repository
- CI/CD configuration
- Monitoring and alerting setup
- Existing ADRs or design docs

## Step 2: Gather team context

Ask the user:
```
To personalize your engineering workflows, I'd like to know:
1. Your name and role
2. Your team name and company
3. Your tech stack (languages, frameworks, databases, cloud)
4. Your default branch name (e.g., main, master)
5. Your deploy process (e.g., canary, blue-green, rolling)
```

Store responses for use across all workflows.

## Step 3: Report readiness

```
Engineering power ready. Available workflows:
- /standup — Generate standup updates
- /review — Code review
- /debug — Structured debugging
- /architecture — Architecture decisions (ADR)
- /incident — Incident response
- /deploy-checklist — Pre-deployment verification

Skills loaded automatically when relevant:
code-review, incident-response, system-design, tech-debt, testing-strategy, documentation
```

# Connectors

This power uses tool categories as placeholders. Any MCP server in that category works.

| Category | Placeholder | Examples |
|----------|-------------|----------|
| Chat | ~~chat | Slack, Microsoft Teams |
| Source control | ~~source control | GitHub, GitLab, Bitbucket |
| Project tracker | ~~project tracker | Linear, Jira, Asana |
| Knowledge base | ~~knowledge base | Notion, Confluence, Guru, Coda |
| Monitoring | ~~monitoring | Datadog, New Relic, Grafana, Splunk |
| Incident management | ~~incident management | PagerDuty, Opsgenie, Incident.io |
| CI/CD | ~~CI/CD | CircleCI, GitHub Actions, Jenkins, BuildKite |

# When to Load Steering Files

- Running `/standup` or asking about daily updates → `standup.md`
- Running `/review` or asking to review code, PRs, diffs → `review.md`
- Running `/debug` or describing a bug to investigate → `debug.md`
- Running `/architecture` or asking about system design decisions → `architecture.md`
- Running `/incident` or reporting a production issue → `incident.md`
- Running `/deploy-checklist` or preparing to deploy → `deploy-checklist.md`
- Discussing code quality, bugs, security, or maintainability → `code-review.md`
- Discussing production incidents, severity, or postmortems → `incident-response.md`
- Designing systems, APIs, or service architecture → `system-design.md`
- Discussing technical debt, refactoring, or code health → `tech-debt.md`
- Discussing test strategy, coverage, or test plans → `testing-strategy.md`
- Writing or maintaining technical documentation → `documentation.md`
