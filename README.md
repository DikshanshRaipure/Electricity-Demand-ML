# Delhi Electricity Demand Forecasting

Hi there! I'm a 20-year-old student who took on a data science project to forecast **Delhi's hourly electricity demand** using machine learning and time series features. This repo contains my complete approach, code, data-cleaning workflow, and the XGBoost model I trained and tested. Hope this helps anyone who wants to work on a similar project or just get better at data science!

## Project Overview

The aim was to predict **Delhi's electricity demand** at the hourly level from Jan 2020 to Dec 2024, using public datasets containing temperature, humidity, and typical datetime features. I focused on **handling missing values, time-based feature engineering, and building a strong predictive model**.

## Dataset

- The dataset contains hourly entries for:
  - Timestamp
  - hour, dayofweek, month, year, dayofyear, weekofyear, quarter
  - Temperature, Humidity
  - Electricity Demand (target)
- Around 44,000+ rows, cleaned from missing or corrupt entries.

## Features & Engineering

- Converted timestamps to pandas’ datetime.
- Created **lag features** (demand 24h or 168h ago), **rolling means/stds** for capturing trends.
- Added **is_weekend** and checked Indian public holidays for pattern discovery (dropped after EDA).
- Did careful **missing-value imputation** (bfill/interpolate or dropping).
- Created more time-context (week of year, quarter).
- **Final features**: mostly numerically encoded for the ML model.

## Exploratory Data Analysis (EDA)

- Plotted overall demand trend to show seasonality, spikes, and dips.
- Box plots for hourly and monthly variations.
- Scatter plot: Temperature vs. Demand.
- Correlation heatmap to check dependencies.
- EDA really helped in selecting features and understanding important drivers for demand.

## Model Building

- Used **XGBoost Regressor** because it handles non-linear time series really well.
- Split dataset: **train = up to 2023**, **test = 2024**.
- Metrics:
  - **Root Mean Squared Error (RMSE): ~175**
  - **Mean Absolute Error (MAE): ~123**
- Visualized **Actual vs. Predicted Demand** — the model tracks well, though peaks are still tricky.

## Project Structure

- `electricity-demand-ml-model.pdf` — Full notebook and documentation
- `delhi_electricity_demapnd.csv` — Main cleaned data
- `xgb_model.pkl` — Saved model, ready to deploy
- Code snippets for preprocessing and feature engineering
- Visualizations and EDA plots

## How to Use

1. **Clone** this repo.
2. Place the dataset and notebook in your work directory.
3. Run the Jupyter/Colab notebook for full reproducibility.
4. If you want predictions for new data, just load `xgb_model.pkl` using joblib.
5. Experiment with feature engineering for different cities or countries!

## What I Learnt

- **Real-world data is messy!** Handling missing values and corrupted entries is super important.
- **Feature engineering matters** — lag features and rolling stats boosted model power.
- **Visualization is not optional** — it’s essential for understanding both data and results.
- Working with **time series data** is quite different than regular tabular data.
- **XGBoost is a beast** for tabular regression — try tuning for better results!
- Saving models and reproducibility is good practice.
- Last but not least, documenting every step makes sharing and collaboration a lot easier.
