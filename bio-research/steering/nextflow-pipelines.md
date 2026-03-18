# Nextflow Pipelines

Run nf-core bioinformatics pipelines on local or public sequencing data.

## Supported Pipelines

| Data Type | Pipeline | Version | Goal |
|-----------|----------|---------|------|
| RNA-seq | `rnaseq` | 3.22.2 | Gene expression |
| WGS/WES | `sarek` | 3.7.1 | Variant calling |
| ATAC-seq | `atacseq` | 2.1.2 | Chromatin accessibility |

## Workflow Checklist

```
- [ ] Step 0: Acquire data (if from GEO/SRA)
- [ ] Step 1: Environment check (MUST pass)
- [ ] Step 2: Select pipeline (confirm with user)
- [ ] Step 3: Run test profile (MUST pass)
- [ ] Step 4: Create samplesheet
- [ ] Step 5: Configure & run (confirm genome with user)
- [ ] Step 6: Verify outputs
```

## Step 0: Acquire Data (GEO/SRA Only)

Skip if user has local FASTQ files.

```bash
python scripts/sra_geo_fetch.py info GSE110004
python scripts/sra_geo_fetch.py download GSE110004 -o ./fastq -i
python scripts/sra_geo_fetch.py samplesheet GSE110004 --fastq-dir ./fastq -o samplesheet.csv
```

## Step 1: Environment Check

```bash
python scripts/check_environment.py
```

All critical checks must pass (Docker, Nextflow ≥23.04, Java ≥11).

## Step 2: Select Pipeline

Auto-detect from data:
```bash
python scripts/detect_data_type.py /path/to/data
```

**Confirm with user before proceeding.**

## Step 3: Run Test Profile

```bash
nextflow run nf-core/<pipeline> -r <version> -profile test,docker --outdir test_output
```

Verify: `ls test_output/multiqc/multiqc_report.html`

## Step 4: Create Samplesheet

```bash
python scripts/generate_samplesheet.py /path/to/data -o samplesheet.csv
```

**Samplesheet formats:**
- rnaseq: `sample,fastq_1,fastq_2,strandedness`
- sarek: `patient,sample,lane,fastq_1,fastq_2,status`
- atacseq: `sample,fastq_1,fastq_2,replicate`

## Step 5: Configure & Run

**Confirm with user:** genome, aligner (rnaseq), tools (sarek), read_length (atacseq).

```bash
nextflow run nf-core/<pipeline> \
  -r <version> -profile docker \
  --input samplesheet.csv --outdir results \
  --genome <genome> -resume
```

Common genomes: GRCh38 (human), GRCm39 (mouse), R64-1-1 (yeast)

## Step 6: Verify Outputs

```bash
ls results/multiqc/multiqc_report.html
grep "Pipeline completed successfully" .nextflow.log
```

**Key outputs:**
- rnaseq: `results/star_salmon/salmon.merged.gene_counts.tsv`
- sarek: `results/variant_calling/*/` (VCF files)
- atacseq: `results/macs2/narrowPeak/` (peak calls)
