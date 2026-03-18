# /explore-data

Profile and explore a dataset to understand its shape, quality, and patterns before diving into analysis.

## Usage

```
/explore-data
```

## How It Works

```
┌─────────────────────────────────────────────────────────────────┐
│ EXPLORE DATA                                                    │
├─────────────────────────────────────────────────────────────────┤
│ STANDALONE (always works)                                       │
│ ✓ Upload CSV, Excel, Parquet, or JSON for profiling             │
│ ✓ Describe a schema and get profiling query guidance            │
│ ✓ Data quality assessment and pattern discovery                 │
├─────────────────────────────────────────────────────────────────┤
│ SUPERCHARGED (when you connect your tools)                      │
│ + Data warehouse: Query live table metadata and run profiling   │
│ + Notebook: Execute profiling in connected environment          │
└─────────────────────────────────────────────────────────────────┘
```

## Workflow

### 1. Access the Data

If **~~data warehouse** is connected:
1. Resolve the table name (handle schema prefixes, suggest matches if ambiguous)
2. Query table metadata: column names, types, descriptions if available
3. Run profiling queries against the live data

If a file is provided (CSV, Excel, Parquet, JSON):
1. Read the file and load into a working dataset
2. Infer column types from the data

If neither:
1. Ask the user to provide a table name (with their warehouse connected) or upload a file

### 2. Understand Structure

**Table-level questions:**
- How many rows and columns?
- What is the grain (one row per what)?
- What is the primary key? Is it unique?
- When was the data last updated?
- How far back does the data go?

**Column classification** — categorize each column as:
- **Identifier**: Unique keys, foreign keys, entity IDs
- **Dimension**: Categorical attributes for grouping/filtering
- **Metric**: Quantitative values for measurement
- **Temporal**: Dates and timestamps
- **Text**: Free-form text fields
- **Boolean**: True/false flags
- **Structural**: JSON, arrays, nested structures

### 3. Generate Data Profile

**All columns:** Null count/rate, distinct count/cardinality ratio, most/least common values

**Numeric columns:**
```
min, max, mean, median (p50), standard deviation
percentiles: p1, p5, p25, p75, p95, p99
zero count, negative count (if unexpected)
```

**String columns:**
```
min/max/avg length, empty string count
pattern analysis, case consistency, leading/trailing whitespace
```

**Date/timestamp columns:**
```
min date, max date, null dates, future dates (if unexpected)
distribution by month/week, gaps in time series
```

### 4. Identify Data Quality Issues

- **High null rates**: >5% (warn), >20% (alert)
- **Cardinality surprises**: Low-cardinality columns that should be high, or vice versa
- **Suspicious values**: Negative amounts, future dates, placeholders ("N/A", "TBD", "test", "999999")
- **Duplicate detection**: Check natural key uniqueness
- **Distribution skew**: Extremely skewed distributions that could affect averages
- **Encoding issues**: Mixed case, trailing whitespace, inconsistent formats

### 5. Discover Relationships and Patterns

- Foreign key candidates linking to other tables
- Hierarchies (country > state > city)
- Correlations between numeric columns
- Derived or redundant columns

### 6. Recommend Follow-Up Analyses

Suggest 3-5 specific analyses:
- "Trend analysis on [metric] by [time_column] grouped by [dimension]"
- "Distribution deep-dive on [skewed_column] to understand outliers"
- "Data quality investigation on [problematic_column]"
- "Cohort analysis using [date_column] and [status_column]"

## Output

```markdown
## Data Profile: [table_name]

### Overview
- Rows: X,XXX,XXX
- Columns: XX (X dimensions, X metrics, X dates, X IDs)
- Date range: YYYY-MM-DD to YYYY-MM-DD

### Column Details
[summary table]

### Data Quality Issues
[flagged issues with severity]

### Recommended Explorations
[numbered list of suggested follow-up analyses]
```

## Quality Assessment Framework

### Completeness Score
- **Complete** (>99% non-null): Green
- **Mostly complete** (95-99%): Yellow — investigate the nulls
- **Incomplete** (80-95%): Orange — understand why
- **Sparse** (<80%): Red — may not be usable without imputation

### Consistency Checks
- Value format inconsistency ("USA", "US", "United States")
- Type inconsistency (numbers stored as strings)
- Referential integrity (foreign keys without parent records)
- Business rule violations (negative quantities, end dates before start dates)

### Accuracy Indicators
- Placeholder values (0, -1, 999999, "N/A", "TBD")
- Default value over-representation
- Stale data (no recent updates in active system)
- Impossible values (ages > 150, far-future dates)

## Tips

- For very large tables (100M+ rows), profiling queries use sampling by default — mention if you need exact counts.
- This command gives you the lay of the land before writing specific queries.
- Quality flags are heuristic — not every flag is a real problem, but each is worth a quick look.
