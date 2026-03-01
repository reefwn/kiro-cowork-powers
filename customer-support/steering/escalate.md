# /escalate

Package a support issue into a structured escalation brief for engineering, product, or leadership. Gathers context, structures reproduction steps, assesses business impact, and identifies the right escalation target.

## Usage

```
/escalate [description]
```

Examples:
- `/escalate API returning 500 errors intermittently for Acme Corp`
- `/escalate Data export is missing rows — 3 customers reported this week`
- `/escalate SSO login loop affecting all Enterprise customers`
- `/escalate Customer threatening to churn over missing audit log feature`

## Workflow

### 1. Understand the Issue

Parse the input and determine:
- **What's broken or needed**: The core technical or product issue
- **Who's affected**: Specific customer(s), segment, or all users
- **How long**: When did this start? How long has the customer been waiting?
- **What's been tried**: Any troubleshooting or workarounds attempted
- **Why escalate now**: What makes this need attention beyond normal support

Use the "When to Escalate vs. Handle in Support" criteria from the **escalation** skill.

### 2. Gather Context

Pull together relevant information from available sources:
- **~~support platform**: Related tickets, timeline of communications
- **~~CRM**: Account details, key contacts, previous escalations
- **~~chat**: Internal discussions about this issue
- **~~project tracker**: Related bug reports or feature requests
- **~~knowledge base**: Known issues or workarounds

### 3. Assess Business Impact

Quantify using the impact dimensions from the **escalation** skill:
- **Breadth**: How many customers/users affected? Growing?
- **Depth**: Blocked vs. inconvenienced?
- **Duration**: How long has this been going on?
- **Revenue**: ARR at risk? Pending deals affected?
- **Time pressure**: Hard deadline?

### 4. Determine Escalation Target

Using the escalation tiers from the **escalation** skill: L2 Support, Engineering, Product, Security, or Leadership.

### 5. Generate Escalation Brief

```
## ESCALATION: [One-line summary]

**Severity:** [Critical / High / Medium]
**Target team:** [Engineering / Product / Security / Leadership]
**Reported by:** [Your name/team]
**Date:** [Today's date]

### Impact
- **Customers affected:** [Who and how many]
- **Workflow impact:** [What they can't do]
- **Revenue at risk:** [If applicable]
- **Time in queue:** [How long this has been an issue]

### Issue Description
[Clear, concise description — 3-5 sentences]

### What's Been Tried
1. [Troubleshooting step and result]
2. [Troubleshooting step and result]

### Reproduction Steps
[If applicable — follow the format from the escalation skill]

### Customer Communication
- **Last update to customer:** [Date and what was communicated]
- **Customer expectation:** [What they're expecting and by when]
- **Escalation risk:** [Will they escalate further if not resolved by X?]

### What's Needed
- [Specific ask — "investigate root cause", "prioritize fix", "make product decision"]
- **Deadline:** [When this needs resolution or an update]

### Supporting Context
- [Related tickets or links]
- [Internal discussion threads]
- [Documentation or logs]
```

### 6. Offer Next Steps

- "Want me to post this in a ~~chat channel for the target team?"
- "Should I update the customer with an interim response?"
- "Want me to set a follow-up reminder to check on this?"
