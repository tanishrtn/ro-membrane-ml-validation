# Processed Data

This directory contains processed tabular inputs rebuilt from the current [Open Membrane Database JSON source](https://raw.githubusercontent.com/Open-Membrane-Database/membranes/main/membranes.json). The previous 976-row CSV contents were replaced rather than combined with the new source.

| File | Data rows | Purpose |
|---|---:|---|
| `preprocessed_full.csv` | 1,090 | Complete processed dataset |
| `train_data.csv` | 872 | Training split |
| `test_data.csv` | 218 | Holdout split |

All three files contain the same 59 columns, including the `A_over_B` target. The training and test rows combine to reproduce the full processed dataset as a multiset. The 80/20 split uses a deterministic shuffle with seed 42.

The source contains 20 records without a `CP` value. Missing `CP` values are filled using the mean calculated from the training partition only. `source_manifest.json` records the source URL, SHA-256 hash, record counts, split seed, and imputation value.

## Cautions

- The source JSON is a live file and may change. Use the recorded SHA-256 hash to identify this exact refresh.
- The files do not include a publication or membrane-family group identifier, so group-separated validation cannot be reconstructed from these CSVs alone.
- The repository notebook currently downloads and reconstructs data directly from the Open Membrane Database instead of loading these files.
- Avoid fitting imputers, scalers, feature selection, or target-informed transformations on the combined dataset before evaluation.
