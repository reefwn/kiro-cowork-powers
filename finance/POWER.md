---
name: "finance"
displayName: "Finance"
description: "Streamline finance and accounting workflows, from journal entries and reconciliation to financial statements and variance analysis. Speed up audit prep, month-end close, and keeping your books clean."
keywords: ["journal entry", "reconciliation", "income statement", "P&L", "variance analysis", "flux", "SOX", "audit", "month-end close", "accrual", "depreciation", "prepaid", "payroll", "revenue recognition", "deferred revenue", "balance sheet", "cash flow", "GAAP", "financial statements", "budget vs actual"]
author: "reefwn"
---

> **Important**: This power assists with finance and accounting workflows but does not provide financial, tax, or audit advice. All outputs should be reviewed by qualified financial professionals before use in financial reporting, regulatory filings, or audit documentation.

# Onboarding

## Step 1: Check environment

Look for existing finance context:
- ERP or accounting system connections
- Data warehouse access for financial queries
- Existing close calendars, reconciliation templates, or workpapers

## Step 2: Gather team context

Ask the user:
```
To personalize your finance workflows, I'd like to know:
1. Your name and role (e.g., Staff Accountant, Controller, FP&A Analyst)
2. Your company name and entity structure
3. Your ERP/accounting system (e.g., NetSuite, SAP, QuickBooks, Xero)
4. Your fiscal year end
5. Your typical close timeline (e.g., 5-day close, 3-day close)
6. Your materiality thresholds for variance analysis
```

Store responses for use across all workflows.

## Step 3: Report readiness

```
Finance power ready. Available workflows:
- /journal-entry — Prepare journal entries with debits, credits, and supporting detail
- /reconciliation — Reconcile GL to subledger, bank, or third-party balances
- /income-statement — Generate P&L with period-over-period comparison and variance analysis
- /variance-analysis — Decompose variances into drivers with narrative explanations
- /sox-testing — Generate SOX sample selections, testing workpapers, and control assessments

Skills loaded automatically when relevant:
journal-entry-prep, reconciliation, financial-statements, variance-analysis, close-management, audit-support
```

# Connectors

This power uses tool categories as placeholders. Any MCP server in that category works.

| Category | Placeholder | Examples |
|----------|-------------|----------|
| Data warehouse | ~~data warehouse | Snowflake, Databricks, BigQuery, Redshift, PostgreSQL |
| Email | ~~email | Microsoft 365, Gmail |
| Office suite | ~~office suite | Microsoft 365 |
| Chat | ~~chat | Slack, Microsoft Teams |
| ERP / Accounting | ~~erp | NetSuite, SAP, QuickBooks, Xero |
| Analytics / BI | ~~analytics | Tableau, Looker, Power BI |

# When to Load Steering Files

- Running `/journal-entry` or preparing accruals, depreciation, prepaids, payroll, or revenue entries → `journal-entry.md`
- Running `/reconciliation` or reconciling accounts → `reconciliation.md`
- Running `/income-statement` or generating P&L reports → `income-statement.md`
- Running `/variance-analysis` or analyzing budget vs actual, period-over-period changes → `variance-analysis.md`
- Running `/sox-testing` or preparing audit workpapers and sample selections → `sox-testing.md`
- Preparing journal entries, reviewing entry types, or checking documentation requirements → `journal-entry-prep.md`
- Performing reconciliations, categorizing reconciling items, or aging analysis → `reconciliation-skill.md`
- Generating or formatting financial statements, GAAP presentation, or flux analysis → `financial-statements.md`
- Decomposing variances, setting materiality thresholds, or writing variance narratives → `variance-analysis-skill.md`
- Managing month-end close, task sequencing, or tracking close progress → `close-management.md`
- SOX 404 testing methodology, sample selection, deficiency classification, or audit prep → `audit-support.md`

# Credits

Ported from [Anthropic's Claude Cowork plugins](https://github.com/anthropics/knowledge-work-plugins) by [@reefwn](https://github.com/reefwn).
