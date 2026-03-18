# scvi-tools Deep Learning

Deep learning for single-cell analysis using scvi-tools.

## When to Use

- scvi-tools, scVI, scANVI, or related models mentioned
- Deep learning-based batch correction or integration needed
- Multi-modal data (CITE-seq, multiome)
- Reference mapping or label transfer required
- ATAC-seq or spatial transcriptomics analysis
- Learning latent representations of single-cell data

## Model Selection Guide

| Data Type | Model | Primary Use Case |
|-----------|-------|------------------|
| scRNA-seq | scVI | Unsupervised integration, DE, imputation |
| scRNA-seq + labels | scANVI | Label transfer, semi-supervised integration |
| CITE-seq (RNA+protein) | totalVI | Multi-modal integration, protein denoising |
| scATAC-seq | PeakVI | Chromatin accessibility analysis |
| Multiome (RNA+ATAC) | MultiVI | Joint modality analysis |
| Spatial + scRNA reference | DestVI | Cell type deconvolution |
| RNA velocity | veloVI | Transcriptional dynamics |
| Cross-technology | sysVI | System-level batch correction |

## Quick Decision Tree

```
Need to integrate scRNA-seq data?
├── Have cell type labels? → scANVI
└── No labels? → scVI

Have multi-modal data?
├── CITE-seq (RNA + protein)? → totalVI
├── Multiome (RNA + ATAC)? → MultiVI
└── scATAC-seq only? → PeakVI

Have spatial data?
└── Need cell type deconvolution? → DestVI

Have pre-trained reference model?
└── Map query to reference? → scArches

Need RNA velocity?
└── veloVI
```

## Critical Requirements

1. **Raw counts required** — scvi-tools models need integer count data
   ```python
   adata.layers["counts"] = adata.X.copy()
   scvi.model.SCVI.setup_anndata(adata, layer="counts")
   ```

2. **HVG selection** — Use 2000-4000 highly variable genes
   ```python
   sc.pp.highly_variable_genes(adata, n_top_genes=2000, batch_key="batch", layer="counts", flavor="seurat_v3")
   adata = adata[:, adata.var['highly_variable']].copy()
   ```

3. **Batch information** — Specify batch_key for integration
   ```python
   scvi.model.SCVI.setup_anndata(adata, layer="counts", batch_key="batch")
   ```

## Example Workflow

```bash
# 1. Validate input data
python scripts/validate_adata.py raw.h5ad --batch-key batch --suggest
# 2. Prepare data (QC, HVG selection)
python scripts/prepare_data.py raw.h5ad prepared.h5ad --batch-key batch --n-hvgs 2000
# 3. Train model
python scripts/train_model.py prepared.h5ad results/ --model scvi --batch-key batch
# 4. Cluster and visualize
python scripts/cluster_embed.py results/adata_trained.h5ad results/ --resolution 0.8
# 5. Differential expression
python scripts/differential_expression.py results/model results/adata_clustered.h5ad results/de.csv --groupby leiden
```

## Key Resources

- [scvi-tools Documentation](https://docs.scvi-tools.org/)
- [scvi-tools Tutorials](https://docs.scvi-tools.org/en/stable/tutorials/index.html)
- [Model Hub](https://huggingface.co/scvi-tools)
