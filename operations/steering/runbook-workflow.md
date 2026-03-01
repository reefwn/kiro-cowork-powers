# Runbook Workflow

Create a step-by-step operational runbook for a recurring task or procedure.

## When to Use
When the user needs to document a repeatable operational procedure with exact steps, failure modes, and escalation paths.

## Output

```markdown
## Runbook: [Task Name]
**Owner:** [Team/Person] | **Frequency:** [Daily/Weekly/Monthly/As Needed]
**Last Updated:** [Date] | **Last Run:** [Date]

### Purpose
[What this runbook accomplishes and when to use it]

### Prerequisites
- [ ] [Access or permission needed]
- [ ] [Tool or system required]
- [ ] [Data or input needed]

### Procedure

#### Step 1: [Name]
```
[Exact command, action, or instruction]
```
**Expected result:** [What should happen]
**If it fails:** [What to do]

#### Step 2: [Name]
```
[Exact command, action, or instruction]
```
**Expected result:** [What should happen]
**If it fails:** [What to do]

### Verification
- [ ] [How to confirm task completed successfully]

### Troubleshooting
| Symptom | Likely Cause | Fix |
|---------|-------------|-----|

### Rollback
[How to undo this if something goes wrong]

### Escalation
| Situation | Contact | Method |
|-----------|---------|--------|

### History
| Date | Run By | Notes |
|------|--------|-------|
```

## If Connectors Available

- **Knowledge base**: Search for existing runbooks to update; publish to ops wiki
- **ITSM**: Link to related incident types and change requests; auto-populate escalation contacts

## Tips

- Be painfully specific — "Run `python sync.py --prod --dry-run` from the ops server" not "Run the script"
- Include failure modes — what can go wrong at each step and what to do
- Test the runbook — have someone unfamiliar follow it; fix where they get stuck
