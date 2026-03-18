# /legal-response

Generate a response to a common legal inquiry using configured templates, with built-in escalation checks.

## Usage

```
/legal-response [inquiry-type]
```

Inquiry types: `dsr`, `hold`, `vendor`, `nda`, `privacy`, `subpoena`, `insurance`, `custom`

If no type provided, show available categories and ask.

## Workflow

### 1. Identify Inquiry Type

Accept the inquiry type. If ambiguous, show categories and ask for clarification.

### 2. Load Template

Look for templates in local settings (e.g., `legal.local.md`). If no templates configured, offer to help create one or provide a reasonable default structure.

### 3. Check Escalation Triggers

Before generating any response, check for situations that should NOT use a template:

**Universal triggers** (all categories):
- Potential litigation or regulatory investigation
- Inquiry from regulator, government agency, or law enforcement
- Response could create binding legal commitment or waiver
- Potential criminal liability
- Media attention involved or likely
- Unprecedented situation
- Multiple jurisdictions with conflicting requirements
- Involves executive leadership or board members

**Category-specific triggers**:
- DSR: Minor's data, regulatory authority request, litigation hold conflict, employee dispute
- Discovery Hold: Criminal liability, unclear scope, conflicts with deletion requirements
- Vendor: Dispute or breach, threatened litigation, regulatory compliance issue
- NDA: Competitor counterparty, government classified info, potential M&A
- Subpoena: ALWAYS requires counsel review

When triggered: Stop, alert the user, explain which trigger was detected, recommend escalation path, offer a draft marked "FOR COUNSEL REVIEW ONLY".

### 4. Gather Details

Prompt for details needed to customize the response based on inquiry type:
- DSR: Requester info, request type, applicable regulation, deadline
- Discovery Hold: Matter name, custodians, scope, outside counsel contact
- Vendor: Vendor name, reference agreement, specific question
- NDA: Requesting team, counterparty, purpose, mutual/unilateral

### 5. Generate Response

Populate the template with gathered details. Ensure:
- Appropriate tone (professional, clear)
- All required legal elements included
- Specific dates, deadlines, and obligations referenced
- Clear next steps for the recipient
- Appropriate disclaimers

Present draft for user review before sending.

## Response Categories

1. **Data Subject Requests**: Acknowledgment, identity verification, fulfillment, denial, extension
2. **Discovery Holds**: Initial notice, reminder, modification, release
3. **Privacy Inquiries**: Cookie/tracking, privacy policy, data sharing, cross-border
4. **Vendor Legal Questions**: Contract status, amendment, compliance certification, audit
5. **NDA Requests**: Standard form, counterparty markup, decline, renewal
6. **Subpoena / Legal Process**: Acknowledgment, objection, extension, compliance cover letter
7. **Insurance Notifications**: Initial claim, supplemental info, reservation of rights response

## Output Format

```
## Generated Response: [Inquiry Type]

**To**: [recipient]
**Subject**: [subject line]

---

[Response body]

---

### Escalation Check
[Confirmation that no triggers detected, OR flagged triggers with recommendations]

### Follow-Up Actions
1. [Post-send actions]
2. [Calendar reminders to set]
3. [Tracking or logging requirements]
```

## Notes

- Always present draft for user review before suggesting it be sent
- If connected to ~~email, offer to create a draft email
- Track response deadlines and offer to set calendar reminders
- For regulated responses (DSRs, subpoenas), always note the applicable deadline
