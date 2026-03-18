# Data Visualization

Chart selection guidance, Python visualization code patterns, design principles, and accessibility considerations.

## Chart Selection Guide

| What You're Showing | Best Chart | Alternatives |
|---|---|---|
| Trend over time | Line chart | Area chart (cumulative/composition) |
| Comparison across categories | Vertical bar chart | Horizontal bar (many categories), lollipop |
| Ranking | Horizontal bar chart | Dot plot, slope chart |
| Part-to-whole composition | Stacked bar chart | Treemap, waffle chart |
| Composition over time | Stacked area chart | 100% stacked bar |
| Distribution | Histogram | Box plot, violin plot, strip plot |
| Correlation (2 variables) | Scatter plot | Bubble chart (3rd variable as size) |
| Correlation (many variables) | Heatmap (correlation matrix) | Pair plot |
| Geographic patterns | Choropleth map | Bubble map |
| Flow / process | Sankey diagram | Funnel chart |
| Multiple KPIs at once | Small multiples | Dashboard with separate charts |

### When NOT to Use Certain Charts
- **Pie charts**: Avoid unless <6 categories. Humans are bad at comparing angles.
- **3D charts**: Never. They distort perception.
- **Dual-axis charts**: Use cautiously. Clearly label both axes.
- **Stacked bar (many categories)**: Hard to compare middle segments. Use small multiples instead.

## Python Code Patterns

### Setup and Style
```python
import matplotlib.pyplot as plt
import matplotlib.ticker as mticker
import seaborn as sns
import pandas as pd
import numpy as np

plt.style.use('seaborn-v0_8-whitegrid')
plt.rcParams.update({
    'figure.figsize': (10, 6), 'figure.dpi': 150,
    'font.size': 11, 'axes.titlesize': 14, 'axes.titleweight': 'bold',
})

PALETTE_CATEGORICAL = ['#4C72B0', '#DD8452', '#55A868', '#C44E52', '#8172B3', '#937860']
PALETTE_SEQUENTIAL = 'YlOrRd'
PALETTE_DIVERGING = 'RdBu_r'
```

### Number Formatting Helper
```python
def format_number(val, format_type='number'):
    if format_type == 'currency':
        if abs(val) >= 1e6: return f'${val/1e6:.1f}M'
        if abs(val) >= 1e3: return f'${val/1e3:.1f}K'
        return f'${val:,.0f}'
    elif format_type == 'percent':
        return f'{val:.1f}%'
    else:
        if abs(val) >= 1e6: return f'{val/1e6:.1f}M'
        if abs(val) >= 1e3: return f'{val/1e3:.1f}K'
        return f'{val:,.0f}'
```

## Design Principles

**Color:** Use color purposefully. Highlight the key insight with accent color; grey everything else. Use blue/orange as primary pair (colorblind-friendly). Max 6-8 categorical colors.

**Typography:** Title states the insight ("Revenue grew 23% YoY" not "Revenue by Month"). Readable axis labels (never rotated 90° if avoidable). Data labels on key points.

**Layout:** Remove chart junk (unnecessary gridlines, borders). Sort categories by value unless natural order exists. Appropriate aspect ratio (time series wider than tall).

**Accuracy:** Bar charts start at zero. Consistent scales across comparison panels. Show uncertainty when data is uncertain. Label your axes.

## Accessibility

- Never rely on color alone — add patterns, line styles, or direct labels
- Test with colorblind simulator; use `sns.color_palette("colorblind")`
- Include alt text describing the chart's key finding
- Minimum 10pt for labels, 12pt for titles
- Ensure chart works in black and white for printing
