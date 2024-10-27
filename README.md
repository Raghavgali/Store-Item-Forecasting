# Store-Item-Forecasting

This project aims to build a robust time series forecasting model to predict daily sales for various items across multiple stores. By leveraging both traditional time series methods and machine learning techniques, this project provides accurate forecasts, enabling better inventory and demand planning.

# Table of Contents

1. [Project Overview](#Project Overview)
2. [Data](#Data)
3. [Approach](#Approach)
4. [Feature Engineering](#Feature Engineering)
5. [Model Selection](#Model Selection)
6. [Evaluation Metrics](#Evaluation Metrics)
7. [Results](#Results)
8. [Future Work](#Future Work)


# Project Overview

The goal of this project is to forecast sales for 50 items across 10 stores over a three-month period. This forecasting model will support inventory management, helping to optimize stock levels and meet customer demand effectively. The project involves an extensive feature engineering process, the use of cross-validation techniques tailored for time series data, and experimentation with both machine learning and statistical models.

# Data

The dataset contains daily sales records for multiple items across various stores, with each entry representing the number of units sold on a particular day.

	• Items: 50 unique items.
	• Stores: 10 different stores.
	• Time Period: Daily data for multiple years, enabling robust forecasting models.
	• Forecast Horizon: 3 months of future sales.

# Approach

## Feature Engineering

Around 20 new features were created to capture the trends, seasonality, and cyclic patterns in sales. Key features include:

	• Lag Features: Historical sales data to capture temporal dependencies.
	• Rolling Window Features: Moving averages and standard deviations over different windows to smooth out short-term fluctuations.
	• Exponential Weighted Means: For weighting recent data more heavily, capturing more recent trends.
	• Time-Based Indicators: Indicators for month, day, and season to capture seasonal patterns.

## Model Selection

The project applies both traditional time series models and machine learning models:

	1. Traditional Models: ARIMA, SARIMA, and other autoregressive models to capture time-dependent patterns.
	2. Machine Learning Models: Algorithms such as Random Forest, XGBoost, and Linear Regression are tested to utilize the engineered features.
	3. Cross-Validation: Time series cross-validation with expanding window (forward chaining) using scikit-learn’s TimeSeriesSplit, including a 7-day gap to prevent overfitting.

## Evaluation Metrics

	• Root Mean Squared Error (RMSE): Primary metric for evaluating forecast accuracy.
	• Mean Absolute Error (MAE): Used to analyze forecast consistency.
