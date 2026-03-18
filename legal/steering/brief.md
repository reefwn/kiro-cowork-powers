# /brief

Generate contextual briefings for legal work — daily summary, topic research, or incident response.

## Usage

```
/brief daily          # Morning brief of legal-relevant items
/brief topic [query]  # Research brief on a specific legal question
/brief incident       # Rapid brief on a developing situation
```

If no mode specified, ask the user which type they need.

## Modes

### Daily Brief

A morning summary of everything a legal team member needs to start their day.

Scan each connected source:
- **Email**: Contract requests, compliance questions, counterparty responses, outside counsel communications
- **Calendar**: Meetings needing legal prep, upcoming deadlines this week
- **Chat**: Overnight messages in legal channels, direct requests, escalations
- **CLM**: Contracts awaiting review/signature, approaching expirations (30 days)
- **CRM**: Deals moving to stages requiring legal involvement

```
## Daily Legal Brief — [Date]

### Urgent / Action Required
[Items needing immediate attention]

### Contract Pipeline
- **Awaiting Your Review**: [count and list]
- **Pending Counterparty Response**: [count and list]
- **Approaching Deadlines**: [items due this week]

### New Requests
[Contract review, NDA, compliance questions received since last brief]

### Calendar Today
[Meetings with legal relevance and prep needed]

### Team Activity
[Key messages or updates from legal team channels]

### This Week's Deadlines
[Upcoming deadlines and filing dates]

### Sources Not Available
[Any sources not connected or returning errors]
```

### Topic Brief

Research and brief on a specific legal question across available sources.

1. Accept the topic query
2. Search across documents, email, chat, CLM for relevant materials
3. Synthesize findings

```
## Topic Brief: [Topic]

### Summary
[2-3 sentence executive summary]

### Background
[Context and history from internal sources]

### Current State
[Organization's current position or approach]

### Key Considerations
[Important factors, risks, open questions]

### Internal Precedent
[Prior decisions, memos, positions found]

### Gaps
[Missing information or unavailable sources]

### Recommended Next Steps
```

Note: Topic briefs synthesize available internal sources. For current legal authority or case law, recommend a legal research platform or outside counsel.

### Incident Brief

Rapid briefing for developing situations (data breaches, litigation threats, regulatory inquiries).

1. Accept the incident topic
2. Rapidly scan all connected sources
3. Compile actionable brief

```
## Incident Brief: [Topic]

**Prepared**: [timestamp]
**Classification**: [severity assessment]

### Situation Summary
### Timeline
### Immediate Legal Considerations
[Notification requirements, preservation obligations, privilege concerns]

### Relevant Agreements
### Internal Response
### Key Contacts
### Recommended Immediate Actions
1. [Most urgent]
2. [Second priority]

### Information Gaps
### Sources Checked
```

Incident brief notes:
- Speed matters — produce quickly with available information
- Flag litigation hold or preservation obligations immediately
- Note privilege considerations
- If potential data breach, flag notification deadlines (e.g., 72 hours for GDPR)
- Recommend outside counsel if matter is significant

## General Notes

- Note gaps prominently so the user knows what was not checked
- Briefs should be actionable: every item should have a clear next step
- Keep briefs concise; link to source materials rather than reproducing in full
