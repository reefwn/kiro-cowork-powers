# /signature-request

Prepare and route a document for e-signature — run a pre-signature checklist, configure signing order, and send for execution.

## Usage

```
/signature-request
```

Accepts: file upload, URL, or document reference.

## Workflow

### 1. Accept the Document

Accept the document as a file upload (PDF, DOCX), URL to ~~cloud storage or ~~CLM, or a reference ("the Acme Corp MSA we finalized yesterday").

### 2. Pre-Signature Checklist

Before routing, verify:

```
## Pre-Signature Checklist

- [ ] Document is in final, agreed form (no open redlines)
- [ ] All exhibits and schedules are attached
- [ ] Correct legal entity names on signature blocks
- [ ] Dates are correct or left blank for execution date
- [ ] Signature blocks match the authorized signers
- [ ] Any required internal approvals have been obtained
- [ ] Document has been reviewed by appropriate counsel
```

### 3. Configure Signing

Gather signing details:
- **Signers**: Who needs to sign? (names, emails, titles)
- **Signing order**: Sequential or parallel?
- **Internal approval**: Does anyone need to approve before the counterparty signs?
- **CC recipients**: Who should receive a copy of the executed document?

### 4. Route for Signature

**If ~~e-signature is connected:**
- Create the signature envelope/request
- Set signing fields and order
- Add required initials or date fields
- Send for signature

**If not connected:**
- Generate a signing instruction document
- Provide the document formatted for wet signature or manual e-sign
- List all signers with contact information

## Output Format

```
## Signature Request: [Document Title]

### Document Details
- **Type**: [MSA / NDA / SOW / Amendment / etc.]
- **Parties**: [Party A] and [Party B]
- **Pages**: [X]

### Pre-Signature Check: [PASS / ISSUES FOUND]
[List any issues needing attention before sending]

### Signing Configuration

| Order | Signer | Email | Role |
|-------|--------|-------|------|
| 1 | [Name] | [email] | [Party A Authorized Signatory] |
| 2 | [Name] | [email] | [Party B Authorized Signatory] |

### CC Recipients
- [Name] — [email]

### Status
[Sent for signature / Ready to send / Issues to resolve first]

### Next Steps
- [What to expect after sending]
- [Expected turnaround time]
- [Follow-up if not signed within X days]
```

## Tips

- Check entity names carefully — the most common signing error is incorrect legal entity names
- Verify authority — make sure each signer is authorized to bind their organization
- Keep a copy — executed copies should be filed in ~~cloud storage or ~~CLM immediately after execution
