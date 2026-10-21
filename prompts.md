# AI Prompts & Architecture Log

This document records the user prompts, implementation rationale,
and shell commands used to establish the documentation architecture and symbolic links for the HeurekaDO discovery platform on ResearchDrive.

## Prompts for Documentation Architecture

- **Initial Architecture Request**:
  > "HeurekaDO Data Architecture: follow example in `~/Documents/GitHub/sysgenDO1200/GitHub` to create `README.md` files in `GitHub` along with symbolic links. Start by reading `../sysgenDO1200/GitHub/README.md` and developing an implementation plan."
- **Execution & Scope Approval**:
  > Approved implementation plan with `HeurekaDO` folder designation inside `GitHub/`.

## Prompts for README Files

- **Top-Level Repositories**:
  - Create a root `GitHub/README.md` that outlines the mirror repository, links to `project.md` and all subfolder READMEs, and documents the symbolic link creation commands.
  - Create `GitHub/project.md` providing an in-depth scientific overview of HeurekaDO, Attie Lab research context, multi-cohort design (F2, DO500, DO1200, Founders), external functional genomics, and data freeze governance.
  - Create `GitHub/HeurekaDO/README.md` indexing the 8 primary directory trees, functional pillars, data freeze policies, and last modification dates.
- **Manifest & Metadata Infrastructure**:
  - Create `GitHub/HeurekaDO/00_manifest/README.md` documenting `file_registry.csv`, large-scale `gene_index` tables, alias parquet databases, mouse manifests, and feature dictionaries.
- **Datasets & Primary Expression**:
  - Create `GitHub/HeurekaDO/01_Datasets/README.md` detailing the B6xBTBR F2 intercross, longitudinal timecourses (ANOVA models), DO500, DO1200, founder strains, and published datasets.
- **Genetic Scans, Peaks & Mediation**:
  - Create `GitHub/HeurekaDO/02_Genetic_results/README.md` covering significant QTL peaks, Bayesian mediation models (`bmediatR`), evolutionary sequence conservation (UCSC 35-way), and variant impacts.
- **Reference Proteomics**:
  - Create `GitHub/HeurekaDO/03_Reference/README.md` detailing founder diet liver proteomics, 13-tissue proteomic surveys, and islet HSP90beta perturbation experiments.
- **External Biological Databases**:
  - Create `GitHub/HeurekaDO/04_External/README.md` detailing STRING v12.5 PPI networks, BioPlex 3.0/1.0 interactomes, Ensembl 116 GRCm39 models, GEO differential expression datasets, HPA v23, HuGE AMP GWAS, and ortholog tables.
- **Archive & Validation**:
  - Create `GitHub/HeurekaDO/90_Archive/README.md` summarizing coordinate validation checks and archival historical tables.
- **Derived Tool Output & Governance**:
  - Create `GitHub/HeurekaDO/99_derived/README.md` detailing rules for tool outputs, provenance tracking (`_provenance.json`), correlation matrices, and gene summary reports.
- **Columnar Storage Layer**:
  - Create `GitHub/HeurekaDO/99_parquet/README.md` describing Parquet conversion tables, DuckDB/Arrow access patterns, and query performance optimizations.

## Symbolic Link Setup

The following commands were used to link markdown documentation from `GitHub/` into the working directories of `DO-Discovery_HEUREKA_2026-09-29`:

```bash
# In /Volumes/mkeller3/General/DO-Discovery_HEUREKA_2026-09-29

# Root symbolic links
ln -s GitHub/HeurekaDO/README.md README.md
ln -s GitHub/project.md project.md
ln -s GitHub/prompts.md prompts.md

# Subdirectory symbolic links
cd 00_manifest && ln -s ../GitHub/HeurekaDO/00_manifest/README.md README.md && cd ..
cd 01_Datasets && ln -s ../GitHub/HeurekaDO/01_Datasets/README.md README.md && cd ..
cd 02_Genetic_results && ln -s ../GitHub/HeurekaDO/02_Genetic_results/README.md README.md && cd ..
cd 03_Reference && ln -s ../GitHub/HeurekaDO/03_Reference/README.md README.md && cd ..
cd 04_External && ln -s ../GitHub/HeurekaDO/04_External/README.md README.md && cd ..
cd 90_Archive && ln -s ../GitHub/HeurekaDO/90_Archive/README.md README.md && cd ..
cd 99_derived && rm -f README.md && ln -s ../GitHub/HeurekaDO/99_derived/README.md README.md && cd ..
cd 99_parquet && ln -s ../GitHub/HeurekaDO/99_parquet/README.md README.md && cd ..
```
