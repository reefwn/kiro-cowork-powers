# Search Strategy

Query decomposition and multi-source search orchestration. Breaks natural language questions into targeted searches per source, translates queries into source-specific syntax, ranks results by relevance, and handles ambiguity and fallback strategies.

## Query Decomposition

### Step 1: Identify Query Type

| Query Type | Example | Strategy |
|-----------|---------|----------|
| **Decision** | "What did we decide about X?" | Prioritize conversations (~~chat, email), look for conclusion signals |
| **Status** | "What's the status of Project Y?" | Prioritize recent activity, task trackers, status updates |
| **Document** | "Where's the spec for Z?" | Prioritize Drive, wiki, shared docs |
| **Person** | "Who's working on X?" | Search task assignments, message authors, doc collaborators |
| **Factual** | "What's our policy on X?" | Prioritize wiki, official docs, then confirmatory conversations |
| **Temporal** | "When did X happen?" | Search with broad date range, look for timestamps |
| **Exploratory** | "What do we know about X?" | Broad search across all sources, synthesize |

### Step 2: Extract Search Components

From the query, extract:
- **Keywords**: Core terms that must appear in results
- **Entities**: People, projects, teams, tools
- **Intent signals**: Decision words, status words, temporal markers
- **Constraints**: Time ranges, source hints, author filters
- **Negations**: Things to exclude

### Step 3: Generate Sub-Queries Per Source

**Prefer semantic search** for: conceptual questions, unknown exact keywords, exploratory queries.

**Prefer keyword search** for: known terms, project names, acronyms, exact phrases, filter-heavy queries.

**Generate multiple query variants** when the topic might be referred to differently:
```
User: "Kubernetes setup"
Queries: "Kubernetes", "k8s", "cluster", "container orchestration"
```

## Source-Specific Query Translation

### ~~chat

| Enterprise filter | ~~chat syntax |
|------------------|--------------|
| `from:sarah` | `from:sarah` or `from:<@USERID>` |
| `in:engineering` | `in:engineering` |
| `after:2025-01-01` | `after:2025-01-01` |
| `before:2025-02-01` | `before:2025-02-01` |
| `type:thread` | `is:thread` |
| `type:file` | `has:file` |

### ~~knowledge base (Wiki)

Semantic search for conceptual queries. Keyword search for exact terms and phrases.

### ~~project tracker

Map to: text search, workspace, completed status, assignee, modified date, resource subtype.

## Result Ranking

### Relevance Scoring

| Factor | Weight (Decision) | Weight (Status) | Weight (Document) | Weight (Factual) |
|--------|-------------------|------------------|--------------------|-------------------|
| Keyword match | 0.3 | 0.2 | 0.4 | 0.3 |
| Freshness | 0.3 | 0.4 | 0.2 | 0.1 |
| Authority | 0.2 | 0.1 | 0.3 | 0.4 |
| Completeness | 0.2 | 0.3 | 0.1 | 0.2 |

### Authority Hierarchy

**Factual/policy:** Wiki/Official docs > Shared documents > Email announcements > Chat messages

**Decision:** Meeting notes > Thread conclusions > Email confirmations > Chat messages

**Status:** Task tracker > Recent chat > Status docs > Email updates

## Handling Ambiguity

Prefer asking one focused clarifying question over guessing. Only ask when genuinely distinct interpretations would produce very different results. Do NOT ask when the query is clear enough to produce useful results.

## Fallback Strategies

When initial queries return too few results, remove constraints in this order:
1. Date filters (search all time)
2. Source/location filters
3. Less important keywords
4. Keep only core entity/topic terms

## Parallel Execution

Always execute searches across sources in parallel, never sequentially:
```
[User query] → decompose → [parallel source queries] → [Merge + Rank + Deduplicate] → [Synthesized answer]
```
