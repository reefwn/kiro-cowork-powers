# Statistical Analysis

Descriptive statistics, trend analysis, outlier detection, hypothesis testing, and guidance on when to be cautious about statistical claims.

## Descriptive Statistics

### Central Tendency

| Situation | Use | Why |
|---|---|---|
| Symmetric distribution, no outliers | Mean | Most efficient estimator |
| Skewed distribution | Median | Robust to outliers |
| Categorical or ordinal data | Mode | Only option for non-numeric |
| Highly skewed with outliers | Median + mean | The gap shows skew |

**Always report mean and median together for business metrics.** If they diverge significantly, the data is skewed and the mean alone is misleading.

### Percentiles for Business Context

Report key percentiles for a richer story:
```
p1:  Bottom 1% (floor)          p50: Median (typical user)
p5:  Low end of normal           p75: Third quartile
p25: First quartile              p90: Top 10% / power users
                                 p95: High end of normal
                                 p99: Top 1% / extreme users
```

### Describing Distributions

Characterize every numeric distribution: shape (normal, right-skewed, bimodal, heavy-tailed), center (mean and median gap), spread (standard deviation or IQR), outliers (count and severity), bounds (natural floor/ceiling).

## Trend Analysis

### Moving Averages
```python
df['ma_7d'] = df['metric'].rolling(window=7, min_periods=1).mean()
df['ma_28d'] = df['metric'].rolling(window=28, min_periods=1).mean()
```

### Period-over-Period Comparison
- **WoW**: Compare to same day last week
- **MoM**: Compare to same month prior
- **YoY**: Gold standard for seasonal businesses

### Growth Rates
```
Simple growth: (current - previous) / previous
CAGR: (ending / beginning) ^ (1 / years) - 1
```

### Seasonality Detection
1. Plot the raw time series — visual inspection first
2. Compute day-of-week averages for weekly patterns
3. Compute month-of-year averages for annual cycles
4. Always use YoY or same-period comparisons to avoid conflating trend with seasonality

## Outlier Detection

### Statistical Methods

**Z-score** (for normally distributed data):
```python
z_scores = (df['value'] - df['value'].mean()) / df['value'].std()
outliers = df[abs(z_scores) > 3]
```

**IQR method** (robust to non-normal distributions):
```python
Q1, Q3 = df['value'].quantile(0.25), df['value'].quantile(0.75)
IQR = Q3 - Q1
outliers = df[(df['value'] < Q1 - 1.5 * IQR) | (df['value'] > Q3 + 1.5 * IQR)]
```

### Handling Outliers

Do NOT automatically remove outliers. Instead:
1. **Investigate**: Data error, genuine extreme, or different population?
2. **Data errors**: Fix or remove
3. **Genuine extremes**: Keep but use robust statistics (median instead of mean)
4. **Different population**: Segment for separate analysis

**Always report what you did**: "We excluded 47 records (0.3%) with transaction amounts >$50K, which represent bulk enterprise orders analyzed separately."

## Hypothesis Testing

### When to Use

When you need to determine whether an observed difference is likely real or could be due to random chance: A/B test results, before/after comparisons, segment comparisons.

### Common Tests

| Scenario | Test |
|---|---|
| Compare two group means | t-test (independent) |
| Compare two group proportions | z-test for proportions |
| Compare paired measurements | Paired t-test |
| Compare 3+ group means | ANOVA |
| Non-normal data, two groups | Mann-Whitney U test |
| Association between categories | Chi-squared test |

### Practical vs. Statistical Significance

A difference can be statistically significant but practically meaningless (common with large samples). Always report:
- **Effect size**: How big is the difference?
- **Confidence interval**: Range of plausible true effects
- **Business impact**: What does this translate to in revenue, users, etc.?

## Cautions About Statistical Claims

- **Correlation ≠ Causation**: Consider reverse causation, confounding variables, coincidence
- **Multiple comparisons**: Testing 20 metrics at p=0.05 means ~1 will be falsely significant
- **Simpson's paradox**: Aggregated trend can reverse when segmented
- **Survivorship bias**: You can only analyze entities that "survived" to be in your dataset
- **Ecological fallacy**: Aggregate trends may not apply to individuals
- **False precision**: Prefer ranges ("4-6%") over point estimates ("4.73%")
