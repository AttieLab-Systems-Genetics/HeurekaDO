# GitHub Documentation Repository

This repo contains documentation files for the [ResearchDrive](https://it.wisc.edu/services/researchdrive/)
folder `mkeller3/General/DO-Discovery_HEUREKA_2026-09-29`.
The repo is a mirror of the subfolder `GitHub`.
This repo is public, but the ResearchDrive (RD) area is private.
The file
[project.md](project.md)
describes the project in more detail.
Updated 21 Oct 2026.

## Files

- [project.md](project.md): Outline of the HeurekaDO project, systems genetics discovery platform, cohorts, multi-tissue design, and data structures.
- [prompts.md](prompts.md): Prompts and commands used to establish the documentation and symbolic link architecture.
- [HeurekaDO/README.md](HeurekaDO/README.md): Master catalog of the `HeurekaDO` (`DO-Discovery_HEUREKA_2026-09-29`) directory structure, subfolders, and governance rules.
- [HeurekaDO/00_manifest/README.md](HeurekaDO/00_manifest/README.md): File registry, gene index, alias mappings, mouse manifests, and feature dictionaries.
- [HeurekaDO/01_Datasets/README.md](HeurekaDO/01_Datasets/README.md): Primary expression, clinical phenotype, and ANOVA timecourse datasets across B6xBTBR F2, DO500, DO1200, and Founder cohorts.
- [HeurekaDO/02_Genetic_results/README.md](HeurekaDO/02_Genetic_results/README.md): Genome-wide QTL peaks, Bayesian mediation models (`bmediatR`), sequence conservation, and candidate variant impacts.
- [HeurekaDO/03_Reference/README.md](HeurekaDO/03_Reference/README.md): Reference proteomics surveys in founder strains (13 tissues, diet studies) and islet pharmacological perturbations.
- [HeurekaDO/04_External/README.md](HeurekaDO/04_External/README.md): External functional genomics knowledge bases (STRING, BioPlex, Ensembl, GEO differential expression, HPA, HuGE AMP, Orthologs) and provenance manifest.
- [HeurekaDO/90_Archive/README.md](HeurekaDO/90_Archive/README.md): Historical verification records and coordinate consistency checks.
- [HeurekaDO/99_derived/README.md](HeurekaDO/99_derived/README.md): Output home for dynamic discovery tools (correlations, gene reports) and data freeze governance rules.
- [HeurekaDO/99_parquet/README.md](HeurekaDO/99_parquet/README.md): High-performance columnar Parquet query layer for zero-copy queries in DuckDB, Arrow, and Polars.

## Symbolic Links

Each of these documentation files has a
[symbolic link](https://www.computerhope.com/jargon/s/symblink.htm)
in the `DO-Discovery_HEUREKA_2026-09-29` directory or its respective subfolder.
These symbolic links enable us to have the primary version-controlled copy of documentation in the `GitHub` folder, while still having it easily accessible in the working directories on ResearchDrive.

The symbolic links are created in Linux/macOS using the following commands:

```bash
# Root DO-Discovery_HEUREKA_2026-09-29 symbolic links
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

---

The `GitHub` folder on ResearchDrive connects to the GitHub repository using help from
[Get started with GitHub](https://happygitwithr.com/usage-intro#usage-intro) and
[Existing project, GitHub last](https://happygitwithr.com/existing-github-last#existing-github-last).
