# HeurekaDO Discovery Platform & Data Architecture

This directory contains the central data repositories, manifests, multi-cohort expression profiling, genetic mapping results, reference proteomics, external knowledge bases, and high-performance Parquet storage for the **HeurekaDO** discovery platform.

See [AI Prompts](../prompts.md) for prompts used for this and other documents, and [Project Overview](../project.md) for biological background, cohort designs, and analytical workflows.
Dates of last documented change in parentheses (YYYY-MM-DD).

Detailed documentation for individual subfolders:

- [00_manifest/README.md](00_manifest/README.md): Master file registry, multi-million entry gene indexes, alias databases, and feature dictionaries.
  - [00_manifest/file_registry.csv](00_manifest/file_registry.csv): **COPY** of central tracking catalog mapping legacy files (from the original Attie lab data shares) to standardized HEUREKA paths. Columns include:
    - `original_path`: Source path on lab storage.
    - `new_path`: Normalized path within the HEUREKA directory structure.
    - `original_name` / `new_name`: Canonical file names.
    - `sha256`: Cryptographic hash verifying file integrity against originals.
    - `size`: Uncompressed byte size.
    - `matches_rdrive_original`: Verification status against the ResearchDrive source.
    - `parquet_path` / `parquet_status` / `parquet_sha256` / `pq_size`: Corresponding Parquet mirror tracking.
- [01_Datasets/README.md](01_Datasets/README.md): Primary expression, clinical phenotype, and ANOVA timecourse datasets across B6xBTBR F2, DO500, DO1200, and Founder cohorts.
- [02_Genetic_results/README.md](02_Genetic_results/README.md): Genome-wide significant QTL peaks, Bayesian causal mediation (`bmediatR`), sequence conservation, and variant impact tables.
- [03_Reference/README.md](03_Reference/README.md): Proteomic surveys in founder strains (13 tissues, diet studies) and islet pharmacological perturbations.
- [04_External/README.md](04_External/README.md): External functional genomics knowledge bases (STRING, BioPlex, Ensembl, GEO differential expression, HPA, HuGE AMP, Orthologs) and provenance manifest.
- [90_Archive/README.md](90_Archive/README.md): Historical verification records and gene coordinate consistency checks.
- [99_derived/README.md](99_derived/README.md): Output home for dynamic discovery tools (correlations, gene reports) and data freeze governance rules.
- [99_parquet/README.md](99_parquet/README.md): High-performance columnar Parquet query layer for zero-copy queries in DuckDB, Arrow, and Polars.

## Functional Organization

### 1. Manifest & Identity

- **`00_manifest/`**: Central registry and cross-referencing index mapping all source datasets to normalized paths, SHA256 checksums, Parquet conversion status, and unified gene/feature identifiers. (2026-10-07)

### 2. Primary Study Cohorts & Proteomics Reference

- **`01_Datasets/`**: High-dimensional molecular profiling across several foundational mouse cohorts: B6 x BTBR F2 intercross (5 tissues), longitudinal ANOVA timecourses (4, 10, 20 weeks), DO500, DO1200, and eight inbred founder strains. (2026-09-29)
- **`03_Reference/`**: Independent proteomic references, including Gygi lab founder diet studies, 13-tissue founder proteomic surveys, and islet HSP90beta inhibitor response data. (2026-09-23)
- **`04_External/`**: Curated external functional knowledge bases spanning protein-protein interactions (STRING v12.5, BioPlex 3.0/1.0), Ensembl GRCm39 gene models, GEO differential expression (11 studies), HPA v23, HuGE AMP GWAS, and human-mouse orthology tables. (2026-09-30)

### 3. Genetic Scans & Statistical Inference

- **`02_Genetic_results/`**: Statistical genetics and causal inference outputs connecting sequence variation to phenotypes through intermediate molecular traits: significant QTL peaks, Bayesian mediation models (`bmediatR`), evolutionary sequence constraint (UCSC 35-way alignment), and candidate variant impacts. (2026-09-29)

### 4. Storage Architecture, Tool Outputs & Governance

- **`90_Archive/`**: Historical verification outputs, including gene coordinate sanity checks. (2026-09-24)
- **`99_derived/`**: Design-controlled output directory for newly created dynamic tools (gene-trait correlation tables, co-expression networks, gene reports). Every run is captured with provenance metadata (`_provenance.json`). (2026-10-06)
- **`99_parquet/`**: Fast columnar storage mirror of `01_Datasets/`, `02_Genetic_results/`, and `03_Reference/`, enabling sub-second analytical queries without loading massive CSVs into memory. (2026-09-29)

### 5. Documentation & Version Control

- **`GitHub/`**: The git repository containing project documentation files, subfolder mirrors, and project descriptions: (2026-10-21)
  - `GitHub/HeurekaDO/README.md` -> `README.md`
  - `GitHub/project.md` -> `project.md`
  - `GitHub/prompts.md` -> `prompts.md`
  - `GitHub/HeurekaDO/[subfolder]/README.md` -> `[subfolder]/README.md`
  - `GitHub/README.md`: Overview of the GitHub repository and symlink setup.

## Data Governance & Freeze Rules

To maintain integrity across multi-investigator analyses and tool suites:

- **Read-Only Original Trees**: Directories `00_manifest/`, `01_Datasets/`, `02_Genetic_results/`, `03_Reference/`, and `04_External/` are frozen and read-only as of September 30, 2026.
- **Dynamic Output Destination**: All novel outputs from discovery tools must be written exclusively to `99_derived/`.
