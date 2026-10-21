# Manifest, Registry & Metadata Infrastructure

This directory serves as the centralized metadata and indexing core for the **HeurekaDO** discovery platform. It establishes persistent identity, SHA256 cryptographic verification, format translation tracking, and unified gene/feature cross-referencing across all integrated datasets.

## Registry & Verification Files

- **`file_registry.csv`**:
  The master tracking catalog mapping legacy files (from the original Attie lab data shares) to standardized HEUREKA paths. Columns include:
  - `original_path`: Source path on lab storage.
  - `new_path`: Normalized path within the HEUREKA directory structure.
  - `original_name` / `new_name`: Canonical file names.
  - `sha256`: Cryptographic hash verifying file integrity against originals.
  - `size`: Uncompressed byte size.
  - `matches_rdrive_original`: Verification status against the ResearchDrive source.
  - `parquet_path` / `parquet_status` / `parquet_sha256` / `pq_size`: Corresponding Parquet mirror tracking.

## Gene Indexes & Cross-Reference Tables

- **`gene_index.csv` & `gene_index.parquet`**:
  The central multi-dimensional gene index (~888 MB CSV, compressed to ~27 MB Parquet) providing rapid lookups across Ensembl gene IDs, official MGI gene symbols, synonyms, genomic coordinates (GRCm39), chromosome positions, and cross-dataset presence indicators.
- **`feature_aliases.csv` & `feature_aliases.parquet`**:
  Comprehensive dictionary resolving transcript, protein, lipid, and metabolite feature identifiers used across distinct platforms (microarrays, RNA-seq, Mass Spectrometry) into unified feature keys.
- **`external_aliases.parquet`**:
  Fast query table mapping internal mouse feature keys to external knowledge base identifiers, including STRING protein IDs, BioPlex interactors, HPA Ensembl identifiers, and human ortholog genes.

## Subject Manifests & Platform Annotations

- **`do500_mouse_manifest.csv`**:
  Subject-level manifest tracking all individual mice in the DO500 study, including animal IDs, sex, generational wave, batch indicators, and clinical measurement flags.
- **`probe_annotations_for_parents_and_F2_mice_HEUREKA.csv`**:
  Microarray probe annotations for the B6 x BTBR parent strains and F2 intercross animals, mapping Agilent/Affymetrix probe IDs to genomic coordinates and target gene annotations.

## Subdirectories

- **`feature_dictionaries/`**:
  Specialized trait dictionaries defining molecular entities:
  - `DO1200_list_of_labeled_liver_metabolites_HEUREKA.csv`: Chemical names, KEGG/HMDB IDs, and ionization modes for 13C/2H isotope tracer metabolites.
  - `DO1200_list_of_unlabeled_liver_metabolites_HEUREKA.csv`: Annotation table for unlabeled steady-state liver metabolites.
