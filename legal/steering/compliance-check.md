# /compliance-check

Run a compliance check on a proposed action, product feature, or business initiative. Surfaces applicable regulations, required approvals, and risk areas.

## Usage

```
/compliance-check [description of what you're planning]
```

Examples:
- `/compliance-check We want to launch a referral program with cash rewards`
- `/compliance-check We're adding biometric authentication to our mobile app`
- `/compliance-check We need to process EU customer data in our US data center`

## Workflow

### 1. Understand the Initiative

Gather details about what is being proposed. Ask for specifics if the description is vague:
- What data is involved?
- What geographies are affected?
- Who are the users/customers?

### 2. Identify Applicable Regulations

Map the initiative against relevant regulations:

| Regulation | Jurisdiction | Key Focus |
|---|---|---|
| GDPR | EU/EEA | Personal data processing, cross-border transfers, DPIAs |
| CCPA/CPRA | California | Consumer rights, opt-out, sensitive PI |
| LGPD | Brazil | Similar to GDPR, DPO requirement |
| POPIA | South Africa | Information Regulator oversight |
| PIPEDA | Canada | Consent-based framework |
| PDPA | Singapore | Do Not Call registry, breach notification |
| PIPL | China | Strict cross-border transfer, data localization |
| UK GDPR | United Kingdom | Post-Brexit UK version |

### 3. Assess Requirements

For each applicable regulation, determine:
- What specific requirements apply
- Whether current practices meet those requirements
- What gaps exist

### 4. DPA Review (If Data Processing Involved)

Verify DPA elements per GDPR Article 28:
- Subject matter, duration, nature and purpose defined
- Processor obligations (instructions, confidentiality, security, sub-processors)
- Data subject rights assistance
- Breach notification timeline (24-48 hours to enable 72-hour regulatory deadline)
- International transfer mechanisms (SCCs, adequacy decisions, BCRs)
- Audit rights and deletion/return obligations

### 5. Data Subject Request Handling

If the initiative involves personal data, verify DSR processes:
- Request types supported (access, rectification, erasure, portability, objection, opt-out)
- Identity verification procedures
- Response timelines per regulation (GDPR: 30 days, CCPA: 45 days)
- Exemption checks (litigation hold, regulatory retention, third-party rights)

## Output Format

```
## Compliance Check: [Initiative]

### Summary
[Quick assessment: Proceed / Proceed with conditions / Requires further review]

### Applicable Regulations and Policies

| Regulation/Policy | Relevance | Key Requirements |
|-------------------|-----------|-----------------|
| [GDPR / CCPA / etc.] | [How it applies] | [What you need to do] |

### Requirements

| # | Requirement | Status | Action Needed |
|---|-------------|--------|---------------|
| 1 | [Requirement] | [Met / Not Met / Unknown] | [What to do] |

### Risk Areas

| Risk | Severity | Mitigation |
|------|----------|------------|
| [Risk] | [High/Med/Low] | [How to address] |

### Recommended Actions
1. [Most important action]
2. [Second priority]
3. [Third priority]

### Approvals Needed

| Approver | Why | Status |
|----------|-----|--------|
| [Person/Team] | [Reason] | [Pending] |

### Further Review Recommended
[Areas where outside counsel or specialist review is advised]
```

## Tips

- Be specific — "We want to email all our users" is better than "marketing campaign"
- Include the geography — compliance requirements vary by jurisdiction
- Mention the data — what personal data is involved drives most requirements
