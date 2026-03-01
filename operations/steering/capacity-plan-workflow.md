# Capacity Plan Workflow

Analyze team capacity and plan resource allocation.

## When to Use
When the user needs to plan resource capacity, analyze workload, or forecast utilization.

## What I Need

- **Team size and roles**: Who do you have?
- **Current workload**: What are they working on? (Upload from project tracker or describe)
- **Upcoming work**: What's coming next quarter?
- **Constraints**: Budget, hiring timeline, skill requirements

## Output

```markdown
## Capacity Plan: [Team/Project]
**Period:** [Date range] | **Team Size:** [X]

### Current Utilization
| Person/Role | Capacity | Allocated | Available | Utilization |
|-------------|----------|-----------|-----------|-------------|
| [Name/Role] | [hrs/wk] | [hrs/wk] | [hrs/wk] | [X]% |

### Capacity Summary
- Total capacity: [X] hours/week
- Currently allocated: [X] hours/week ([X]%)
- Available: [X] hours/week ([X]%)
- Overallocated: [X people above 100%]

### Upcoming Demand
| Project/Initiative | Start | End | Resources Needed | Gap |
|--------------------|-------|-----|-----------------|-----|
| [Project] | [Date] | [Date] | [X FTEs] | [Covered/Gap] |

### Bottlenecks
- [Skill or role that's oversubscribed]
- [Time period with a crunch]

### Recommendations
1. [Hire / Contract / Reprioritize / Delay]

### Scenarios
| Scenario | Outcome |
|----------|---------|
| Do nothing | [What happens] |
| Hire [X] | [What changes] |
| Deprioritize [Y] | [What frees up] |
```

See the **resource-planning** steering for utilization targets by role type and common pitfalls.

## If Connectors Available

- **Project tracker**: Pull current workload and ticket assignments, upcoming commitments per person
- **Calendar**: Factor in PTO, holidays, recurring meeting load; calculate actual available hours

## Tips

- Include all work — BAU, projects, support, meetings. People aren't 100% available for project work.
- Plan for buffer — target 80% utilization.
- Update regularly — capacity plans go stale fast. Review monthly.
