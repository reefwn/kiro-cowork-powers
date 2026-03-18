# /write-query

Write a SQL query from a natural language description, optimized for your specific SQL dialect and following best practices.

## Usage

```
/write-query
```

## How It Works

```
┌─────────────────────────────────────────────────────────────────┐
│ WRITE QUERY                                                     │
├─────────────────────────────────────────────────────────────────┤
│ STANDALONE (always works)                                       │
│ ✓ Translate natural language to SQL                             │
│ ✓ Optimize for your specific SQL dialect                        │
│ ✓ CTE-based structure with comments and explanations            │
│ ✓ Performance notes and modification suggestions                │
├─────────────────────────────────────────────────────────────────┤
│ SUPERCHARGED (when you connect your tools)                      │
│ + Data warehouse: Discover schema, inspect columns, execute     │
│ + Notebook: Run query in connected notebook environment         │
└─────────────────────────────────────────────────────────────────┘
```

## Workflow

### 1. Understand the Request

Parse the user's description to identify:
- **Output columns**: What fields should the result include?
- **Filters**: What conditions limit the data?
- **Aggregations**: GROUP BY operations, counts, sums, averages?
- **Joins**: Does this require combining multiple tables?
- **Ordering**: How should results be sorted?
- **Limits**: Top-N or sample requirement?

### 2. Determine SQL Dialect

If not already known, ask which dialect:
- PostgreSQL (including Aurora, RDS, Supabase, Neon)
- Snowflake
- BigQuery (Google Cloud)
- Redshift (Amazon)
- Databricks SQL
- MySQL (including Aurora MySQL, PlanetScale)
- SQL Server (Microsoft)
- DuckDB / SQLite / Other

Remember the dialect for future queries in the same session.

### 3. Discover Schema (If Warehouse Connected)

If **~~data warehouse** is connected:
1. Search for relevant tables based on the user's description
2. Inspect column names, types, and relationships
3. Check for partitioning or clustering keys that affect performance
4. Look for pre-built views or materialized views

### 4. Write the Query

**Structure:**
- Use CTEs (WITH clauses) for readability when queries have multiple logical steps
- One CTE per logical transformation or data source
- Name CTEs descriptively (e.g., `daily_signups`, `active_users`, `revenue_by_product`)

**Performance:**
- Never use `SELECT *` in production queries — specify only needed columns
- Filter early (push WHERE clauses close to base tables)
- Use partition filters when available
- Prefer `EXISTS` over `IN` for large subqueries
- Use appropriate JOIN types
- Be mindful of exploding joins (many-to-many)

**Readability:**
- Add comments explaining the "why" for non-obvious logic
- Use consistent indentation and formatting
- Alias tables with meaningful short names

### 5. Present the Query

Provide:
1. The complete query in a SQL code block
2. Brief explanation of what each CTE or section does
3. Performance notes if relevant
4. Modification suggestions for common variations

### 6. Offer to Execute

If **~~data warehouse** is connected, offer to run the query and analyze the results.

## Tips

1. **Mention your dialect** upfront to get the right syntax immediately.
2. **Include table names** if you know them.
3. **Specify idempotency** if the query needs to be safe to re-run.
4. **Request parameterization** for recurring queries with date ranges.
