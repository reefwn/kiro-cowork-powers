# /vendor-check

Check the status of existing agreements with a vendor across all connected systems.

## Usage

```
/vendor-check [vendor name]
```

If no vendor name provided, prompt the user.

## Workflow

### 1. Identify the Vendor

Accept the vendor name. Handle common variations (legal name vs. trade name, abbreviations, parent/subsidiary). Ask for clarification if ambiguous.

### 2. Search Connected Systems

Search in priority order:

- **CLM**: Active agreements, expired (last 3 years), in negotiation, amendments
- **CRM**: Account status, relationship type, associated opportunities, contacts
- **Email**: Contract-related emails (last 6 months), NDA/agreement attachments, negotiation threads
- **Documents**: Executed agreements, redlines, due diligence materials
- **Chat**: Contract requests, legal questions, relevant discussions (last 3 months)

### 3. Compile Agreement Status

For each agreement found, report:

| Field | Details |
|-------|---------|
| Agreement Type | NDA, MSA, SOW, DPA, SLA, License Agreement, etc. |
| Status | Active, Expired, In Negotiation, Pending Signature |
| Effective Date | When the agreement started |
| Expiration Date | When it expires or renews |
| Auto-Renewal | Yes/No, with renewal term and notice period |
| Key Terms | Liability cap, governing law, termination provisions |
| Amendments | Any amendments or addenda on file |

### 4. Gap Analysis

Identify what exists and what might be missing:

```
## Agreement Coverage

[CHECK] NDA — [status]
[CHECK/MISSING] MSA — [status or "Not found"]
[CHECK/MISSING] DPA — [status or "Not found"]
[CHECK/MISSING] SOW(s) — [status or "Not found"]
[CHECK/MISSING] SLA — [status or "Not found"]
[CHECK/MISSING] Insurance Certificate — [status or "Not found"]
```

Flag gaps based on relationship type (e.g., MSA but no DPA when vendor handles personal data).

### 5. Generate Report

```
## Vendor Agreement Status: [Vendor Name]

**Search Date**: [today]
**Sources Checked**: [list]
**Sources Unavailable**: [list]

## Relationship Overview
**Vendor**: [full legal name]
**Relationship Type**: [vendor/partner/customer]

## Agreement Summary

### [Agreement Type] — [Status]
- **Effective**: [date]
- **Expires**: [date] ([auto-renews / does not auto-renew])
- **Key Terms**: [summary]
- **Location**: [where stored]

## Gap Analysis
[What's in place vs. what may be needed]

## Upcoming Actions
- [Approaching expirations or renewal deadlines]
- [Required agreements not yet in place]
- [Amendments or updates needed]
```

### 6. Handle Missing Sources

If key systems are not connected:
- Note which sources were not searched
- Suggest manual checks (e.g., "search your email for '[vendor] agreement'")
- Always clearly state completeness of the report

## Notes

- If no agreements found anywhere, report clearly and ask if stored elsewhere
- For vendor groups, ask whether to check specific entity or entire group
- Flag expired agreements with surviving obligations (confidentiality, indemnification)
- Highlight agreements approaching expiration within 90 days
