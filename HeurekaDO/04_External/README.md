# External Knowledge Bases & Biological Annotations

This directory aggregates and standardizes external public functional genomics, protein interaction, transcriptomic, and human genetic knowledge bases. These resources provide biological context, cross-species translation, and network-level annotations for QTL candidates discovered in mouse cohorts.

Provenance, cryptographic hashes, source URLs, and licensing terms are formally tracked in **`_source_manifest.json`**.

## Integrated Resources

### 1. `string/` (STRING Database v12.5)
- **Files**: `10090.protein.links.detailed.v12.5.txt.gz`, `10090.protein.info.v12.5.txt.gz`, `10090.protein.aliases.v12.5.txt.gz`.
- **Content**: Comprehensive functional protein-protein association networks for *Mus musculus* (Taxonomy ID 10090), including confidence scores partitioned across neighborhood, fusion, co-occurrence, co-expression, experimental, and text-mining channels.
- **License**: CC-BY-4.0; cite Szklarczyk et al., *Nucleic Acids Res.* 2023.

### 2. `bioplex/` (BioPlex 3.0 & 1.0 Interactomes)
- **Files**: `BioPlex_293T_Network_10K_Dec_2019.tsv`, `BioPlex_HCT116_Network_5.5K_Dec_2019.tsv`.
- **Content**: High-throughput affinity purification mass spectrometry (AP-MS) physical protein interactomes in HEK293T (~10,000 baits) and HCT116 (~5,500 baits) human cell lines.
- **License**: Academic use; cite Huttlin et al., *Cell* 2021.

### 3. `ensembl/` (Ensembl Gene Models release-116)
- **Files**: `Mus_musculus.GRCm39.116.gff3.gz`.
- **Content**: Canonical GRCm39 mouse genome annotation and feature coordinates (release 116).
- **License**: CC-BY-4.0.

### 4. `geo/` (Gene Expression Omnibus Curated DE Studies)
- **Files**: `geo_DE_all.csv`, `geo_DE_all.parquet`, `de_contrasts_spec.json`.
- **Content**: Normalized differential expression results spanning 11 published metabolic studies and 13 dataset-contrast units (processed via `edgeR glmQLFTest` for RNA-seq counts and `limma` for microarrays).
- **License**: Published open data; cite respective PMIDs documented in the metadata.

### 5. `hpa/` (Human Protein Atlas v23)
- **Files**: `proteinatlas.tsv.zip`.
- **Content**: Human tissue and cellular expression profiles, cell-type specificity classifications, and subcellular localization for human orthologs.
- **License**: Academic use; cite Uhlén et al., *Science* 2015.

### 6. `hugeamp/` (Common Metabolic Diseases Knowledge Portal)
- **Files**: `portal.trait_gene_combined.with_cat.gt1.txt.gz`.
- **Content**: Human genome-wide association study (GWAS) summary statistics, credible sets, and gene-level evidence scores for type 2 diabetes, BMI, fasting glucose/insulin, and cardiovascular traits.
- **Source**: CMD Knowledge Portal (HuGE AMP).

### 7. `orthologs/` (Ensembl BioMart High-Confidence Mappings)
- **Files**: `Mouse_to_human_all_genes.txt`, `Human_to_mouse_all_genes.txt`.
- **Content**: Cross-species orthology mapping tables between Ensembl mouse and human gene identifiers, including orthology confidence tiers and sequence identity metrics.
