# Start Workflow

Initialize the task and memory systems.

## Instructions

### 1. Check What Exists

Check the working directory for:
- `TASKS.md` — task list
- `CLAUDE.md` — working memory
- `memory/` — deep memory directory

### 2. Create What's Missing

**If `TASKS.md` doesn't exist:** Create it with the standard template (see task-management steering).

**If `CLAUDE.md` and `memory/` don't exist:** This is a fresh setup — begin the memory bootstrap workflow (see below).

### 3. Orient the User

If everything was already initialized:
```
Your tasks and memory are both loaded.
- Use /update to sync tasks and check memory
- Use /update --comprehensive for a deep scan of all activity
```

If memory hasn't been bootstrapped yet, continue to step 4.

### 4. Bootstrap Memory (First Run Only)

Only do this if `CLAUDE.md` and `memory/` don't exist yet.

The best source of workplace language is the user's actual task list. Real tasks = real shorthand.

**Ask the user:**
```
Where do you keep your todos or task list? This could be:
- A local file (e.g., TASKS.md, todo.txt)
- An app (e.g. Asana, Linear, Jira, Notion, Todoist)
- A notes file

I'll use your tasks to learn your workplace shorthand.
```

**Once you have access to the task list:**

For each task item, analyze it for potential shorthand:
- Names that might be nicknames
- Acronyms or abbreviations
- Project references or codenames
- Internal terms or jargon

**For each item, decode it interactively:**

```
Task: "Send PSR to Todd re: Phoenix blockers"

I see some terms I want to make sure I understand:

1. **PSR** - What does this stand for?
2. **Todd** - Who is Todd? (full name, role)
3. **Phoenix** - Is this a project codename? What's it about?
```

Continue through each task, asking only about terms you haven't already decoded.

### 5. Optional Comprehensive Scan

After task list decoding, offer:
```
Do you want me to do a comprehensive scan of your messages, emails, and documents?
This takes longer but builds much richer context about the people, projects, and terms in your work.

Or we can stick with what we have and add context later.
```

**If they choose comprehensive scan:**

Gather data from available MCP sources:
- **~~chat:** Recent messages, channels, DMs
- **~~email:** Sent messages, recipients
- **~~knowledge base:** Recent docs, collaborators
- **~~calendar:** Meetings, attendees

Build a braindump of people, projects, and terms found. Present findings grouped by confidence:
- **Ready to add** (high confidence) — offer to add directly
- **Needs clarification** — ask the user
- **Low frequency / unclear** — note for later

### 6. Write Memory Files

From everything gathered, create:

**CLAUDE.md** (working memory, ~50-80 lines) with sections: Me, People, Terms, Projects, Preferences.

**memory/** directory:
- `memory/glossary.md` — full decoder ring (acronyms, terms, nicknames, codenames)
- `memory/people/{name}.md` — individual profiles
- `memory/projects/{name}.md` — project details
- `memory/context/company.md` — teams, tools, processes

### 7. Report Results

```
Productivity system ready:
- Tasks: TASKS.md (X items)
- Memory: X people, X terms, X projects

Use /update to keep things current (add --comprehensive for a deep scan).
```

## Notes

- If memory is already initialized, just report current state
- Nicknames are critical — always capture how people are actually referred to
- If a source isn't available, skip it and note the gap
- Memory grows organically through natural conversation after bootstrap
