# /search

Search across all connected MCP sources in a single query. Decompose the user's question, run parallel searches, and synthesize results.

## How It Works

┌─────────────────────────────────────────────────────────────────┐
│ SEARCH                                                          │
├─────────────────────────────────────────────────────────────────┤
│ STANDALONE (always works)                                       │
│ ✓ Search across any connected MCP source                        │
│ ✓ Decompose queries into source-specific searches               │
│ ✓ Rank, deduplicate, and synthesize results                     │
│ ✓ Source attribution on every answer                            │
├─────────────────────────────────────────────────────────────────┤
│ SUPERCHARGED (the more tools you connect)                       │
│ + ~~chat: Messages, threads, channels, DMs                      │
│ + ~~email: Emails, attachments, conversations                   │
│ + ~~cloud storage: Docs, sheets, slides, PDFs                   │
│ + ~~knowledge base: Wiki pages, runbooks, articles              │
│ + ~~project tracker: Tasks, issues, epics, milestones           │
│ + ~~CRM: Accounts, contacts, opportunities                      │
└─────────────────────────────────────────────────────────────────┘

## Instructions

### 1. Check Available Sources

Before searching, determine which MCP sources are available from the tool list. Common sources:

- **~~chat** — chat platform tools
- **~~email** — email tools
- **~~cloud storage** — cloud storage tools
- **~~project tracker** — project tracking tools
- **~~CRM** — CRM tools
- **~~knowledge base** — knowledge base tools

If no MCP sources are connected:
```
To search across your tools, you'll need to connect at least one source.
Check your MCP settings to add ~~chat, ~~email, ~~cloud storage, or other tools.
```

### 2. Parse the User's Query

Analyze the search query to understand:

- **Intent**: What is the user looking for? (a decision, a document, a person, a status update, a conversation)
- **Entities**: People, projects, teams, tools mentioned
- **Time constraints**: Recency signals ("this week", "last month", specific dates)
- **Source hints**: References to specific tools ("in ~~chat", "that email", "the doc")
- **Filters**: Extract explicit filters:
  - `from:` — Filter by sender/author
  - `in:` — Filter by channel, folder, or location
  - `after:` — Only results after this date
  - `before:` — Only results before this date
  - `type:` — Filter by content type (message, email, doc, thread, file)

### 3. Decompose into Sub-Queries

For each available source, create a targeted sub-query using that source's native search syntax:

**~~chat:** Use available search and read tools. Translate filters: `from:` → sender, `in:` → channel, dates → time range. Use natural language for semantic search, keywords for exact matches.

**~~email:** Use available email search tools. Map `from:` → sender, dates → time range, `type:` → attachment/subject filters.

**~~cloud storage:** Use file search tools. Translate to file query syntax: name contains, full text, modified date, file type.

**~~project tracker:** Use task search or typeahead tools. Map to text search, assignee, date, and project filters.

**~~CRM:** Use CRM query tools. Search across Account, Contact, Opportunity objects.

**~~knowledge base:** Use semantic search for conceptual questions, keyword search for exact matches.

### 4. Execute Searches in Parallel

Run all sub-queries simultaneously. Do not wait for one source before searching another. For each source:
- Execute the translated query
- Capture results with metadata (timestamps, authors, links, source type)
- Note any failures — do not let one failure block others

### 5. Rank and Deduplicate Results

**Deduplication:** Identify the same information across sources, group related results, prefer the most authoritative or complete version.

**Ranking factors:**
- **Relevance**: How well does the result match the query intent?
- **Freshness**: More recent results rank higher for status/decision queries
- **Authority**: Official docs > wiki > chat for factual questions; conversations > docs for "what did we discuss" queries
- **Completeness**: Results with more context rank higher

### 6. Present Unified Results

Format as a synthesized answer, not a raw list:

**For factual/decision queries:**
```
[Direct answer to the question]

Sources:
- [Source 1: brief description] (~~chat, #channel, date)
- [Source 2: brief description] (~~email, from person, date)
```

**For exploratory queries:**
```
[Synthesized summary combining information from all sources]

Found across:
- ~~chat: X relevant messages in Y channels
- ~~email: X relevant threads
- ~~cloud storage: X related documents
```

**For "find" queries:**
```
[The thing they're looking for, with direct reference]

Also found:
- [Related items from other sources]
```

### 7. Handle Edge Cases

**Ambiguous queries:** Ask one clarifying question before searching.

**No results:** Suggest broader terms, different time range, or checking source connections.

**Partial results:** Present what was found, note which sources failed.

## Tips

1. **Be specific** — "API migration decision from last week" beats "API stuff"
2. **Use filters** — `from:sarah after:2025-01-01` narrows results fast
3. **Connect more sources** — The more tools connected, the more complete the results
