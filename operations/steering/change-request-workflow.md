# Change Request Workflow

Create a structured change request with impact analysis, risk assessment, and rollback plan.

## When to Use
When the user needs to document a change affecting people, systems, or processes with formal approval and rollback planning.

## Output

```markdown
## Change Request: [Title]
**Requester:** [Name] | **Date:** [Date] | **Priority:** [Critical/High/Medium/Low]
**Status:** Draft | Pending Approval | Approved | In Progress | Complete

### Description
[What is changing and why]

### Business Justification
[Why this change is needed — cost savings, compliance, efficiency, risk reduction]

### Impact Analysis
| Area | Impact | Details |
|------|--------|---------|
| Users | [High/Med/Low/None] | [Who is affected and how] |
| Systems | [High/Med/Low/None] | [What systems are affected] |
| Processes | [High/Med/Low/None] | [What workflows change] |
| Cost | [High/Med/Low/None] | [Budget impact] |

### Risk Assessment
| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| [Risk] | [H/M/L] | [H/M/L] | [How to mitigate] |

### Implementation Plan
| Step | Owner | Timeline | Dependencies |
|------|-------|----------|--------------|

### Communication Plan
| Audience | Message | Channel | Timing |
|----------|---------|---------|--------|

### Rollback Plan
- Trigger: [When to roll back]
- Steps: [How to roll back]
- Verification: [How to confirm rollback worked]

### Approvals Required
| Approver | Role | Status |
|----------|------|--------|
```

See the **change-management** steering for the assess-plan-execute-sustain framework and communication principles.

## If Connectors Available

- **ITSM**: Create change request ticket automatically, pull CAB schedule and approval workflows
- **Project tracker**: Link to implementation tasks and dependencies
- **Chat**: Draft stakeholder notifications, post change updates to channels

## Tips

- Be specific about impact — "200 users in the billing team" not "everyone"
- Always have a rollback plan — even if confident, plan for failure
- Communicate early — surprises create resistance, previews create buy-in
