# Archival Records & Verification Checks

This directory retains quality control audits, validation checkpoints, and historical verification records created during data ingestion and pipeline standardization.

## Archived Checkpoints

- **`gene_order_check_HEUREKA.csv`**:
  Quality control audit confirming that across all 10 B6 x BTBR F2 tissue expression matrices (adipose, gastrocnemius, hypothalamus, islet, and kidney; both `int2` raw intensities and `mlratio` log-ratios), all 31,280 microarray gene features maintain identical row ordering (`same_as_first = TRUE`).
  This ensures that row indices across tissues and metrics are directly alignable without risk of feature misordering.
