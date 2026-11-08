# Reverse Osmosis Membrane Machine Learning Validation

This repository supports the paper **Validation and Controlled Experiments for Reverse Osmosis Membrane Selectivity**. It contains the IEEE-style report, a reproducible notebook based on Gao et al. (2025), and the processed train/test datasets used by the wider validation project.

## Project overview

The project studies machine-learning prediction of reverse-osmosis membrane water–salt selectivity (`A_over_B`). It focuses on reproducibility, leakage-aware evaluation, controlled model comparisons, and transparent reporting.

The notebook reproduces a paper-style benchmark from the Open Membrane Database and compares seven regression model families. It also includes an improved-model comparison and a publication-group split audit.

## Repository structure

```text
ro-membrane-ml-validation/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   ├── README.md
│   ├── preprocessed_full.csv
│   ├── train_data.csv
│   └── test_data.csv
├── notebooks/
│   └── ro_membrane_ml_replication.ipynb
└── report/
    └── ro_membrane_validation_report.docx
```

## Data

The processed dataset contains 976 observations. The supplied split contains 780 training rows and 196 test rows. Each file includes the target column `A_over_B`.

The combined training and test rows match the full processed dataset as a multiset. See [`data/README.md`](data/README.md) for the file contract and cautions.

## Run the notebook

1. Create and activate a Python environment.
2. Install the dependencies:

   ```bash
   python -m pip install -r requirements.txt
   ```

3. Start Jupyter:

   ```bash
   jupyter lab
   ```

4. Open `notebooks/ro_membrane_ml_replication.ipynb` and run the cells in order.

An internet connection is required because the notebook downloads the current Open Membrane Database JSON file at runtime. The notebook records the download time and SHA-256 hash for traceability.

## Important reproducibility note

The notebook and the supplied CSV files represent related but distinct project paths:

- The notebook reconstructs its modelling table directly from the current Open Membrane Database JSON source.
- The report describes a broader validation framework whose data contract uses `train_data.csv`, `test_data.csv`, and `preprocessed_full.csv`.

The notebook does not currently load the three CSV files. Results from the live database reconstruction should therefore not be presented as if they came from the supplied processed split without first aligning the preprocessing and feature definitions.

## Reference study

W. Gao et al., “Insights into synthesis and optimization features of reverse osmosis membrane using machine learning,” *Materials*, vol. 18, no. 4, article 840, 2025. https://doi.org/10.3390/ma18040840

## Status

The report distinguishes published reference scores, software verification, and results that still require execution on the membrane dataset. Synthetic checks validate code behaviour but are not evidence of improved membrane prediction.

## License

No license has been selected. Until a license is added, reuse is not automatically permitted beyond rights provided by applicable law.
