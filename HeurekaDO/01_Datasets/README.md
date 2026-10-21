# Multi-Cohort Datasets & Primary Expression Matrices

This directory houses the primary quantitative phenotype tables, transcriptomic profiling matrices, longitudinal expression timecourses, and clinical metadata across the core mouse cohorts analyzed within **HeurekaDO**.

## Cohort Organization

### 1. `B6_BTBR_F2/`
Molecular and clinical profiling of the C57BL/6J x BTBR F2 intercross cohort (>500 mice):
- **`expression/`**: Microarray gene expression profiling across five metabolic tissues:
  - Adipose (`adipose_int2_HEUREKA.csv`, `adipose_mlratio_HEUREKA.csv`)
  - Gastrocnemius muscle (`gastroc_int2_HEUREKA.csv`, `gastroc_mlratio_HEUREKA.csv`)
  - Hypothalamus (`hypo_int2_HEUREKA.csv`, `hypo_mlratio_HEUREKA.csv`)
  - Pancreatic islets (`islet_int2_HEUREKA.csv`, `islet_mlratio_HEUREKA.csv`)
  - Kidney (`kidney_int2_HEUREKA.csv`, `kidney_mlratio_HEUREKA.csv`)
  Both raw intensity (`int2`) and mean log-ratio (`mlratio`) metrics are provided.
- **`metadata/`**: Mouse-level annotations (`Annotations_F2_mice_for_five_tissues_HEUREKA.csv`) and genomic probe coordinate ordering (`gene_order_HEUREKA.csv`).
- **`phenotypes/`**: In vivo and post-sacrifice physiological phenotypes (`Clinical_phenotypes_all_B6BTBR_F2_mice_HEUREKA.csv`), including glucose tolerance tests, insulin secretion, adiposity, and plasma lipid profiles.

### 2. `B6_BTBR_timecourse/`
Longitudinal gene expression study examining age and obesity progression in B6 and BTBR mice:
- **`anova/`**: Factorial ANOVA summary models across tissues evaluating main effects of age (4, 10, 20 weeks), obesity status (*Lep^ob/ob* vs. lean), and age x obesity interaction.
- **`expression/`**: Tissue-specific expression matrices for adipose, gastrocnemius, hypothalamus, islets, and kidney across timepoints.
- **`metadata/` & `phenotypes/`**: Animal age cohorts, genotyping confirmation, and clinical trajectory tables.

### 3. `DO500_HFHS/`
The ~500 Diversity Outbred cohort maintained on a high-fat, high-sucrose diet:
- **`expression/`**: Multi-tissue expression profiling across adipose, heart, ileum, pancreatic islets, liver, and skeletal muscle.
- **`metadata/`**: Subject covariates (sex, wave, diet duration, generation).
- **`phenotypes/`**: Clinical measurements, GTT dynamics, insulin secretion indices, and lipidomic profiles.

### 4. `DO1200_HF_HS/`
The large-scale ~1,200 Diversity Outbred cohort on HF/HS diet:
- **`expression/`**: Liver transcriptomics, transcript isoform abundances, and alternative splicing percent-spliced-in (PSI) matrices.
- **`metadata/`**: Batch identifiers, sequencing depth, and covariate tables.
- **`phenotypes/`**: In vivo clinical traits, plasma and liver isotope tracer metabolomics (13C, 2H), and lipidomics.

### 5. `Founders_DO500_HFHS/` & `Founders_DO1200_HF_HS/`
Molecular profiling of the 8 DO progenitor inbred strains (A/J, B6, 129S1, NOD, NZO, CAST, PWK, WSB):
- Variance-stabilized gene and isoform expression (`vsd_genes_founder_app_liverRNA_HEUREKA.csv`, `vsd_isoforms_founder_app_liverRNA_HEUREKA.csv`).
- In vivo clinical parameters, baseline phenotypes, and diet response metrics.

### 6. `Published/`
Curated validation datasets from peer-reviewed publications:
- **Emfinger et al. (2022)** *JCI Insight* (PMID: 35603790): RNA-seq and whole-islet proteomics in *Zfp148* wild-type and knockout mice.
- **Keller et al. (2016)** *PLOS Genet* (PMID: 27935966): Mouse islet RNA-seq following *NFATc1* and *NFATc2* overexpression.
- **Simonett et al. (2021)** *JCI* (PMID: 34491912): Human islet RNA-seq following *NFATc1*/*NFATc2* overexpression.
- **Petersen et al. (2024)** *Cell Metab* (PMID: 38569471): Human adipose RNA-seq in metabolically healthy vs. unhealthy obesity.
- **Kolic et al. (2024)** *Cell Metab* (PMID: 38959864) and **Roy et al. (2025)** *Cell Rep* (PMID: 40512624).
