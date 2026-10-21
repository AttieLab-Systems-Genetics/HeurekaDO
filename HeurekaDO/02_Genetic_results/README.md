# Genetic Results: QTL Peaks, Mediation & Variant Impacts

This directory contains the primary statistical genetics outputs connecting genome-wide sequence variation to molecular and clinical phenotypes across the Diversity Outbred populations (**DO500** and **DO1200**).

## Subdirectory Overview

```
02_Genetic_results/
├── qtl_peaks/      # Statistically significant QTL peak tables
│   ├── do500/      # DO500 peaks across 8 tissue/trait classes
│   └── do1200/     # DO1200 peaks across 7 tissue/trait classes
├── mediation/      # Bayesian causal mediation analysis (bmediatR)
│   ├── do500/      # Target-mediator relationships across tissues
│   └── do1200/     # Liver and plasma causal mediation models
├── conservation/   # Multi-species evolutionary constraint scores
│   ├── do500/      # UCSC 35-way alignment scores & priority rankings
│   └── do1200/     # Liver/plasma variant conservation rankings
└── variants/       # High & moderate functional consequence annotations
```

---

## 1. `qtl_peaks/`
Summary tables of genome-wide significant and suggestive QTL peaks generated using linear mixed-effect models (`qtl2::scan1`):
- **Cohort Coverage**:
  - `do500/`: Adipose FAHFAs, adipose transcriptomics, in vivo clinical traits, islet transcriptomics, islet cellular phenotypes (insulin secretion), liver transcriptomics, liver lipidomics, and plasma lipidomics.
  - `do1200/`: In vivo clinical traits, liver transcriptomics, liver transcript isoforms, liver lipidomics, liver isotope tracer metabolites (13C/2H labeled and unlabeled), and plasma metabolites.
- **Model Strata**:
  - `all_mice`: Combined sex additive models.
  - `female_mice` / `male_mice`: Sex-stratified additive models.
  - `HC_mice` / `HF_mice`: Diet-stratified models (high-calorie / high-fat).
- **Peak Metrics Reported**: Chromosome, peak position (cM and Mbp GRCm39), peak LOD score, Bayesian 95% credible / 1.5-LOD support intervals, and eight founder strain allele effects (A–H).

---

## 2. `mediation/`
Bayesian causal mediation analysis implemented via `bmediatR`:
- Evaluates whether an intermediate molecular trait (gene expression, protein abundance, lipid, or metabolite) mediates the causal effect of a local QTL on a distant downstream phenotype.
- Computes posterior probabilities for candidate causal models:
  - Complete mediation (QTL -> Mediator -> Target)
  - Partial mediation (Direct + Indirect effects)
  - Independent / reactive co-regulation
- Organized into cohort-specific subdirectories (`do500/` and `do1200/`) across cross-tissue target-mediator pairs.

---

## 3. `conservation/`
Evolutionary sequence constraint metrics evaluated using the UCSC 35-way multi-species vertebrate whole-genome alignment:
- Computes base-level phyloP and phastCons conservation scores across all variant loci located under significant QTL peaks.
- Constructs hybrid priority scores integrating LOD scores, founder allele concordance, and conservation metrics to prioritize functional candidate variants.

---

## 4. `variants/`
- **`all_mouse_strains_high_moderate_impact_variants_collapsed_with_conservation_score_HEUREKA.csv`**:
  Integrated variant catalog collapsing Ensembl Variant Effect Predictor (VEP) functional annotations across all 8 DO founder strains (A/J, B6, 129S1, NOD, NZO, CAST, PWK, WSB).
  Focuses on **HIGH** (frameshift, stop gained/lost, splice donor/acceptor) and **MODERATE** (missense, in-frame indels) impact variants, annotated with UCSC 35-way evolutionary conservation scores.
