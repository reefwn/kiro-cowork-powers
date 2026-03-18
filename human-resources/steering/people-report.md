# /people-report

Generate people analytics reports from your HR data.

## Usage

```
/people-report [report type]
```

## How It Works

```
┌─────────────────────────────────────────────────────────────────┐
│ PEOPLE REPORT                                                   │
├─────────────────────────────────────────────────────────────────┤
│ STANDALONE (always works)                                       │
│ ✓ Upload a CSV or describe your data                            │
│ ✓ Headcount, attrition, diversity, or org health reports        │
│ ✓ Data-driven recommendations                                   │
├─────────────────────────────────────────────────────────────────┤
│ SUPERCHARGED (when you connect your tools)                      │
│ + HRIS: Pull live employee data automatically                   │
│ + Chat: Share report summaries to channels                      │
└─────────────────────────────────────────────────────────────────┘
```

## Report Types

- **Headcount**: Current org snapshot — by team, location, level, tenure
- **Attrition**: Turnover analysis — voluntary/involuntary, by team, trends
- **Diversity**: Representation metrics — by level, team, pipeline
- **Org Health**: Span of control, management layers, team sizes, flight risk

## Key Metrics

### Retention
- Overall attrition rate (voluntary + involuntary)
- Regrettable attrition rate
- Average tenure
- Flight risk indicators

### Diversity
- Representation by level, team, and function
- Pipeline diversity (hiring funnel by demographic)
- Promotion rates by group
- Pay equity analysis

### Engagement
- Survey scores and trends
- eNPS (Employee Net Promoter Score)
- Participation rates
- Open-ended feedback themes

### Productivity
- Revenue per employee
- Span of control efficiency
- Time to productivity for new hires

## What I Need From You

Upload a CSV or describe your data. Helpful fields:
- Employee name/ID, department, team
- Title, level, location
- Start date, end date (if applicable)
- Manager, compensation (if relevant)
- Demographics (for diversity reports, if available)

## Output

```markdown
## People Report: [Type] — [Date]

### Executive Summary
[2-3 key takeaways]

### Key Metrics
| Metric | Value | Trend |
|--------|-------|-------|
| [Metric] | [Value] | [up/down/flat] |

### Detailed Analysis
[Charts, tables, and narrative for the specific report type]

### Recommendations
- [Data-driven recommendation]
- [Action item]

### Methodology
[How the numbers were calculated, any caveats]
```

## If Connectors Available

If **~~HRIS** is connected:
- Pull live employee data — headcount, tenure, department, level
- Generate reports without needing a CSV upload

If **~~chat** is connected:
- Offer to share the report summary in a relevant channel
