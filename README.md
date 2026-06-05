# Yield Curve Reconstruction using Two-Factor CIR and Kalman Filtering

## Overview

This project reconstructs the short end of the Treasury yield curve (6M, 9M, 1Y, and 2Y) using only the observed 3M yield. The study begins with a Single-Factor Cox-Ingersoll-Ross (CIR) model and extends it to a Two-Factor CIR state-space model calibrated using Maximum Likelihood Estimation (MLE) and Kalman Filtering.

## Objectives

* Reconstruct 6M, 9M, 1Y, and 2Y yields from the observed 3M yield.
* Compare Single-Factor and Two-Factor CIR models.
* Evaluate model performance using RMSE, MAE, and Out-of-Sample R².

## Methodology

### Data Processing

* Missing values handled using forward fill.
* Outliers detected and normalized using the IQR method.
* Exploratory Data Analysis (EDA) performed on yield curve dynamics and maturity correlations.

### Single-Factor CIR

* Calibrated using Maximum Likelihood Estimation (MLE).
* Used as the baseline model for yield curve reconstruction.

### Two-Factor CIR Extension

* Formulated as a state-space model with two latent CIR factors.
* Calibrated using Kalman Filtering and MLE.
* Trained on all available maturities (3M–30Y) and evaluated on 6M–2Y reconstruction.

## Results

| Model                          | Average R² |
| ------------------------------ | ---------- |
| Single-Factor CIR              | 0.621      |
| Two-Factor CIR + Kalman Filter | 0.854      |

The proposed Two-Factor CIR model significantly improves reconstruction accuracy, reducing prediction error by approximately 32% and exceeding the target performance threshold.

## Technologies Used

* Python
* NumPy
* Pandas
* SciPy
* Scikit-learn
* Matplotlib

## Repository Structure

```text
├── Project_PS1.ipynb
├── train_data.csv
├── test_data.csv
├── test_data_3M.csv
└── README.md
```

## Key Takeaways

* Multiple latent factors are necessary to capture yield curve dynamics effectively.
* Kalman Filtering provides robust state estimation for latent interest-rate factors.
* The Two-Factor CIR model substantially outperforms the baseline Single-Factor CIR model in out-of-sample yield curve reconstruction.
