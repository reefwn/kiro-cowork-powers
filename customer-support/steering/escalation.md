# Escalation

Expert at determining when and how to escalate support issues. Structure escalation briefs that give receiving teams everything they need to act quickly.

## When to Escalate vs. Handle in Support

### Handle in Support When:
- Documented solution or known workaround exists
- Configuration or setup issue you can resolve
- Customer needs guidance or training
- Known limitation with documented alternative
- Previous similar tickets resolved at support level

### Escalate When:
- **Technical**: Bug confirmed, infrastructure investigation needed, data corruption/loss
- **Complexity**: Beyond support's ability to diagnose, requires access support doesn't have
- **Impact**: Multiple customers affected, production down, data integrity at risk, security concern
- **Business**: High-value customer at risk, SLA breach imminent, customer requesting executive involvement
- **Time**: Open beyond SLA, customer waiting unreasonably long
- **Pattern**: Same issue reported by 3+ customers, recurring issue supposedly fixed

## Escalation Tiers

| From → To | When | What to Include |
|-----------|------|-----------------|
| L1 → L2 | Deeper investigation, specialized knowledge | Ticket summary, steps tried, customer context |
| L2 → Engineering | Confirmed bug, infrastructure issue, needs code change | Reproduction steps, environment, logs, business impact |
| L2 → Product | Feature gap, design decision needed, workflow mismatch | Customer use case, business impact, frequency |
| Any → Security | Data exposure, unauthorized access, vulnerability, compliance | What was observed, who's affected, containment steps |
| Any → Leadership | High-revenue churn risk, SLA breach, cross-functional decision needed | Full business context, revenue at risk, specific decision needed |

## Business Impact Assessment

| Dimension | Questions to Answer |
|-----------|-------------------|
| **Breadth** | How many customers/users affected? Growing? |
| **Depth** | Blocked vs. inconvenienced? |
| **Duration** | How long? How long until critical? |
| **Revenue** | ARR at risk? Pending deals affected? |
| **Reputation** | Could this become public? Reference customer? |
| **Contractual** | SLAs being breached? Contractual obligations? |

## Severity Shorthand

- **Critical**: Production down, data at risk, security breach. Immediate attention.
- **High**: Major functionality broken, key customer blocked, SLA at risk. Same-day.
- **Medium**: Significant issue with workaround. This week.

## Writing Reproduction Steps

1. Start from a clean state (account type, configuration, permissions)
2. Be specific ("Click the Export button in the top-right of the Dashboard page")
3. Include exact values (specific inputs, dates, IDs)
4. Note the environment (browser, OS, account type, plan level)
5. Capture frequency (always reproducible? intermittent?)
6. Include evidence (screenshots, error messages, logs)
7. Note what you've ruled out

## Follow-up Cadence After Escalation

| Severity | Internal Follow-up | Customer Update |
|----------|-------------------|-----------------|
| **Critical** | Every 2 hours | Every 2-4 hours |
| **High** | Every 4 hours | Every 4-8 hours |
| **Medium** | Daily | Every 1-2 business days |
