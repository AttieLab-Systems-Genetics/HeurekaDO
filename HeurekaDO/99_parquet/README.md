# 99_parquet — High-Performance Columnar Storage Layer

This directory contains Snappy-compressed, columnar Apache Parquet conversions of the primary matrices in `01_Datasets/`, `02_Genetic_results/`, and `03_Reference/`.

The Parquet architecture drastically reduces I/O latency, minimizes disk footprint, and enables zero-copy partition pruning and predicate pushdown queries across large-scale systems genetics data.

## Directory Structure

```
99_parquet/
├── feature_dictionary.parquet    # Fast lookup table for unified feature keys
├── 01_Datasets/                  # High-dimensional expression & phenotype tables
│   ├── B6_BTBR_F2/               # 5-tissue int2 & mlratio expression matrices
│   ├── B6_BTBR_timecourse/       # Longitudinal ANOVA and timecourse matrices
│   ├── DO500_HFHS/               # Multi-tissue DO500 transcriptomic matrices
│   ├── DO1200_HF_HS/             # DO1200 liver transcriptomics & metabolomics
│   ├── Founders_DO500_HFHS/      # Founder strain expression & phenotype tables
│   └── Founders_DO1200_HF_HS/    # Founder diet study liver RNA VSD tables
├── 02_Genetic_results/           # Genetic mapping results
│   ├── do500/                    # DO500 QTL peak tables
│   ├── do1200/                   # DO1200 QTL peak tables
│   ├── mediation/                # bmediatR mediation tables
│   └── variants/                 # High/moderate impact candidate variant tables
└── 03_Reference/                 # Proteomic reference tables
    └── Liver proteomics in founder diet study unaware of coding variants Gygi_HEUREKA.parquet
```

## Analytical Query Patterns

Parquet files can be directly queried in place without ingesting multi-gigabyte CSVs into memory:

### R (`arrow` / `duckdb`)
```r
library(arrow)
library(dplyr)

# Query expression for specific genes without reading the full matrix
expr_ds <- open_dataset("99_parquet/01_Datasets/DO500_HFHS/expression/")
target_data <- expr_ds %>%
  filter(gene_id %in% c("ENSMUSG00000020122", "ENSMUSG00000030500")) %>%
  collect()
```

### Python (`duckdb` / `polars`)
```python
import duckdb

# SQL query with predicate pushdown directly over Parquet
con = duckdb.connect()
peaks_df = con.execute("""
    SELECT trait, chr, pos, lod
    FROM '99_parquet/02_Genetic_results/do500/*.parquet'
    WHERE lod > 7.5
""").df()
```
