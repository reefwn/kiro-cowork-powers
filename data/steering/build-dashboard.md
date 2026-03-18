# /build-dashboard

Build a self-contained interactive HTML dashboard with charts, filters, tables, and professional styling. Opens directly in a browser — no server or dependencies required.

## Usage

```
/build-dashboard [data source]
```

## How It Works

```
┌─────────────────────────────────────────────────────────────────┐
│ BUILD DASHBOARD                                                 │
├─────────────────────────────────────────────────────────────────┤
│ STANDALONE (always works)                                       │
│ ✓ Paste data or upload CSV for dashboard generation             │
│ ✓ Create from description with sample data                     │
│ ✓ Self-contained HTML file — no server needed                   │
│ ✓ Interactive Chart.js charts, filters, sortable tables         │
├─────────────────────────────────────────────────────────────────┤
│ SUPERCHARGED (when you connect your tools)                      │
│ + Data warehouse: Query data and embed results directly         │
│ + Notebook: Generate dashboard from notebook outputs            │
└─────────────────────────────────────────────────────────────────┘
```

## Workflow

### 1. Understand Requirements

Determine:
- **Purpose**: Executive overview, operational monitoring, deep-dive analysis, team reporting
- **Audience**: Who will use this dashboard?
- **Key metrics**: What numbers matter most?
- **Dimensions**: What should users be able to filter or slice by?
- **Data source**: Live query, pasted data, CSV file, or sample data

### 2. Gather the Data

If **~~data warehouse** is connected:
1. Query the necessary data
2. Embed the results as JSON within the HTML file

If data is pasted or uploaded:
1. Parse and clean the data
2. Embed as JSON in the dashboard

If working from a description without data:
1. Create a realistic sample dataset
2. Note in the dashboard that it uses sample data
3. Provide instructions for swapping in real data

### 3. Design the Layout

```
┌──────────────────────────────────────────────────┐
│ Dashboard Title                    [Filters ▼]   │
├────────────┬────────────┬────────────┬───────────┤
│ KPI Card   │ KPI Card   │ KPI Card   │ KPI Card  │
├────────────┴────────────┼────────────┴───────────┤
│ Primary Chart           │ Secondary Chart        │
│ (largest area)          │                        │
├─────────────────────────┴────────────────────────┤
│ Detail Table (sortable, scrollable)              │
└──────────────────────────────────────────────────┘
```

- 2-4 KPI cards at the top for headline numbers
- 1-3 charts in the middle for trends and breakdowns
- Optional detail table at the bottom for drill-down data
- Filters in the header or sidebar

### 4. Build the HTML Dashboard

Generate a single self-contained HTML file including:

**Structure (HTML):** Semantic HTML5, responsive grid, filter controls, KPI cards, chart containers, data table with sortable headers.

**Styling (CSS):** Professional color scheme, card-based layout with subtle shadows, consistent typography (system fonts), responsive design, print-friendly styles.

**Interactivity (JavaScript):** Chart.js for interactive charts (via CDN), filter dropdowns that update all charts and tables simultaneously, sortable table columns, hover tooltips, number formatting.

**Data (embedded JSON):** All data embedded directly as JavaScript variables. No external data fetches. Works completely offline.

### 5. Chart Types

Use Chart.js for all charts:
- **Line chart**: Time series trends
- **Bar chart**: Category comparisons
- **Doughnut chart**: Composition (when <6 categories)
- **Stacked bar**: Composition over time
- **Mixed (bar + line)**: Volume with rate overlay

### 6. Data Size Guidelines

| Data Size | Approach |
|---|---|
| <1,000 rows | Embed directly. Full interactivity. |
| 1,000 - 10,000 rows | Embed in HTML. May need to pre-aggregate for charts. |
| 10,000 - 100,000 rows | Pre-aggregate server-side. Embed only aggregated data. |
| >100,000 rows | Not suitable for client-side dashboard. Use a BI tool. |

### 7. Save and Open

1. Save as HTML file with descriptive name (e.g., `sales_dashboard.html`)
2. Open in the user's default browser
3. Confirm it renders correctly
4. Provide instructions for updating data or customizing

## Tips

- Dashboards are fully self-contained HTML files — share by sending the file.
- For real-time dashboards, consider a BI tool instead. These are point-in-time snapshots.
- Request "dark mode" or "presentation mode" for different styling.
- You can request a specific color scheme to match your brand.
