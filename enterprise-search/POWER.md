---
name: "enterprise-search"
displayName: "Enterprise Search"
description: "Search across all of your company's tools in one place. Find anything across email, chat, documents, and wikis without switching between apps."
keywords: ["search", "find", "digest", "lookup", "where is", "what did we decide", "find that doc", "who works on", "what's the status", "enterprise search", "cross-tool search", "knowledge base", "catch up", "daily digest", "weekly digest", "summary"]
author: "reefwn"
---

# Onboarding

## Step 1: Check environment

Look for connected MCP sources:
- Chat (Slack, Microsoft Teams)
- Email (Gmail, Microsoft 365)
- Cloud storage (Microsoft 365, Dropbox)
- Knowledge base (Notion, Confluence, Guru)
- Project tracker (Jira, Asana, Linear)
- CRM (Salesforce, HubSpot)

## Step 2: Gather user context

Ask the user:
```
To personalize your enterprise search, I'd like to know:
1. Your name and role
2. Your team and company
3. Which tools your team uses for chat, email, docs, and project tracking
4. Any key projects or topics you frequently search for
```

Store responses for use across all workflows.

## Step 3: Report readiness

```
Enterprise Search power ready. Available workflows:
- /search — Search across all connected sources in one query
- /digest — Generate a daily or weekly digest of activity

Skills loaded automatically when relevant:
search-strategy, source-management, knowledge-synthesis
```

# Connectors

This power uses tool categories as placeholders. Any MCP server in that category works.

| Category | Placeholder | Examples |
|----------|-------------|----------|
| Chat | ~~chat | Slack, Microsoft Teams, Discord |
| Email | ~~email | Gmail, Microsoft 365 |
| Cloud storage | ~~cloud storage | Microsoft 365, Dropbox, Google Drive |
| Knowledge base | ~~knowledge base | Notion, Confluence, Guru, Slite |
| Project tracker | ~~project tracker | Jira, Asana, Linear, monday.com |
| CRM | ~~CRM | Salesforce, HubSpot |
| Office suite | ~~office suite | Microsoft 365, Google Workspace |
| Calendar | ~~calendar | Google Calendar |

# When to Load Steering Files

- Running `/search` or asking to find something across tools → `search.md`
- Running `/digest` or asking for a daily/weekly summary → `digest.md`
- Decomposing queries or translating to source-specific syntax → `search-strategy.md`
- Checking which sources are connected or guiding connections → `source-management.md`
- Combining results from multiple sources into coherent answers → `knowledge-synthesis.md`

# Credits

Ported from [Anthropic's Claude Cowork plugins](https://github.com/anthropics/knowledge-work-plugins) by [@reefwn](https://github.com/reefwn).
