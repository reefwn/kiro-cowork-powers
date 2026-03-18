# /digest

Scan recent activity across all connected sources and generate a structured digest highlighting what matters.

## How It Works

┌─────────────────────────────────────────────────────────────────┐
│ DIGEST                                                          │
├─────────────────────────────────────────────────────────────────┤
│ STANDALONE (always works)                                       │
│ ✓ Daily or weekly activity summary                              │
│ ✓ Action items, decisions, mentions, doc updates                │
│ ✓ Grouped by topic/project, not by source                       │
├─────────────────────────────────────────────────────────────────┤
│ SUPERCHARGED (the more tools you connect)                       │
│ + ~~chat: Mentions, threads, channel activity                   │
│ + ~~email: Inbox, replies, action items                         │
│ + ~~cloud storage: Modified docs, new shares                    │
│ + ~~project tracker: Task updates, completions                  │
│ + ~~CRM: Opportunity changes, account activity                  │
│ + ~~knowledge base: Updated wiki pages                          │
└─────────────────────────────────────────────────────────────────┘

## Instructions

### 1. Parse Flags

Determine the time window:
- `--daily` — Last 24 hours (default if no flag specified)
- `--weekly` — Last 7 days
- `--since <date>` — Custom range (e.g., `--since Monday`, `--since 2025-01-20`)

### 2. Check Available Sources

Identify connected MCP sources:
- **~~chat** — channels, DMs, mentions
- **~~email** — inbox, sent, threads
- **~~cloud storage** — recently modified docs
- **~~project tracker** — tasks assigned, completed, commented on
- **~~CRM** — opportunity updates, account activity
- **~~knowledge base** — recently updated wiki pages

If no sources are connected, guide the user to add at least one.

### 3. Gather Activity from Each Source

**~~chat:** Messages mentioning the user, channel activity, threads participated in.

**~~email:** Recent inbox messages, threads with new replies, emails with action items.

**~~cloud storage:** Documents recently modified or shared, new comments on user's docs.

**~~project tracker:** Tasks assigned (new or updated), tasks completed by others, comments on involved tasks.

**~~CRM:** Opportunity stage changes, new activities on owned accounts.

**~~knowledge base:** Recently updated documents in relevant collections.

### 4. Identify Key Items

From all gathered activity, extract and categorize:

- **Action Items**: Direct requests, assigned tasks, questions awaiting response, review requests
- **Decisions**: Conclusions in threads/emails, approvals/rejections, direction changes
- **Mentions**: Times the user was referenced, discussions about user's projects
- **Updates**: Status changes, document updates, completed items

### 5. Group by Topic

Organize by topic/project, not by source. Merge related activity across sources:

```
## Project Aurora
- ~~chat: Design review thread concluded — team chose Option B (#design, Tuesday)
- ~~email: Sarah sent updated spec incorporating feedback (Wednesday)
- ~~cloud storage: "Aurora API Spec v3" updated by Sarah (Wednesday)
- ~~project tracker: 3 tasks moved to In Progress, 2 completed
```

### 6. Format the Digest

```
# [Daily/Weekly] Digest — [Date or Date Range]

Sources scanned: ~~chat, ~~email, ~~cloud storage, [others]

## Action Items (X items)
- [ ] [Action item 1] — from [person], [source] ([date])
- [ ] [Action item 2] — from [person], [source] ([date])

## Decisions Made
- [Decision 1] — [context] ([source], [date])

## [Topic/Project Group 1]
[Activity summary with source attribution]

## Mentions
- [Mention context] — [source] ([date])

## Documents Updated
- [Doc name] — [who modified, what changed] ([date])
```

### 7. Handle Unavailable Sources

If any source fails:
```
Note: Could not reach [source name] for this digest.
The following sources were included: [list of successful sources].
```

Do not let one failed source prevent the digest from being generated.

### 8. Summary Stats

End with:
```
---
[X] action items · [Y] decisions · [Z] mentions · [W] doc updates
Across [N] sources · Covering [time range]
```

## Notes

- Default to `--daily` if no flag is specified
- Group by topic/project, not by source
- Action items should always be listed first
- Deduplicate cross-source activity (same decision in ~~chat and email = one entry)
- For weekly digests, prioritize significance over completeness
