# Air Quality Index (AQI) Prediction Using Time Series Models

## Overview
This repository contains a Jupyter Notebook that analyzes and predicts the Air Quality Index (AQI) for Jaipur and Kolkata using time series models. The notebook leverages AR, MA, ARMA, ARIMA, and SARIMA models to forecast AQI values based on historical data.

## Dataset
- The dataset contains hourly AQI readings for Jaipur and Kolkata.
- Data is aggregated into daily and weekly averages for analysis.
- The timeframe spans from 2018-01-01 to the most recent available data.

## Features
### 1. Data Preprocessing
- Converts hourly AQI data into daily and weekly averages.
- Creates a date range and sets it as the index.
- Splits the data into training (all but the last 365 days) and testing (last 365 days).

### 2. Stationarity Testing
- **Augmented Dickey-Fuller (ADF) Test**: Checks if the time series is stationary by testing for the presence of a unit root.
  - **Null Hypothesis (H0)**: The series is non-stationary.
  - If the p-value < 0.05, we reject H0 and conclude the series is stationary.
- **Kwiatkowski-Phillips-Schmidt-Shin (KPSS) Test**: Checks if the time series is trend-stationary.
  - **Null Hypothesis (H0)**: The series is stationary.
  - If the p-value < 0.05, we reject H0 and conclude the series is non-stationary.
- If ADF rejects non-stationarity but KPSS rejects stationarity, differencing may be required.
- If both tests indicate non-stationarity, transformations like log differencing or seasonal decomposition may be needed.

### 3. Time Series Analysis
- Computes and visualizes Autocorrelation (ACF) and Partial Autocorrelation (PACF) to determine lag dependencies.
- Conducts analysis on both daily and weekly AQI data.

### 4. Model Training & Forecasting
Trains and forecasts AQI using the following models:
- **Autoregressive (AR)**
- **Moving Average (MA)**
- **Autoregressive Moving Average (ARMA)**
- **Autoregressive Integrated Moving Average (ARIMA)**
- **Seasonal ARIMA (SARIMA)**

Uses sliding window forecasting, where each model is updated iteratively with real test values.

### 5. Model Evaluation
Compares model performance using:
- **R² Score**
- **Mean Absolute Error (MAE)**
- **Root Mean Square Error (RMSE)**

Visualizes actual vs. predicted AQI for all models.

## Installation
Clone the repository and install the required dependencies:

```bash
git clone <repository-url>
cd AQI-Analysis
pip install -r requirements.txt
```

Alternatively, install the required libraries manually:

```bash
pip install numpy pandas matplotlib statsmodels scikit-learn
```

## Usage
Run the Jupyter Notebook:

```bash
jupyter notebook AQI.ipynb
```

## Results & Insights
- Stationarity tests (ADF & KPSS) help determine the need for differencing before model training.
- The SARIMA model typically performs best due to its ability to capture seasonality.
- The ARIMA model works well for general trends but may struggle with seasonal variations.
- ACF and PACF plots help in determining the order of AR, MA, and seasonal components.

## Future Improvements
- Experiment with LSTM or GRU models for deep learning-based forecasting.
- Perform hyperparameter tuning for optimal model performance.
- Incorporate exogenous variables (weather, traffic) to enhance predictions.

## Contributing
Feel free to submit pull requests or open issues for improvements and bug fixes.

## License
This project is licensed under the MIT License.

## Author
[Ritabrata Chakraborty](https://github.com/yourgithubprofile)

