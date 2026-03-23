# Weather and Crime Prediction

## Repository Contents

This repository contains the full pipeline for a study examining the relationship between weather conditions and crime rates, including dataset construction, exploratory analysis, and multiple predictive models (linear regression, SARIMAX, RNN, and LSTM).

---

## Section 1: Software and Platform

### Software
- **Python 3** — all analysis and modeling is done in Python via Jupyter Notebooks.

### Required Packages
Install all dependencies via `pip`:

```
pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn tensorflow torch tqdm requests
```

| Package | Purpose |
|---|---|
| `pandas`, `numpy` | Data manipulation |
| `matplotlib`, `seaborn` | Visualization |
| `scipy`, `statsmodels` | Statistical analysis and SARIMAX modeling |
| `scikit-learn` | Preprocessing and regression metrics |
| `tensorflow` | RNN model |
| `torch` | LSTM model |
| `tqdm`, `requests` | Data collection utilities |

### Platform
- Development was done on **Windows / Mac / Linux** (all platforms supported). Python 3.9+ is recommended.

---
## Section 2: Map of Documentation
```
PROJECT2---WEATHER-CRI.../
│
├── .ipynb_checkpoints/
│   ├── chicago_crime-checkpoint.ipynb
│   ├── Charlottesville...-checkpoint.ipynb
│   ├── RNNModel-checkpoint.ipynb
│   ├── temp-checkpoint.ipynb
│   ├── weather_crime_final-checkpoint.csv
│   └── weather_data-checkpoint.ipynb
│
├── .venv/
│
├── Data/
│   ├── Backup_Data/
│   ├── Data Appendix (1).pdf
│   ├── Dataset Formulation.pdf
│   └── weather_crime_final.csv        # Final merged dataset (weather + crime by city/date)
│
├── Outputs/
│   ├── Charlottesvillecrime_only.png
│   ├── Charlottesvilleweather_crime.png
│   ├── Chicagocrime_only.png
│   ├── Chicagoweather_crime.png
│   ├── crime_by_city.png
│   ├── crime_by_day.png
│   ├── crime_distribution.png
│   ├── crime_types_by_city.png
│   ├── Durhamcrime_only.png
│   ├── Durhamweather_crime.png
│   ├── fig1_scatter_by_city_size.png
│   ├── fig2_violent_property_scatter.png
│   ├── fig3_temp_bin_boxplots.png
│   ├── fig4_correlation_bar.png
│   ├── fig5_lagged_correlation.png
│   ├── fig6_ccf_plots.png
│   ├── fig7_rain_boxplots.png
│   └── fig8_temp_rain_heatmap.png
│   └── nrmse_comparison.png
│   └── NYCcrime_only.png
│   └── NYCcweather_crime.png
│   └── predicted_vs_actual.png
│
├── Scripts/
│   ├── Backup_Scripts/
│   │   ├── chicago_crime.ipynb
│   │   ├── Crime_EDA.ipynb
│   │   ├── Dataset_Project2.ipynb
│   │   ├── EDA_proj2.ipynb
│   │   ├── lstm.ipynb
│   │   ├── Modeling_proj2.ipynb
│   │   ├── RNNModel.ipynb
│   │   ├── temp.ipynb
│   │   └── weather_data.ipynb
│   ├── Dataset_Formulation.ipynb      # Step 1: Data collection and merging
│   ├── Exploratory_Data_Analysis.ipynb  # Step 2: EDA, visualizations, correlation analysis
│   └── Modeling.ipynb #Step 3: Linear Regression, SARIMAX, RNN (TensorFlow/Keras), and LSTM (PyTorch) Models 
│
├── README.md                          # Project overview and reproduction instructions
└── license.md                         # MIT License
```

## Section 3: Instructions for Reproducing Results

Follow these steps in order to reproduce the full results of the study.

### Step 1 — Set Up Your Environment

1. Ensure Python 3.9 or later is installed on your machine.
2. Install all required packages by running the following in your terminal:
   ```
   pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn tensorflow torch tqdm requests
   ```
3. Clone or download this repository and open the project folder.

### Step 2 — Prepare the Data

1. Place `weather_crime_final.csv` inside a folder named `Data/` in the project root directory (i.e., `Data/weather_crime_final.csv`). This file contains daily crime counts and weather measurements (mean temperature, precipitation) for each city.
2. Open and run **`Dataset_Formulation.ipynb`** top to bottom. This notebook handles any additional data pulling or preprocessing needed before analysis. If the CSV is already present, you may skip this step.

### Step 3 — Run Exploratory Data Analysis

1. Open **`Exploratory_Data_Analysis.ipynb`**.
2. Run all cells from top to bottom.
3. This notebook produces descriptive statistics, time series plots, correlation analyses, and cross-correlation functions (CCF) between weather variables and crime counts. Review the output plots to understand the structure of the data before modeling.

### Step 4 — Run the Modeling

1. Open **`Modeling.ipynb`**.
2. Run all cells from top to bottom.
3. The first section of this notebook fits a **Linear Regression** baseline and a **SARIMAX** time series model to predict crime counts from weather features. Evaluation metrics (MAE, RMSE, R²) are printed at the end of each model section.
4. The next section trains a **Recurrent Neural Network** using TensorFlow/Keras — first using both weather and crime features, then crime-only. Seeds are set at the top of the notebook (seed = 42) to ensure reproducibility. Final evaluation metrics are displayed after training.
5. The last section in this notebook notebook trains a **Long Short-Term Memory (LSTM)** network using PyTorch. It includes sequence building, an initial LSTM, and an improved LSTM variant. Results (MSE, MAE) are printed after each model.

### Notes on Reproducibility
- All models use fixed random seeds (42) where applicable. Results should be consistent across runs on the same machine, though minor floating-point differences may occur across different hardware or library versions.
- Make sure the `Data/` folder is at the project root level before running any notebook that loads `weather_crime_final.csv`.
