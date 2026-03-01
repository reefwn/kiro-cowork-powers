# Vendor Review Workflow

Evaluate a vendor with structured analysis covering cost, risk, performance, and fit.

## When to Use
When the user is evaluating a new vendor, making a renewal decision, or comparing vendors side-by-side.

## What I Need

- **Vendor name**: Who are you evaluating?
- **Context**: New evaluation, renewal, or comparison?
- **Details**: Contract terms, pricing, proposal document, or current performance data

## Output

```markdown
## Vendor Review: [Vendor Name]
**Date:** [Date] | **Type:** [New / Renewal / Comparison]

### Summary
[2-3 sentence recommendation]

### Cost Analysis
| Component | Annual Cost | Notes |
|-----------|-------------|-------|
| License/subscription | $[X] | [Per seat, flat, usage-based] |
| Implementation | $[X] | [One-time] |
| Support/maintenance | $[X] | [Included or add-on] |
| **Total Year 1** | **$[X]** | |
| **Total 3-Year** | **$[X]** | |

### Risk Assessment
| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|

### Strengths
- [Strength 1]
- [Strength 2]

### Concerns
- [Concern 1]
- [Concern 2]

### Recommendation
[Proceed / Negotiate / Pass] — [Reasoning]

### Negotiation Points
- [Leverage point 1]
- [Leverage point 2]
```

See the **vendor-management** steering for TCO frameworks, risk criteria, and performance metrics.

## If Connectors Available

- **Knowledge base**: Search for existing vendor evaluations, contracts, performance reviews; pull procurement policies
- **Procurement**: Pull current contract terms, spend history, renewal dates; compare against existing agreements

## Tips

- Upload the proposal — I can extract pricing, terms, and SLAs from vendor documents
- Compare vendors — "Compare Vendor A vs Vendor B" gets a side-by-side analysis
- Include current spend — for renewals, knowing what you pay now helps evaluate changes
