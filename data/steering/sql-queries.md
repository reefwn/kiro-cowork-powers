# SQL Queries

Write correct, performant, readable SQL across all major data warehouse dialects.

## Dialect-Specific Reference

### PostgreSQL (including Aurora, RDS, Supabase, Neon)

**Date/time:**
```sql
CURRENT_DATE, CURRENT_TIMESTAMP, NOW()
date_column + INTERVAL '7 days'
DATE_TRUNC('month', created_at)
EXTRACT(YEAR FROM created_at)
TO_CHAR(created_at, 'YYYY-MM-DD')
```

**String functions:**
```sql
column ILIKE '%pattern%'          -- case-insensitive
column ~ '^regex_pattern$'        -- regex
SPLIT_PART(str, delimiter, position)
```

**Arrays and JSON:**
```sql
data->>'key'                      -- text
data->'nested'->'key'             -- json
ARRAY_AGG(column)
```

**Performance:** `EXPLAIN ANALYZE`, indexes on filtered/joined columns, `EXISTS` over `IN`, partial indexes.

### Snowflake

**Date/time:**
```sql
CURRENT_DATE(), CURRENT_TIMESTAMP()
DATEADD(day, 7, date_column)
DATEDIFF(day, start_date, end_date)
DATE_TRUNC('month', created_at)
```

**Semi-structured data:**
```sql
data:customer:name::STRING        -- VARIANT access
SELECT f.value FROM table, LATERAL FLATTEN(input => array_col) f
```

**Performance:** Clustering keys (not indexes), filter on clustering key columns, appropriate warehouse size.

### BigQuery (Google Cloud)

**Date/time:**
```sql
CURRENT_DATE(), CURRENT_TIMESTAMP()
DATE_ADD(date_column, INTERVAL 7 DAY)
DATE_DIFF(end_date, start_date, DAY)
DATE_TRUNC(created_at, MONTH)
FORMAT_DATE('%Y-%m-%d', date_column)
```

**String functions:**
```sql
LOWER(column) LIKE '%pattern%'    -- no ILIKE
REGEXP_CONTAINS(column, r'pattern')
SPLIT(str, delimiter)             -- returns ARRAY
```

**Performance:** Always filter on partition columns, use clustering, `APPROX_COUNT_DISTINCT()`, avoid `SELECT *` (billing is per-byte scanned).

### Redshift (Amazon)

**Date/time:**
```sql
CURRENT_DATE, GETDATE()
DATEADD(day, 7, date_column)
DATEDIFF(day, start_date, end_date)
DATE_TRUNC('month', created_at)
```

**Performance:** Distribution keys (DISTKEY) for collocated joins, sort keys (SORTKEY) for filtered columns, `ANALYZE` and `VACUUM` regularly.

### Databricks SQL

**Date/time:**
```sql
CURRENT_DATE(), CURRENT_TIMESTAMP()
DATE_ADD(date_column, 7)
DATEDIFF(end_date, start_date)
DATE_TRUNC('MONTH', created_at)
```

**Delta Lake features:**
```sql
SELECT * FROM my_table TIMESTAMP AS OF '2024-01-15'  -- time travel
MERGE INTO target USING source ON target.id = source.id
  WHEN MATCHED THEN UPDATE SET *
  WHEN NOT MATCHED THEN INSERT *
```

**Performance:** `OPTIMIZE` and `ZORDER`, Photon engine, `CACHE TABLE`.

## Common SQL Patterns

### Window Functions
```sql
ROW_NUMBER() OVER (PARTITION BY user_id ORDER BY created_at DESC)
SUM(revenue) OVER (ORDER BY date_col ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) as running_total
AVG(revenue) OVER (ORDER BY date_col ROWS BETWEEN 6 PRECEDING AND CURRENT ROW) as moving_avg_7d
LAG(value, 1) OVER (PARTITION BY entity ORDER BY date_col) as prev_value
revenue / SUM(revenue) OVER () as pct_of_total
```

### CTEs for Readability
```sql
WITH
base_users AS (
  SELECT user_id, created_at, plan_type
  FROM users
  WHERE created_at >= DATE '2024-01-01' AND status = 'active'
),
user_metrics AS (
  SELECT u.user_id, u.plan_type,
    COUNT(DISTINCT e.session_id) as session_count,
    SUM(e.revenue) as total_revenue
  FROM base_users u
  LEFT JOIN events e ON u.user_id = e.user_id
  GROUP BY u.user_id, u.plan_type
)
SELECT plan_type, COUNT(*) as user_count,
  AVG(session_count) as avg_sessions,
  SUM(total_revenue) as total_revenue
FROM user_metrics
GROUP BY plan_type
ORDER BY total_revenue DESC;
```

### Cohort Retention
```sql
WITH cohorts AS (
  SELECT user_id, DATE_TRUNC('month', first_activity_date) as cohort_month
  FROM users
),
activity AS (
  SELECT user_id, DATE_TRUNC('month', activity_date) as activity_month
  FROM user_activity
)
SELECT c.cohort_month, COUNT(DISTINCT c.user_id) as cohort_size,
  COUNT(DISTINCT CASE WHEN a.activity_month = c.cohort_month THEN a.user_id END) as month_0,
  COUNT(DISTINCT CASE WHEN a.activity_month = c.cohort_month + INTERVAL '1 month' THEN a.user_id END) as month_1,
  COUNT(DISTINCT CASE WHEN a.activity_month = c.cohort_month + INTERVAL '3 months' THEN a.user_id END) as month_3
FROM cohorts c
LEFT JOIN activity a ON c.user_id = a.user_id
GROUP BY c.cohort_month
ORDER BY c.cohort_month;
```

### Funnel Analysis
```sql
WITH funnel AS (
  SELECT user_id,
    MAX(CASE WHEN event = 'page_view' THEN 1 ELSE 0 END) as step_1_view,
    MAX(CASE WHEN event = 'signup_start' THEN 1 ELSE 0 END) as step_2_start,
    MAX(CASE WHEN event = 'signup_complete' THEN 1 ELSE 0 END) as step_3_complete,
    MAX(CASE WHEN event = 'first_purchase' THEN 1 ELSE 0 END) as step_4_purchase
  FROM events
  WHERE event_date >= CURRENT_DATE - INTERVAL '30 days'
  GROUP BY user_id
)
SELECT COUNT(*) as total_users,
  SUM(step_1_view) as viewed,
  SUM(step_2_start) as started_signup,
  SUM(step_3_complete) as completed_signup,
  SUM(step_4_purchase) as purchased,
  ROUND(100.0 * SUM(step_2_start) / NULLIF(SUM(step_1_view), 0), 1) as view_to_start_pct,
  ROUND(100.0 * SUM(step_3_complete) / NULLIF(SUM(step_2_start), 0), 1) as start_to_complete_pct,
  ROUND(100.0 * SUM(step_4_purchase) / NULLIF(SUM(step_3_complete), 0), 1) as complete_to_purchase_pct
FROM funnel;
```

### Deduplication
```sql
WITH ranked AS (
  SELECT *, ROW_NUMBER() OVER (PARTITION BY entity_id ORDER BY updated_at DESC) as rn
  FROM source_table
)
SELECT * FROM ranked WHERE rn = 1;
```

## Error Handling and Debugging

1. **Syntax errors**: Check dialect-specific syntax (`ILIKE` not in BigQuery, `SAFE_DIVIDE` only in BigQuery)
2. **Column not found**: Verify column names against schema — check typos, case sensitivity
3. **Type mismatches**: Cast explicitly (`CAST(col AS DATE)`, `col::DATE`)
4. **Division by zero**: Use `NULLIF(denominator, 0)`
5. **Ambiguous columns**: Always qualify with table alias in JOINs
6. **Group by errors**: All non-aggregated columns must be in GROUP BY (except BigQuery allows grouping by alias)
