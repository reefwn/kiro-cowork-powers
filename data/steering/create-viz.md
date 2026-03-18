# /create-viz

Create publication-quality data visualizations using Python. Generates charts from data with best practices for clarity, accuracy, and design.

## Usage

```
/create-viz [chart type] [additional instructions]
```

## How It Works

```
┌─────────────────────────────────────────────────────────────────┐
│ CREATE VISUALIZATION                                            │
├─────────────────────────────────────────────────────────────────┤
│ STANDALONE (always works)                                       │
│ ✓ Paste data or upload CSV/Excel for charting                   │
│ ✓ Chart type recommendation based on data and question          │
│ ✓ Publication-quality matplotlib/seaborn output                 │
│ ✓ Interactive plotly charts on request                          │
├─────────────────────────────────────────────────────────────────┤
│ SUPERCHARGED (when you connect your tools)                      │
│ + Data warehouse: Query data and visualize in one step          │
│ + Notebook: Generate charts in connected notebook               │
└─────────────────────────────────────────────────────────────────┘
```

## Workflow

### 1. Understand the Request

Determine:
- **Data source**: Query results, pasted data, CSV/Excel file, or data to be queried
- **Chart type**: Explicitly requested or needs to be recommended
- **Purpose**: Exploration, presentation, report, dashboard component
- **Audience**: Technical team, executives, external stakeholders

### 2. Get the Data

If **~~data warehouse** is connected and data needs querying:
1. Write and execute the query
2. Load results into a pandas DataFrame

If data is pasted or uploaded:
1. Parse the data into a pandas DataFrame
2. Clean and prepare as needed

### 3. Select Chart Type

If the user didn't specify, recommend based on the data:

| Data Relationship | Recommended Chart |
|---|---|
| Trend over time | Line chart |
| Comparison across categories | Bar chart (horizontal if many categories) |
| Part-to-whole composition | Stacked bar or area chart (avoid pie unless <6 categories) |
| Distribution of values | Histogram or box plot |
| Correlation between two variables | Scatter plot |
| Geographic data | Choropleth map |
| Ranking | Horizontal bar chart |
| Matrix of relationships | Heatmap |

### 4. Generate the Visualization

Write Python code using:
- **matplotlib + seaborn**: Default for static, publication-quality charts
- **plotly**: For interactive charts (when user requests interactivity)

**Code requirements:**
```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

plt.style.use('seaborn-v0_8-whitegrid')
sns.set_palette("husl")

fig, ax = plt.subplots(figsize=(10, 6))
# [chart-specific code]

ax.set_title('Clear, Descriptive Title', fontsize=14, fontweight='bold')
ax.set_xlabel('X-Axis Label', fontsize=11)
ax.set_ylabel('Y-Axis Label', fontsize=11)

# Format numbers: '$1.2M' not '1200000', '45.2%' not '0.452'
ax.spines['top'].set_visible(False)
ax.spines['right'].set_visible(False)

plt.tight_layout()
plt.savefig('chart_name.png', dpi=150, bbox_inches='tight')
plt.show()
```

### 5. Apply Design Best Practices

**Color:** Use colorblind-friendly palette. Highlight key data with accent color. Grey out less important reference data.

**Typography:** Title states the insight ("Revenue grew 23% YoY" not "Revenue by Month"). Readable axis labels. Data labels on key points.

**Layout:** Appropriate whitespace. Legend doesn't obscure data. Categories sorted by value unless natural order exists.

**Accuracy:** Y-axis starts at zero for bar charts. No misleading axis breaks. Consistent scales when comparing panels.

### 6. Save and Present

1. Save the chart as a PNG file with descriptive name
2. Display the chart to the user
3. Provide the code used so they can modify it
4. Suggest variations (different chart type, different grouping, zoomed time range)

## Tips

- Mention "interactive" for plotly charts with hover, zoom, and filter.
- Specify "presentation" for larger fonts and higher contrast.
- You can request multiple charts at once (e.g., "create a 2x2 grid of charts showing...").
- Charts are saved to your current directory as PNG files.
