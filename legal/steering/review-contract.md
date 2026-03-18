# /review-contract

Review a contract against your organization's negotiation playbook — flag deviations, generate redlines, provide business impact analysis.

## Usage

```
/review-contract
```

Accepts: file upload, URL, or pasted contract text.

## Workflow

### 1. Accept the Contract

Accept the contract as a file upload (PDF, DOCX), URL, or pasted text. If none provided, prompt the user.

### 2. Gather Context

Ask:
1. Which side are you on? (vendor, customer, licensor, licensee, partner)
2. Deadline for finalization
3. Focus areas (e.g., data protection, liability, IP ownership)
4. Deal context (deal size, strategic importance, existing relationship)

Proceed with partial context if provided and note assumptions.

### 3. Load the Playbook

Look for the organization's contract review playbook in local settings (e.g., `legal.local.md`). The playbook defines standard positions, acceptable ranges, and escalation triggers.

If no playbook is configured, inform the user and offer to proceed with generic commercial standards as baseline.

### 4. Clause-by-Clause Analysis

Analyze systematically, covering at minimum:

| Clause Category | Key Review Points |
|----------------|-------------------|
| Limitation of Liability | Cap amount, carveouts, mutual vs. unilateral, consequential damages |
| Indemnification | Scope, mutual vs. unilateral, cap, IP infringement, data breach |
| IP Ownership | Pre-existing IP, developed IP, work-for-hire, license grants, assignment |
| Data Protection | DPA requirement, processing terms, sub-processors, breach notification, cross-border transfers |
| Confidentiality | Scope, term, carveouts, return/destruction obligations |
| Representations & Warranties | Scope, disclaimers, survival period |
| Term & Termination | Duration, renewal, termination for convenience/cause, wind-down |
| Governing Law & Dispute Resolution | Jurisdiction, venue, arbitration vs. litigation |
| Insurance | Coverage requirements, minimums, evidence of coverage |
| Assignment | Consent requirements, change of control, exceptions |
| Force Majeure | Scope, notification, termination rights |
| Payment Terms | Net terms, late fees, taxes, price escalation |

Read the entire contract before flagging issues — clauses interact with each other.

### 5. Flag Deviations

Classify each deviation:

- **GREEN — Acceptable**: Aligns with or is better than standard position. No negotiation needed.
- **YELLOW — Negotiate**: Outside standard but within negotiable range. Generate specific redline language, fallback position, and business impact.
- **RED — Escalate**: Outside acceptable range or triggers escalation criteria. Explain risk, provide market-standard alternative, estimate exposure, recommend escalation path.

### 6. Generate Redline Suggestions

For each YELLOW and RED deviation:

```
**Clause**: [Section reference and clause name]
**Current language**: "[exact quote]"
**Proposed redline**: "[specific alternative language]"
**Rationale**: [1-2 sentences suitable for external sharing]
**Priority**: [Must-have / Should-have / Nice-to-have]
**Fallback**: [Alternative position if primary redline is rejected]
```

### 7. Business Impact Summary

Provide:
- Overall risk assessment
- Top 3 issues to address
- Negotiation strategy (which issues to lead with, what to concede)
- Timeline considerations

Organize redlines by negotiation priority:
- **Tier 1 — Must-Haves**: Deal breakers requiring resolution
- **Tier 2 — Should-Haves**: Material risk with negotiation room
- **Tier 3 — Nice-to-Haves**: Concession candidates

## Output Format

```
## Contract Review Summary

**Document**: [contract name]
**Parties**: [party names and roles]
**Your Side**: [vendor/customer/etc.]
**Deadline**: [if provided]
**Review Basis**: [Playbook / Generic Standards]

## Key Findings
[Top 3-5 issues with severity flags]

## Clause-by-Clause Analysis

### [Clause Category] — [GREEN/YELLOW/RED]
**Contract says**: [summary]
**Playbook position**: [your standard]
**Deviation**: [description of gap]
**Business impact**: [what this means practically]
**Redline suggestion**: [specific language, if YELLOW or RED]

## Negotiation Strategy
[Recommended approach, priorities, concession candidates]

## Next Steps
[Specific actions to take]
```

## Notes

- For contracts in other languages, ask if the user wants translation or review in the original language
- For very long contracts (50+ pages), offer to focus on the most material sections first
- Always remind the user that analysis should be reviewed by qualified legal counsel
