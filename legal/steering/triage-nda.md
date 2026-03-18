# /triage-nda

Rapidly triage an incoming NDA and classify it as GREEN (standard approval), YELLOW (counsel review), or RED (full legal review).

## Usage

```
/triage-nda
```

Accepts: file upload, URL, or pasted NDA text.

## Workflow

### 1. Accept the NDA

Accept the NDA as a file upload (PDF, DOCX), URL, or pasted text. If none provided, prompt the user.

### 2. Load NDA Playbook

Look for NDA screening criteria in local settings (e.g., `legal.local.md`). If no playbook is configured, proceed with market-standard defaults:
- Mutual obligations required
- Term: 2-3 years standard, up to 5 years for trade secrets
- Standard carveouts: independently developed, publicly available, rightfully received from third party, required by law
- No non-solicitation or non-compete provisions
- Governing law in a reasonable commercial jurisdiction

### 3. Quick Screen

Evaluate against each criterion:

1. **Agreement Structure**: Type (mutual/unilateral), appropriate for context, standalone agreement
2. **Definition of Confidential Information**: Reasonable scope, marking requirements, exclusions present
3. **Obligations**: Standard of care, use restriction, disclosure restriction
4. **Standard Carveouts**: Public knowledge, prior possession, independent development, third-party receipt, legal compulsion
5. **Permitted Disclosures**: Employees, contractors/advisors, affiliates, legal/regulatory
6. **Term and Duration**: Reasonable agreement term, survival period, not perpetual
7. **Return and Destruction**: Triggered on termination, retention exception for legal/compliance
8. **Remedies**: Injunctive relief acknowledgment, no liquidated damages, not one-sided
9. **Problematic Provisions**: Non-solicitation, non-compete, exclusivity, standstill, broad residuals, IP assignment, audit rights
10. **Governing Law**: Reasonable jurisdiction, consistent, no mandatory arbitration

### 4. Classify

**GREEN — Standard Approval**: All criteria pass. Mutual NDA, all carveouts present, standard term, no problematic provisions. Route for signature via standard delegation.

**YELLOW — Counsel Review**: Minor issues present but NDA is not fundamentally problematic. Broader-than-preferred definition, longer term, missing one carveout, narrowly scoped residuals, non-preferred jurisdiction. Counsel can resolve in a single review pass.

**RED — Significant Issues**: Unilateral when mutual required, missing critical carveouts, non-solicitation/non-compete embedded, exclusivity/standstill, unreasonable term (10+ years or perpetual), overbroad definition, broad residuals, IP assignment, liquidated damages, unfavorable jurisdiction with mandatory arbitration, or document is not actually an NDA.

### 5. Generate Triage Report

```
## NDA Triage Report

**Classification**: [GREEN / YELLOW / RED]
**Parties**: [party names]
**Type**: [Mutual / Unilateral (disclosing) / Unilateral (receiving)]
**Term**: [duration]
**Governing Law**: [jurisdiction]
**Review Basis**: [Playbook / Default Standards]

## Screening Results

| Criterion | Status | Notes |
|-----------|--------|-------|
| Mutual Obligations | [PASS/FLAG/FAIL] | [details] |
| Definition Scope | [PASS/FLAG/FAIL] | [details] |
| Term | [PASS/FLAG/FAIL] | [details] |
| Standard Carveouts | [PASS/FLAG/FAIL] | [details] |
| ... | | |

## Issues Found

### [Issue 1 — YELLOW/RED]
**What**: [description]
**Risk**: [what could go wrong]
**Suggested Fix**: [specific language or approach]

## Recommendation
[Specific next step: approve, send for review, or reject/counter]

## Next Steps
1. [Action item 1]
2. [Action item 2]
```

### 6. Routing Suggestion

| Classification | Recommended Action | Typical Timeline |
|---|---|---|
| GREEN | Approve and route for signature | Same day |
| YELLOW | Send to reviewer with specific issues flagged | 1-2 business days |
| RED | Engage counsel for full review; prepare counterproposal | 3-5 business days |

## Notes

- If the document is not actually an NDA (contains substantive commercial terms), flag as RED immediately
- For NDAs that are part of a larger agreement, note that the broader context may affect analysis
- Always note this is a screening tool and counsel should review uncertain items
