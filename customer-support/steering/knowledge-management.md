# Knowledge Management

Expert at creating, organizing, and maintaining support knowledge base content. Write articles that are searchable, scannable, and solve customer problems on the first read. Every good KB article reduces future ticket volume.

## Article Structure

Every KB article should include:
1. **Title**: Clear, searchable, describes the outcome or problem
2. **Overview**: 1-2 sentences explaining what this article covers
3. **Body**: Structured content appropriate to the article type
4. **Related articles**: Links to companion content
5. **Metadata**: Category, tags, audience, last updated date

## Writing for Searchability

### Title Best Practices
- "How to configure SSO with Okta" (not "SSO Setup")
- "Fix: Dashboard shows blank page" (not "Dashboard Issue")
- "Error: 'Connection refused' when importing data" (not "Import Problems")

### Keyword Optimization
- Include exact error messages (customers copy-paste into search)
- Use customer language, not internal terminology
- Include common synonyms ("delete/remove", "export/download")
- Tag with product areas matching how customers think

### Opening Sentence Formula
- **How-to**: "This guide shows you how to [accomplish X]."
- **Troubleshooting**: "If you're seeing [symptom], this article explains how to fix it."
- **FAQ**: "[Question in customer's words]? Here's the answer."
- **Known issue**: "Some users are experiencing [symptom]. Here's what we know."

## Article Types

### How-to
Prerequisites → Numbered steps → Verify it worked → Common issues

### Troubleshooting
Symptoms → Cause → Solution (multiple options, most likely first) → Prevention → Still having issues?

### FAQ
Direct answer (first sentence) → Details if needed → Related questions

### Known Issue
Status (Investigating/Workaround Available/Fix In Progress/Resolved) → Affected → Symptoms → Workaround → Fix timeline → Updates log

## Review and Maintenance Cadence

| Activity | Frequency |
|----------|-----------|
| New article review | Before publishing |
| Accuracy audit | Quarterly (top-traffic articles) |
| Stale content check | Monthly (flag articles not updated in 6+ months) |
| Known issue updates | Weekly |
| Analytics review | Monthly (low helpfulness, high bounce) |
| Gap analysis | Quarterly (top ticket topics without KB articles) |

## Article Lifecycle

1. **Draft** → 2. **Published** → 3. **Needs update** → 4. **Archived** → 5. **Retired**

### Update vs. Create New
- **Update**: Product changed, mostly right but missing detail, better workaround found
- **Create new**: New feature/product area, resolved ticket reveals gap, existing article covers too many topics, different audience needs

## Formatting Rules

- Use headers (H2, H3) for scannable sections
- Numbered lists for sequential steps
- Bullet lists for non-sequential items
- Bold for UI elements and key terms
- Code blocks for commands, API calls, error messages
- Tables for comparisons and reference data
- Keep paragraphs to 2-4 sentences max
