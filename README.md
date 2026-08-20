## Overview

This release provides the full pipeline for predicting superconducting critical temperature (Tc) using a two-level stacking ensemble. Base learners (Ridge, Lasso, KNN, SVR, MLP) generate out-of-fold meta-features, which an XGBoost meta-learner combines for final prediction. SHAP analysis drives feature selection and supports model interpretability.

## Contents

- **Feature selection**: `SHAP_feature_selection.ipynb` implements SHAP-based selection on the UCI Superconductivity Dataset (21,263 compounds, 81 features).
- **Hyperparameter tuning**: `tunning_50_HPO/` contains optimization runs for the top 50 selected features.
- **Evaluation**: `evaluation/` holds benchmarking scripts against Hamidieh (2018) and Shams et al. (2023).
- **External validation**: `External_validation_.ipynb` tests the trained model on 250 out-of-distribution compounds from Stanev et al.
- **Data**: `train_raw.csv`, `top50_train.csv`, `top50_test.csv`, and `stanev_250_unseen_compounds.csv` provide the training, test, and external validation splits.

## Results

- Held-out test set: RMSE = 8.839 K, R² = 0.932, MAE = 4.919 K
- External validation (250 unseen compounds): RMSE = 7.664 K, R² = 0.913, MAE = 5.248 K
