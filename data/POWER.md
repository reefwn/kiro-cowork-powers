---
name: "data"
displayName: "Data"
description: "Write SQL, explore datasets, and generate insights faster. Build visualizations and dashboards, and turn raw data into clear stories for stakeholders."
keywords: ["SQL", "query", "data", "dataset", "explore", "analyze", "visualization", "chart", "dashboard", "KPI", "metrics", "warehouse", "Snowflake", "BigQuery", "Databricks", "Redshift", "PostgreSQL", "cohort", "funnel", "retention", "trend", "distribution", "validate", "data quality", "profiling"]
author: "reefwn"
---

# Onboarding

## Step 1: Check environment

Look for existing data context:
- Data warehouse connections (Snowflake, BigQuery, Databricks, Redshift, PostgreSQL)
- Existing SQL files, notebooks, or analysis scripts
- BI tool configurations or dashboard definitions
- Data dictionaries or schema documentation

## Step 2: Gather team context

Ask the user:
```
To personalize your data workflows, I'd like to know:
1. Your name and role (e.g., Data Analyst, Analytics Engineer, Data Scientist)
2. Your company name
3. Your data warehouse / SQL dialect (e.g., Snowflake, BigQuery, PostgreSQL)
4. Your key data domains (e.g., product analytics, marketing, finance, operations)
5. Any BI tools you use (e.g., Looker, Tableau, Hex, Amplitude)
```

Store responses for use across all workflows.

## Step 3: Report readiness

```
Data power ready. Available workflows:
- /analyze — Answer data questions — from quick lookups to full analyses
- /explore-data — Profile and explore a dataset to understand its shape, quality, and patterns
- /write-query — Write optimized SQL for your dialect with best practices
- /create-viz — Create publication-quality visualizations with Python
- /build-dashboard — Build interactive HTML dashboards with filters and charts
- /validate — QA an analysis before sharing — methodology, accuracy, and bias checks

Skills loaded automatically when relevant:
sql-queries, data-visualization, statistical-analysis
```

# Connectors

This power uses tool categories as placeholders. Any MCP server in that category works.

| Category | Placeholder | Examples |
|----------|-------------|----------|
| Data warehouse | ~~data warehouse | Snowflake, Databricks, BigQuery, Redshift, PostgreSQL |
| Notebook | ~~notebook | Hex, Jupyter, Deepnote, Observable |
| Product analytics | ~~product analytics | Amplitude, Mixpanel, Heap |
| Project tracker | ~~project tracker | Atlassian (Jira/Confluence), Linear, Asana |

# When to Load Steering Files

- Running `/analyze` or asking a data question, looking up a metric, or investigating a trend → `analyze.md`
- Running `/explore-data` or profiling a table, checking data quality, or discovering patterns → `explore-data.md`
- Running `/write-query` or asking to write, optimize, or translate SQL → `write-query.md`
- Running `/create-viz` or asking to create a chart, plot, or visualization → `create-viz.md`
- Running `/build-dashboard` or asking to build an interactive dashboard or report → `build-dashboard.md`
- Running `/validate` or reviewing an analysis before sharing with stakeholders → `validate-data.md`
- Writing or optimizing SQL across any dialect, using window functions, CTEs, or common patterns → `sql-queries.md`
- Creating charts, selecting chart types, or applying visualization design principles → `data-visualization.md`
- Applying statistical methods, trend analysis, outlier detection, or hypothesis testing → `statistical-analysis.md`

# Credits

Ported from [Anthropic's Claude Cowork plugins](https://github.com/anthropics/knowledge-work-plugins) by [@reefwn](https://github.com/reefwn).
