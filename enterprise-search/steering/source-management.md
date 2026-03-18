# Source Management

Manages connected MCP sources for enterprise search. Detects available sources, guides users to connect new ones, handles source priority ordering, and manages rate limiting awareness.

## Checking Available Sources

Determine which MCP sources are connected by checking available tools:

| Source | Key capabilities |
|--------|-----------------|
| **~~chat** | Search messages, read channels and threads |
| **~~email** | Search messages, read individual emails |
| **~~cloud storage** | Search files, fetch document contents |
| **~~project tracker** | Search tasks, typeahead search |
| **~~CRM** | Query records (accounts, contacts, opportunities) |
| **~~knowledge base** | Semantic search, keyword search |

If a tool prefix is available, the source is connected and searchable.

## Guiding Users to Connect Sources

When a user searches but has few or no sources connected:
```
You currently have [N] source(s) connected: [list].

To expand your search, you can connect additional sources in your MCP settings:
- ~~chat — messages, threads, channels
- ~~email — emails, conversations, attachments
- ~~cloud storage — docs, sheets, slides
- ~~project tracker — tasks, projects, milestones
- ~~CRM — accounts, contacts, opportunities
- ~~knowledge base — wiki pages, knowledge base articles
```

## Source Priority Ordering

Different query types benefit from searching certain sources first. Use these priorities to weight results, not to skip sources:

**Decision queries:** ~~chat → ~~email → ~~cloud storage → Wiki → Task tracker

**Status queries:** Task tracker → ~~chat → ~~cloud storage → ~~email → Wiki

**Document queries:** ~~cloud storage → Wiki/~~knowledge base → ~~email → ~~chat → Task tracker

**People queries:** ~~chat → Task tracker → ~~cloud storage → ~~CRM → ~~email

**Factual/Policy queries:** Wiki/~~knowledge base → ~~cloud storage → ~~email → ~~chat

**Default (general):** ~~chat → ~~email → ~~cloud storage → Wiki/~~knowledge base → Task tracker → CRM

## Rate Limiting Awareness

### Detection
Rate limit responses: HTTP 429, "rate limit", "too many requests", "quota exceeded".

### Handling
1. Do not retry immediately — respect the limit
2. Continue with other sources — do not block the entire search
3. Inform the user which source is limited and suggest retrying later
4. For digests, note which time range was covered before the limit hit

### Prevention
- Avoid unnecessary API calls
- Use targeted queries over broad scans
- Batch requests where the API supports it
- Don't re-run the same query immediately

## Source Health

Track source availability during a session:
```
Source Status:
~~chat:            ✓ Available
~~email:           ✓ Available
~~cloud storage:   ✓ Available
~~project tracker: ✗ Not connected
~~CRM:             ✗ Not connected
~~knowledge base:  ⚠ Rate limited (retry in 2 min)
```

When reporting search results, include which sources were searched so the user knows the scope of the answer.

## Adding Custom Sources

The enterprise search power works with any MCP-connected source. New MCP servers can be added to the `mcp.json` configuration. The search and digest commands will automatically detect and include new sources based on available tools.
