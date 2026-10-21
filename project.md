# HeurekaDO Project Overview

This project is conducted in the laboratory of
[Alan Attie](https://biochem.wisc.edu/people/attie/)
at the University of Wisconsin–Madison; see the
[Attie Lab Website](https://attielab.biochem.wisc.edu/)
for an overview of research programs in systems genetics, islet biology, and metabolic disease.

The **HeurekaDO** initiative represents a unified discovery platform integrating multiple mouse cohorts, longitudinal expression studies, high-resolution QTL mapping, multi-tissue causal mediation, external functional genomics, and high-performance columnar data storage. Its mission is to dissect the genetic architecture of type 2 diabetes, insulin resistance, beta-cell dysfunction, and systemic metabolic cross-talk.

## Multi-Cohort Systems Genetics Architecture

HeurekaDO synthesizes genetic, transcriptomic, proteomic, and metabolomic profiling across several complementary mouse populations:

1. **Diversity Outbred (DO) Populations**:
   - **DO500**: Approximately 500 Diversity Outbred mice maintained on high-fat, high-sucrose (HF/HS) diets, featuring multi-tissue molecular profiling across adipose, heart, ileum, islets of Langerhans, liver, plasma, and skeletal muscle.
   - **DO1200**: Over 1,200 DO mice providing deep physiological phenotyping, liver transcriptomics/isoforms/alternative splicing, metabolite kinetics, lipidomics, and high-density SNP association mapping.
   - **Founder Strains**: The eight inbred progenitor strains of the DO (A/J, C57BL/6J, 129S1/SvImJ, NOD/ShiLtJ, NZO/HlLtJ, CAST/EiJ, PWK/PhJ, WSB/EiJ) profiled under baseline and diet conditions.

2. **B6 x BTBR Intercross Populations**:
   - **B6 x BTBR F2 Intercross**: Over 500 F2 progeny derived from diabetes-resistant C57BL/6J (B6) and diabetes-susceptible BTBR mice, profiled across 5 metabolic tissues (adipose, gastrocnemius muscle, hypothalamus, pancreatic islets, and kidney) and deep clinical phenotyping.
   - **Longitudinal Timecourses**: Multi-tissue expression profiling across ages (4, 10, and 20 weeks) and obesity states (lean vs. *Lep^ob/ob*), modeled through factorial ANOVA.

3. **External Benchmarks and Validated Cohorts**:
   - Curated reference datasets (`Published/`) providing cross-validation for discovery findings.

## Integrated Functional Genomics Pipeline

HeurekaDO connects genetic locus discovery to molecular mechanisms through an integrated workflow:

```
Mouse Cohorts (01_Datasets/)
  ├── B6 x BTBR F2 (5 tissues, microarray)
  ├── B6 x BTBR Timecourse (ANOVA)
  ├── DO500 & DO1200 (Multi-tissue & Liver)
  └── Inbred Founder Strains
         │
         ▼
Genetic Mapping & Inference (02_Genetic_results/)
  ├── Significant QTL Peaks (qtl_peaks/)
  ├── Bayesian Causal Mediation (mediation/ via bmediatR)
  ├── Evolutionary Sequence Constraint (conservation/ UCSC 35-way)
  └── Candidate Coding & Regulatory Variants (variants/)
         │
         ▼
External Functional Integration (04_External/)
  ├── Protein-Protein Interaction Networks (STRING v12.5, BioPlex 3.0/1.0)
  ├── Gene Expression Omnibus (GEO differential expression across 11 studies)
  ├── Human Orthology & Genetic Portals (Ensembl BioMart, HuGE AMP GWAS)
  └── Human Tissue Protein Atlas (HPA v23)
         │
         ▼
High-Performance Analysis & Discovery Tools (99_parquet/ & 99_derived/)
  ├── Zero-Copy Columnar Storage (Parquet mirrors for instant DuckDB/Arrow queries)
  └── Dynamic Discovery Outputs (Gene-trait correlations, multi-tissue driver reports)
```

## Governance and Data Freeze

To ensure strict reproducibility across computational tools, collaborative analyses, and automated workflows:

- **Frozen Original Trees**: As of September 30, 2026, directories `00_manifest/`, `01_Datasets/`, `02_Genetic_results/`, `03_Reference/`, and `04_External/` are designated **read-only**. Files in these directories represent canonical frozen inputs.
- **Derived Tool Outputs**: All newly generated analysis outputs, gene-trait correlations, co-expression matrices, and driver overlays are stored exclusively in `99_derived/`. Each analysis subfolder is expected to contain a `_provenance.json` tracking inputs, scripts, parameters, and run dates.
- **Columnar Storage**: High-volume matrices are converted to Snappy-compressed Parquet files in `99_parquet/` to enable rapid, low-memory access without loading tens of gigabytes into memory.
