# Knowledge Synthesis

Combines search results from multiple sources into coherent, deduplicated answers with source attribution. Handles confidence scoring based on freshness and authority, and summarizes large result sets effectively.

## Cross-Source Deduplication

**Signals that results are about the same thing:**
- Same or very similar text content
- Same author/sender
- Timestamps within a short window
- References to the same entity
- One source references another ("as discussed in ~~chat", "per the email")

**Merge strategy:** Combine into a single narrative item, cite all sources, use the most complete version as primary, add unique details from each source.

**Deduplication priority:** Most complete version → Most authoritative source → Most recent version.

**Do NOT deduplicate when:** Different conclusions, different viewpoints, meaningful evolution between sources, or different time periods.

## Citation and Source Attribution

Every claim must be attributable to a source.

**Inline attribution:**
```
Sarah confirmed the REST approach in her email on Wednesday.
The design doc was updated to reflect this (~~cloud storage: "API Design Doc v3").
```

**Source list at the end:**
```
Sources:
- ~~chat: #engineering discussion (Jan 14) — initial decision thread
- ~~email: "API Decision" from Sarah Chen (Jan 15) — formal confirmation
- ~~cloud storage: "API Design Doc v3" last modified Jan 15 — updated specification
```

**Rules:** Always name the source type, include specific location (channel, folder), date, author when relevant, and document/thread titles.

## Confidence Levels

### Freshness

| Recency | Confidence impact |
|---------|------------------|
| Today / yesterday | High confidence for current state |
| This week | Good confidence |
| This month | Moderate — things may have changed |
| Older than a month | Lower — flag as potentially outdated |

### Authority

| Source type | Authority level |
|-------------|----------------|
| Official wiki / knowledge base | Highest |
| Shared documents (final versions) | High |
| Email announcements | High |
| Meeting notes | Moderate-high |
| Chat messages (thread conclusions) | Moderate |
| Chat messages (mid-thread) | Lower |
| Draft documents | Low |

### Expressing Confidence

**High** (multiple fresh, authoritative sources agree): Direct statement.

**Moderate** (single source or somewhat dated): "Based on the discussion in #engineering last month, the team was leaning toward..."

**Low** (old data, informal source, conflicting signals): "I found a reference from three months ago, but couldn't find a formal decision document. The information may be outdated."

### Conflicting Information

Always surface conflicts rather than silently picking one version:
```
I found conflicting information:
- The ~~chat discussion on Jan 10 suggested GraphQL
- But Sarah's email on Jan 15 confirmed REST
- The design doc (updated Jan 15) reflects REST

The most recent sources indicate REST was the final decision.
```

## Summarization Strategies

**Small (1-5 results):** Present each result with context. No summarization needed.

**Medium (5-15 results):** Group by theme and summarize each group. Show top 3-5 sources.

**Large (15+ results):** High-level synthesis with key findings, top sources, and offer to drill down.

## Synthesis Workflow

```
[Raw results] → Deduplicate → Cluster by theme → Rank → Assess confidence → Synthesize narrative → Format for result count
```

## Anti-Patterns

**Do not:** List results source by source, include irrelevant keyword matches, bury the answer under methodology, present conflicting info without flagging, omit attribution, present uncertain info with high confidence.

**Do:** Lead with the answer, group by topic not source, flag confidence levels, surface conflicts, attribute all claims, offer to go deeper on large result sets.
