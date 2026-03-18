# /validate

Review an analysis for accuracy, methodology, and potential biases before sharing with stakeholders. Generates a confidence assessment and improvement suggestions.

## Usage

```
/validate
```

The analysis can be: a document or report in the conversation, a file (markdown, notebook, spreadsheet), SQL queries and their results, charts and their underlying data, or a description of methodology and findings.

## How It Works

```
┌─────────────────────────────────────────────────────────────────┐
│ VALIDATE ANALYSIS                                               │
├─────────────────────────────────────────────────────────────────┤
│ STANDALONE (always works)                                       │
│ ✓ Review methodology and assumptions                            │
│ ✓ Check for common analytical pitfalls                          │
│ ✓ Spot-check calculations and aggregation logic                 │
│ ✓ Assess visualizations for accuracy                            │
│ ✓ Generate confidence assessment                                │
├─────────────────────────────────────────────────────────────────┤
│ SUPERCHARGED (when you connect your tools)                      │
│ + Data warehouse: Re-run queries to verify results              │
│ + Notebook: Execute validation checks in notebook               │
└─────────────────────────────────────────────────────────────────┘
```

## Workflow

### 1. Review Methodology and Assumptions

Examine:
- **Question framing**: Is the analysis answering the right question?
- **Data selection**: Are the right tables/datasets being used? Is the time range appropriate?
- **Population definition**: Is the analysis population correctly defined? Unintended exclusions?
- **Metric definitions**: Are metrics defined clearly and consistently?
- **Baseline and comparison**: Is the comparison fair?

### 2. Pre-Delivery QA Checklist

**Data Quality Checks:**
- [ ] Source verification — correct tables/data sources
- [ ] Freshness — data is current enough, "as of" date noted
- [ ] Completeness — no unexpected gaps
- [ ] Null handling — nulls handled appropriately
- [ ] Deduplication — no double-counting from bad joins
- [ ] Filter verification — all WHERE clauses correct

**Calculation Checks:**
- [ ] Aggregation logic — GROUP BY includes all non-aggregated columns
- [ ] Denominator correctness — rates use the right denominator
- [ ] Date alignment — comparisons use same period length
- [ ] Join correctness — appropriate JOIN types, no many-to-many inflation
- [ ] Metric definitions — match stakeholder understanding
- [ ] Subtotals sum — parts add up to the whole

**Reasonableness Checks:**
- [ ] Magnitude — numbers in plausible range
- [ ] Trend continuity — no unexplained jumps or drops
- [ ] Cross-reference — key numbers match other known sources
- [ ] Edge cases — boundaries handled correctly

**Presentation Checks:**
- [ ] Chart accuracy — bar charts start at zero, axes labeled, scales consistent
- [ ] Number formatting — appropriate precision, consistent formatting
- [ ] Title clarity — titles state the insight, date ranges specified
- [ ] Caveat transparency — limitations stated explicitly
- [ ] Reproducibility — someone else could recreate this analysis

### 3. Check for Common Analytical Pitfalls

- **Join explosion**: Many-to-many join silently multiplies rows
- **Survivorship bias**: Analyzing only entities that exist today
- **Incomplete period comparison**: Comparing partial period to full period
- **Denominator shifting**: Denominator changes between periods
- **Average of averages**: Averaging pre-computed averages gives wrong results
- **Timezone mismatches**: Different sources use different timezones
- **Selection bias**: Segments defined by the outcome being measured
- **Simpson's paradox**: Trend reverses when aggregated vs. segmented
- **Cherry-picked time ranges**: Ranges that favor a particular narrative

### 4. Verify Calculations

Where possible, spot-check:
- Recalculate key numbers independently
- Verify subtotals sum to totals
- Check percentages sum to ~100% where expected
- Confirm YoY/MoM comparisons use correct base periods
- Validate filters applied consistently across all metrics

### 5. Assess Visualizations

- Do axes start at appropriate values?
- Are scales consistent across comparison charts?
- Do chart titles accurately describe what's shown?
- Could the visualization mislead a quick reader?
- Are there truncated axes, inconsistent intervals, or 3D effects?

### 6. Evaluate Narrative and Conclusions

- Conclusions supported by the data shown?
- Alternative explanations acknowledged?
- Uncertainty communicated appropriately?
- Recommendations follow logically from findings?
- Confidence level matches strength of evidence?

### 7. Generate Confidence Assessment

Rate on a 3-level scale:

**Ready to share** — Methodologically sound, calculations verified, caveats noted. Minor suggestions but nothing blocking.

**Share with noted caveats** — Largely correct but has specific limitations that must be communicated to stakeholders.

**Needs revision** — Found specific errors, methodological issues, or missing analyses that should be addressed first.

## Output

```markdown
## Validation Report

### Overall Assessment: [Ready to share | Share with caveats | Needs revision]

### Methodology Review
[Findings about approach, data selection, definitions]

### Issues Found
1. [Severity: High/Medium/Low] [Issue description and impact]

### Calculation Spot-Checks
- [Metric]: [Verified / Discrepancy found]

### Visualization Review
[Any issues with charts or visual presentation]

### Suggested Improvements
1. [Improvement and why it matters]

### Required Caveats for Stakeholders
- [Caveat that must be communicated]
```

## Tips

- Run `/validate` before any high-stakes presentation or decision.
- Even quick analyses benefit from a sanity check.
- If validation finds issues, fix them and re-validate.
- Share the validation output alongside your analysis to build stakeholder confidence.
