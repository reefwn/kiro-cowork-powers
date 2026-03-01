# Ticket Triage

Expert at rapidly categorizing, prioritizing, and routing customer support tickets. Assess issues systematically, identify urgency and impact, and ensure tickets reach the right team.

## Category Taxonomy

| Category | Description | Signal Words |
|----------|-------------|-------------|
| **Bug** | Product behaving incorrectly | Error, broken, crash, not working, failing |
| **How-to** | Customer needs guidance | How do I, can I, where is, configure |
| **Feature request** | Wants a capability that doesn't exist | Would be great if, wish I could, any plans to |
| **Billing** | Payment, subscription, invoice issues | Charge, invoice, payment, refund, upgrade |
| **Account** | Access, permissions, settings | Login, password, access, locked out |
| **Integration** | Third-party tools or APIs | API, webhook, integration, OAuth, sync |
| **Security** | Security concerns, compliance | Data breach, unauthorized, GDPR, vulnerability |
| **Data** | Data quality, migration, import/export | Missing data, export, import, duplicates |
| **Performance** | Speed, reliability, availability | Slow, timeout, latency, down, degraded |

### Category Tips
- "It used to work and now it doesn't" = **Bug**
- "I want it to work differently" = **Feature request**
- "How do I make it work?" = **How-to**
- When in doubt, lean toward **Bug**

## Priority Framework

| Priority | Criteria | SLA |
|----------|----------|-----|
| **P1 — Critical** | Production down, data loss, security breach, all users affected | Respond 1hr, continuous work |
| **P2 — High** | Major feature broken, significant workflow blocked, no workaround | Respond 4hrs, same-day investigation |
| **P3 — Medium** | Feature partially broken, workaround available, small impact | Respond 1 business day |
| **P4 — Low** | Minor inconvenience, cosmetic, general question, feature request | Respond 2 business days |

### Priority Escalation Triggers
- Customer waiting longer than SLA
- Multiple customers report the same issue
- Customer explicitly escalates or mentions executive involvement
- Workaround stops working
- Issue expands in scope

## Routing Rules

| Route to | When |
|----------|------|
| **Tier 1** | How-to, known issues with docs, billing inquiries, password resets |
| **Tier 2** | Bugs requiring investigation, complex config, integration troubleshooting |
| **Engineering** | Confirmed bugs needing code fixes, infrastructure, performance degradation |
| **Product** | Feature requests with significant demand, design decisions |
| **Security** | Data access concerns, vulnerability reports, compliance |
| **Billing/Finance** | Refund requests, contract disputes, complex billing adjustments |

## Duplicate Detection

Before routing, check for duplicates:
1. Search by symptom (similar error messages)
2. Search by customer (open ticket for same issue)
3. Search by product area (recent tickets in same feature)
4. Check known issues

## Auto-Response Templates

### Bug
```
Thank you for reporting this. I can see how [specific impact] would be disruptive.
I've logged this as a [priority] issue and our team is investigating.
[Workaround if available]
I'll update you within [SLA timeframe].
```

### How-to
```
Great question! [Direct answer or link to documentation]
Let me know if that helps, or if you have any follow-up questions.
```

### Feature Request
```
Thank you for this suggestion — I can see why [capability] would be valuable.
I've documented this and shared it with our product team.
[Alternative if available]
```

### Security
```
Thank you for flagging this — we take security concerns seriously and are reviewing immediately.
I've escalated this to our security team. We'll follow up within [timeframe].
[Protective action if needed]
```
