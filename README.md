# Integrated Predictive Maintenance and Energy Forecasting Platform
This repository contains the code, notebook, and documents for an integrated platform that combines predictive maintenance and energy forecasting to optimize industrial operations.
​

## Overview
The project builds a real-time dashboard that:

Predicts Remaining Useful Life (RUL) for industrial engines using the NASA CMAPSS FD001 dataset.
​

Forecasts short-term energy consumption using a steel industry energy dataset and Prophet.
​

Aligns maintenance actions with low-cost energy periods to reduce downtime and operating cost.
​

## Key Features
# Predictive maintenance (PdM)

Random Forest Regressor trained on selected CMAPSS sensor and operating features.

Achieves about 
RMSE
≈
25
RMSE≈25 cycles and 
R
2
≈
0.64
R 
2
 ≈0.64 on test data.
​

### Energy forecasting

Prophet time-series model on hourly steel plant energy data with calendar and load-type regressors.

Achieves about MAPE ≈ 9.65 and RMSE ≈ 65.36 kWh over a 7‑day hourly horizon.
​

### Integrated scheduling

Merges RUL predictions with energy cost forecasts using timestamps.

Flags units with RUL < 30 cycles and schedules maintenance in the lowest forecasted energy-cost periods.
​

### Real-time dashboard (Streamlit)

Live plots of RUL vs. time for multiple units.

Live energy usage and forecast curves.

Maintenance alerts and an exportable maintenance schedule (CSV).
​

## Project Structure
### Source_Notebook.ipynb

End-to-end workflow: data loading, preprocessing, model training, evaluation, and CSV exports (cmapsspredictions.csv, steelenergyforecast.csv, integratedschedule.csv).
​

### Integrated_Predictive_Maintenance_and_Energy_Forecasting_Platform_for_Industrial_Optimization.docx

Full project report: background, datasets, methods, results, and future work.
​

### Integrated-Predictive-Maintenance-and-Energy-Forecasting-Platform-for.pptx

Presentation slides summarizing motivation, approach, and results.
​

### realtimedashboardcolab.py (generated from the notebook)

Streamlit app for real-time simulation and visualization.

Integrates PdM and energy forecasting with maintenance alerts and schedule export.
​

## Datasets
### NASA CMAPSS FD001

Multivariate time series for 100 engines, 23 sensors, 3 operating settings.

Used to compute and predict RUL per engine.
​

### Steel Industry Energy Dataset

Hourly energy usage, power factors, and environmental variables from a steel plant.

Used for short-term energy and cost forecasting.
​

(Ensure the dataset files are placed in the expected data/ folder or update paths in the notebook/script.)
​

## How to Run
### Environment setup

Python 3.11+

Recommended packages:

pandas, numpy, scikit-learn

prophet

matplotlib

streamlit, pyngrok (for the dashboard, optional)
​

### Reproduce core experiments

Open Source_Notebook.ipynb in Jupyter or Colab.

Run cells sequentially to:

Load and preprocess CMAPSS and steel datasets.

Train the Random Forest PdM model and Prophet energy model.

Generate evaluation metrics and plots.

Save prediction and schedule CSVs.
​

### Run the real-time dashboard (optional)

Ensure realtimedashboardcolab.py exists (or export it from the notebook).

Install streamlit and pyngrok.

### Run:

bash
streamlit run realtimedashboardcolab.py
If using ngrok (e.g., in Colab), configure your auth token and use the provided public URL.
​

## Results (Summary)
PdM (Random Forest): RMSE ≈ 25 cycles, 
R
2
≈
0.64
R 
2
 ≈0.64 on test engines.
​

### Energy forecasting (Prophet): MAPE ≈ 9.65, RMSE ≈ 65.36 kWh for the 7‑day hourly horizon.
​

### Integrated schedule: successfully proposes maintenance windows where RUL is low and energy cost is minimized.
​

## Future Work
Explore deep learning models (e.g., LSTMs) for RUL and energy forecasting.

Add more industrial datasets and richer IoT streaming integration.

Deploy the dashboard on cloud infrastructure for production use.
