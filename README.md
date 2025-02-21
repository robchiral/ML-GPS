# ML-GPS

## Overview
This is the GitHub repository for **ML-GPS: a machine learning-assisted genetic priority score**.

### Reference
Chen R, Duffy Á, Petrazzini BO, Vy HM, Stein D, Mort M, Park JK, Schlessinger A, Itan Y, Cooper DN, Jordan DM, Rocheleau G, Do R. Expanding drug targets for 112 chronic diseases using a machine learning-assisted genetic priority score. *Nat Commun.* 2024 Oct 15;15(1):8891. doi: [10.1038/s41467-024-53333-y](https://doi.org/10.1038/s41467-024-53333-y).

## ML-GPS Predictions
- **Interactive results**: The top 10% of ML-GPS and ML-GPS DOE predictions can be viewed at [this web application](https://rstudio-connect.hpc.mssm.edu/mlgps/).
- **Full predictions**: Available for download at [Zenodo](https://doi.org/10.5281/zenodo.10939110).

## Requirements
- Python **3.11.6**
- Dependencies are listed in `requirements.txt`. Install them using:
  ```sh
  pip install -r requirements.txt
  ```

## Running the Analysis
The repository contains six Jupyter notebooks required for data cleaning, training ML-GPS and ML-GPS DOE models, and reproducing figures. **Run these notebooks in order**:

1. **Create cleaned files.ipynb**
2. **Create inputs for training.ipynb**
3. **Analyze univariate associations.ipynb**
4. **Training ML-GPS and ML-GPS DOE models.ipynb**
5. **Calculating additional metrics.ipynb**
6. **Formatting final predictions.ipynb**

## Required External Datasets
Several directories must be downloaded from the Zenodo repository ([doi:10.5281/zenodo.10939110](https://doi.org/10.5281/zenodo.10939110)) as they are too large to be hosted on GitHub:

- **Cleaned files** (Generated in Step 1; required for Steps 2 and beyond)
- **Datasets** (Generated in Step 2; required for Steps 3 and beyond)
- **Models** (Generated in Step 4; required for Steps 5 and beyond)
- **OT_2024.9** (Generated in Step 0; required for Steps 1 and beyond)
- **Raw files** (Required for all steps)

## Important Updates
Results in the Jupyter notebooks **slightly differ** from those in the original manuscript due to improvements and error corrections:

1. **Updated Open Targets dataset**: Uses release **2024.9** instead of **2023.3**.
2. **Fixed DOE model direction error**: Previously, direction-of-effect for rare and ultrarare variants was incorrectly incorporated.
3. **Adjusted phase-based weighting in DOE model**: Decreased weighting to improve model performance.
4. **OMIM feature refinement**: Now uses **OMIM gene-level annotations** instead of OMIM variants, reducing redundancy with ClinVar.
5. **Increased maximum LightGBM iterations**: Increased from **500 to 1000**, with early stopping after **10 iterations** of no improvement.

---