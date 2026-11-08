# Processed Data

This directory contains the processed tabular inputs supplied with the project.

| File | Data rows | Purpose |
|---|---:|---|
| `preprocessed_full.csv` | 976 | Complete processed dataset |
| `train_data.csv` | 780 | Training split |
| `test_data.csv` | 196 | Supplied holdout split |

All three files contain the same 59 columns, including the `A_over_B` target. The training and test rows combine to reproduce the full processed dataset as a multiset.

## Cautions

- The provenance of upstream preprocessing should be documented before treating the holdout as fully independent.
- The files do not include a publication or membrane-family group identifier, so group-separated validation cannot be reconstructed from these CSVs alone.
- The repository notebook currently downloads and reconstructs data directly from the Open Membrane Database instead of loading these files.
- Avoid fitting imputers, scalers, feature selection, or target-informed transformations on the combined dataset before evaluation.
