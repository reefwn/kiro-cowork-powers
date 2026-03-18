# Single-Cell RNA-seq Quality Control

Automated QC workflow for scRNA-seq data following scverse best practices.

## When to Use

- User requests QC on single-cell RNA-seq data
- Filtering low-quality cells or assessing data quality
- Need QC visualizations or metrics
- Following scverse/scanpy best practices
- MAD-based filtering or outlier detection

**Supported formats:** `.h5ad` (AnnData), `.h5` (10X Genomics Cell Ranger)

## Approach 1: Complete QC Pipeline (Recommended)

For standard QC, use the convenience script:
```bash
python3 scripts/qc_analysis.py input.h5ad
# or for 10X .h5 files:
python3 scripts/qc_analysis.py raw_feature_bc_matrix.h5
```

**Parameters:**
- `--output-dir` — Output directory
- `--mad-counts`, `--mad-genes`, `--mad-mt` — MAD thresholds
- `--mt-threshold` — Hard mitochondrial % cutoff
- `--min-cells` — Gene filtering threshold
- `--mt-pattern`, `--ribo-pattern`, `--hb-pattern` — Gene name patterns for different species

**Outputs** (saved to `_qc_results/`):
- `qc_metrics_before_filtering.png` — Pre-filtering visualizations
- `qc_filtering_thresholds.png` — MAD-based threshold overlays
- `qc_metrics_after_filtering.png` — Post-filtering quality metrics
- `_filtered.h5ad` — Clean, filtered dataset
- `_with_qc.h5ad` — Original data with QC annotations

### Pipeline Steps
1. Calculate QC metrics — count depth, gene detection, MT/ribo/hemoglobin content
2. Apply MAD-based filtering — permissive outlier detection
3. Filter genes — remove genes detected in few cells
4. Generate visualizations — before/after plots with threshold overlays

## Approach 2: Modular Building Blocks (Custom Workflows)

For non-standard requirements, use modular utility functions:
```python
import anndata as ad
from qc_core import calculate_qc_metrics, detect_outliers_mad, filter_cells
from qc_plotting import plot_qc_distributions

adata = ad.read_h5ad('input.h5ad')
calculate_qc_metrics(adata, inplace=True)
# ... custom analysis logic
```

**Available functions from `qc_core.py`:**
- `calculate_qc_metrics()` — Calculate and annotate QC metrics
- `detect_outliers_mad()` — MAD-based outlier detection
- `apply_hard_threshold()` — Apply hard cutoffs
- `filter_cells()` / `filter_genes()` — Apply filters
- `print_qc_summary()` — Print summary statistics

**Available functions from `qc_plotting.py`:**
- `plot_qc_distributions()` — Comprehensive QC plots
- `plot_filtering_thresholds()` — Visualize filtering thresholds
- `plot_qc_after_filtering()` — Post-filtering plots

## Best Practices

1. Be permissive with filtering — retain most cells to avoid losing rare populations
2. Inspect visualizations — review before/after plots for biological sense
3. Consider dataset-specific factors — some tissues have higher MT content (neurons, cardiomyocytes)
4. Check gene annotations — MT prefixes vary by species (mt- mouse, MT- human)
5. Iterate if needed — adjust parameters based on experiment/tissue type

## Requirements

anndata, scanpy, scipy, matplotlib, seaborn, numpy
