# 99_derived — Tool Output Home & Analysis Repository

This directory serves as the designated, write-permissible output workspace for dynamic discovery tools, association pipelines, correlation analyses, and multi-tissue report generators.

## Governance Rules

To preserve reproducible data baselines across investigators and computational pipelines:

1. **Isolation from Frozen Trees**:
   All new analytical and tool outputs must be written **HERE**, never into `00_manifest/`, `01_Datasets/`, `02_Genetic_results/`, `03_Reference/`, or `04_External/`. Those canonical trees are permanently **frozen** and read-only as of 2026-09-30.
2. **Analysis-Specific Subfolders**:
   Each discrete run or analytical batch must reside in its own subfolder (e.g., `gene_trait_corr_2026-10-05/`).
3. **Mandatory Provenance Tracking**:
   Every output folder must carry a `_provenance.json` recording:
   - Input file paths and checksums
   - Execution script name and version
   - Command-line arguments and hyper-parameters
   - Execution timestamp and runtime user
4. **Modifications to Frozen Originals**:
   Modifying a frozen original file is strictly restricted to rare corrections: strip read-only flag -> perform audited edit -> re-apply read-only permissions -> record change in `prompts.md`.

## Active Output Subdirectories

- **`correlations/`**:
  Calculated pairwise correlations between gene expression traits and in vivo clinical parameters, cross-tissue co-expression matrices, and ranked association tables.
- **`gene_reports/`**:
  Synthesized multi-dimensional gene dossier reports combining QTL evidence, Bayesian mediation probabilities, STRING interactors, and human GWAS orthology.
