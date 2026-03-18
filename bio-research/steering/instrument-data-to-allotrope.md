# Instrument Data to Allotrope

Convert laboratory instrument output files (PDF, CSV, Excel, TXT) to Allotrope Simple Model (ASM) JSON format or flattened 2D CSV.

## Workflow

1. **Detect instrument type** from file contents (auto-detect or user-specified)
2. **Parse file** using allotropy library (native) or flexible fallback parser
3. **Generate outputs:** ASM JSON, flattened CSV, and/or Python parser code
4. **Validate and deliver** with summary and usage instructions

## Quick Start

```python
pip install allotropy pandas openpyxl pdfplumber
from allotropy.parser_factory import Vendor
from allotropy.to_allotrope import allotrope_from_file
asm = allotrope_from_file("instrument_data.csv", Vendor.BECKMAN_VI_CELL_BLU)
```

## Supported Instruments

| Category | Instruments |
|----------|-------------|
| Cell Counting | Vi-CELL BLU, Vi-CELL XR, NucleoCounter |
| Spectrophotometry | NanoDrop One/Eight/8000, Lunatic |
| Plate Readers | SoftMax Pro, EnVision, Gen5, CLARIOstar |
| ELISA | SoftMax Pro, BMG MARS, MSD Workbench |
| qPCR | QuantStudio, Bio-Rad CFX |
| Chromatography | Empower, Chromeleon |

## Detection & Parsing Strategy

1. **Tier 1: Native allotropy parsing (preferred)** — Always try allotropy first
2. **Tier 2: Flexible fallback** — Only if allotropy doesn't support the instrument
3. **Tier 3: PDF extraction** — For PDF-only files, extract tables with pdfplumber

## Calculated Data Handling

Separate raw measurements from calculated/derived values:
- **Raw data** → `measurement-document`
- **Calculated data** → `calculated-data-aggregate-document` (must include traceability)

## Validation

```bash
python scripts/validate_asm.py output.json
python scripts/validate_asm.py output.json --reference known_good.json
python scripts/validate_asm.py output.json --strict
```

## Code Export for Data Engineers

```bash
python scripts/export_parser.py --input "data.csv" --vendor "VI_CELL_BLU" --output "parser_script.py"
```

Generates standalone Python scripts with no external dependencies beyond pandas/allotropy.
