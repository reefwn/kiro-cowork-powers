# /draft-response

Draft a professional, customer-facing response tailored to the situation, customer relationship, and communication context.

## Usage

```
/draft-response [situation description]
```

Examples:
- `/draft-response Acme Corp is asking when the new dashboard feature will ship`
- `/draft-response Customer escalation — their integration has been down for 2 days`
- `/draft-response Responding to a feature request we won't be building`
- `/draft-response Customer hit a billing error and wants a resolution ASAP`

## Workflow

### 1. Understand the Context

Parse the input to determine:
- **Customer**: Who is the communication for?
- **Situation type**: Question, issue, escalation, announcement, bad news, good news, follow-up
- **Urgency**: Is this time-sensitive? How long has the customer been waiting?
- **Channel**: Email, support ticket, chat (adjust formality accordingly)
- **Relationship stage**: New customer, established, frustrated/escalated
- **Stakeholder level**: End user, manager, executive, technical, business

### 2. Research Context

Gather relevant background from available sources:
- **~~email**: Previous correspondence
- **~~chat**: Internal discussions about this customer
- **~~CRM**: Account details and plan level
- **~~support platform**: Related tickets and their resolution
- **~~knowledge base**: Official documentation to reference

### 3. Generate the Draft

```
## Draft Response

**To:** [Customer contact name]
**Re:** [Subject/topic]
**Channel:** [Email / Ticket / Chat]
**Tone:** [Empathetic / Professional / Technical / Celebratory / Candid]

---

[Draft response text]

---

### Notes for You (internal — do not send)
- **Why this approach:** [Rationale for tone and content choices]
- **Things to verify:** [Any facts or commitments to confirm before sending]
- **Risk factors:** [Anything sensitive about this response]
- **Follow-up needed:** [Actions to take after sending]
```

### 4. Situation-Specific Approaches

- **Answering a product question**: Lead with the direct answer, provide docs links
- **Responding to an issue/bug**: Acknowledge impact, state what you know, provide workaround, set timeline
- **Handling an escalation**: Acknowledge severity, take ownership, provide clear action plan
- **Delivering bad news**: Be direct, explain reasoning, acknowledge impact, offer alternatives
- **Sharing good news**: Lead with the positive outcome, connect to their goals
- **Declining a request**: Acknowledge the request, be honest, offer alternatives

### 5. Quality Checks

Before presenting the draft, verify:
- Tone matches the situation and relationship
- No commitments beyond what's authorized
- No product roadmap details that shouldn't be shared externally
- Clear next steps and ownership
- Length is appropriate for the channel

### 6. Offer Iterations

- "Want me to adjust the tone?"
- "Should I add or remove any specific points?"
- "Want me to make this shorter/longer?"
- "Should I draft a version for a different stakeholder?"
