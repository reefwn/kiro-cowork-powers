---
name: "bio-research"
displayName: "Bio-Research"
description: "Connect to preclinical research tools and databases (literature search, genomics analysis, target prioritization) to accelerate early-stage life sciences R&D. Works with your existing tools or standalone."
keywords: ["literature search", "PubMed", "bioRxiv", "single-cell", "scRNA-seq", "QC", "scvi-tools", "nextflow", "nf-core", "RNA-seq", "variant calling", "ATAC-seq", "drug discovery", "drug targets", "clinical trials", "ChEMBL", "Open Targets", "Allotrope", "instrument data", "scientific illustration", "BioRender", "research strategy", "problem selection", "genomics", "sequencing", "bioinformatics"]
author: "reefwn"
---

# Onboarding

## Step 1: Check environment

Look for existing research context:
- Data files (.h5ad, .h5, .fastq, .csv)
- Existing analysis scripts or notebooks
- Pipeline configurations (nextflow.config)
- Lab instrument output files

## Step 2: Gather researcher context

Ask the user:
```
To personalize your bio-research workflows, I'd like to know:
1. Your name and role (e.g., grad student, postdoc, PI)
2. Your research area (e.g., oncology, neuroscience, immunology)
3. Your primary data types (e.g., scRNA-seq, bulk RNA-seq, WGS, ATAC-seq)
4. Your model organisms (e.g., human, mouse, zebrafish)
5. Any specific tools or databases you regularly use
```

Store responses for use across all workflows.

## Step 3: Report readiness

```
Bio-Research power ready. Available workflows:
- /start — Check connected tools and explore available capabilities
- /literature — Search biomedical literature and preprints
- /single-cell-qc — Quality control for scRNA-seq data
- /scvi — Deep learning single-cell analysis (scVI, scANVI, totalVI, etc.)
- /nextflow — Run nf-core pipelines (RNA-seq, WGS/WES, ATAC-seq)
- /instrument-convert — Convert lab instrument data to Allotrope format
- /drug-discovery — Search compounds, targets, and clinical trials
- /research-strategy — Scientific problem selection framework

Steering files loaded automatically when relevant.
```

# Connectors

This power uses tool categories as placeholders. Any MCP server in that category works.

| Category | Placeholder | Examples |
|----------|-------------|----------|
| Literature | ~~literature | PubMed, bioRxiv, Google Scholar, Semantic Scholar |
| Scientific illustration | ~~scientific illustration | BioRender |
| Clinical trials | ~~clinical trials | ClinicalTrials.gov, EU Clinical Trials Register |
| Chemical database | ~~chemical database | ChEMBL, PubChem, DrugBank |
| Drug targets | ~~drug targets | Open Targets, UniProt, STRING |
| Data repository | ~~data repository | Synapse, Zenodo, Dryad, Figshare |
| Journal access | ~~journal access | Wiley Scholar Gateway, Elsevier, Springer Nature |
| AI research | ~~AI research | Owkin |
| Lab platform | ~~lab platform | Benchling |

# When to Load Steering Files

- Running `/start` or first getting oriented with the plugin → `start.md`
- Running `/literature` or searching for papers, preprints, publications → `literature-review.md`
- Running `/single-cell-qc` or asking about scRNA-seq quality control → `single-cell-rna-qc.md`
- Running `/scvi` or mentioning scVI, scANVI, totalVI, PeakVI, batch correction → `scvi-tools.md`
- Running `/nextflow` or asking about nf-core, RNA-seq, variant calling, ATAC-seq pipelines → `nextflow-pipelines.md`
- Running `/instrument-convert` or converting lab instrument data to Allotrope → `instrument-data-to-allotrope.md`
- Running `/drug-discovery` or searching compounds, drug targets, clinical trials → `drug-discovery.md`
- Running `/research-strategy` or asking about research problem selection, project ideation → `scientific-problem-selection.md`

# Credits

Ported from [Anthropic's Claude Cowork plugins](https://github.com/anthropics/knowledge-work-plugins) by [@reefwn](https://github.com/reefwn).
