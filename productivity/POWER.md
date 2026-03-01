---
name: "productivity"
displayName: "Productivity"
description: "Manage tasks, plan your day, and build up memory of important context about your work. Syncs with your calendar, email, and chat to keep everything organized and on track."
keywords: ["tasks", "todo", "standup", "daily", "sync", "memory", "remember", "action items", "meeting notes", "triage", "organize", "what's on my plate", "remind me", "done with", "waiting on"]
---

# Onboarding

## Step 1: Validate workspace

Check the working directory for:
- `TASKS.md` — task list
- `CLAUDE.md` — working memory
- `memory/` — deep memory directory

## Step 2: Create what's missing

**If `TASKS.md` doesn't exist:** Create it with the standard template:

```markdown
# Tasks

## Active

## Waiting On

## Someday

## Done
```

**If `CLAUDE.md` and `memory/` don't exist:** This is a fresh setup. Create:

```markdown
# Memory

## Me
[Name], [Role] on [Team].

## People
| Who | Role |
|-----|------|
→ Full list: memory/glossary.md, profiles: memory/people/

## Terms
| Term | Meaning |
|------|---------|
→ Full glossary: memory/glossary.md

## Projects
| Name | What |
|------|------|
→ Details: memory/projects/

## Preferences
```

And create the memory directory structure:
- `memory/glossary.md` — full decoder ring
- `memory/people/` — individual profiles
- `memory/projects/` — project details
- `memory/context/` — company, teams, tools

## Step 3: Bootstrap memory (first run only)

Ask the user:
```
Where do you keep your todos or task list? This could be:
- A local file (e.g., TASKS.md, todo.txt)
- An app (e.g. Asana, Linear, Jira, Notion, Todoist)
- A notes file

I'll use your tasks to learn your workplace shorthand.
```

For each task item, analyze for potential shorthand — names, acronyms, project references, internal terms. Decode interactively:

```
Task: "Send PSR to Todd re: Phoenix blockers"

I see some terms I want to make sure I understand:
1. **PSR** - What does this stand for?
2. **Todd** - Who is Todd? (full name, role)
3. **Phoenix** - Is this a project codename? What's it about?
```

Continue through each task, asking only about terms not already decoded.

## Step 4: Optional comprehensive scan

After task list decoding, offer to scan chat, email, calendar, and documents via connected MCP sources. Present findings grouped by confidence:
- **Ready to add** (high confidence) — offer to add directly
- **Needs clarification** — ask the user
- **Low frequency / unclear** — note for later

## Step 5: Report results

```
Productivity system ready:
- Tasks: TASKS.md (X items)
- Memory: X people, X terms, X projects

Use /update to keep things current (add --comprehensive for a deep scan).
```

# Connectors

This power uses tool categories as placeholders. Any MCP server in that category works.

| Category | Placeholder | Examples |
|----------|-------------|----------|
| Chat | ~~chat | Slack, Microsoft Teams, Discord |
| Email | ~~email | Microsoft 365, Gmail |
| Calendar | ~~calendar | Microsoft 365, Google Calendar |
| Knowledge base | ~~knowledge base | Notion, Confluence, Guru, Coda |
| Project tracker | ~~project tracker | Asana, Linear, Jira, monday.com, ClickUp |

# When to Load Steering Files

- Adding, completing, or triaging tasks → `task-management.md`
- Remembering people, terms, projects, or decoding shorthand → `memory-management.md`
- Running `/start` to initialize the system → `start-workflow.md`
- Running `/update` to sync and triage → `update-workflow.md`
