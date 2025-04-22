# 🛒 Store Item Demand Forecasting

This project builds a robust time series forecasting model to predict daily sales for various items across multiple stores. By combining traditional time series techniques with advanced machine learning (LightGBM, Optuna), we deliver accurate demand forecasts to enhance inventory management and supply chain planning.

---

## 📚 Table of Contents

1. [Project Overview](#project-overview)  
2. [Data](#data)  
3. [Approach](#approach)  
   - [Feature Engineering](#feature-engineering)  
   - [Model Selection](#model-selection)  
   - [Evaluation Metrics](#evaluation-metrics)  
4. [Results](#results)  
5. [Future Work](#future-work)  

---

## 🧠 Project Overview

The goal is to forecast sales for **50 items** across **10 stores** over a 3-month horizon. This allows for proactive inventory management, optimized stock levels, and improved customer service. The project applies extensive feature engineering, time-aware cross-validation, and both ML and statistical models.

---

## 🗃️ Data

The dataset contains **daily sales records** with the following characteristics:

- 📦 50 unique items  
- 🏪 10 distinct stores  
- 📅 ~5 years of daily data  
- 📈 Forecasting Horizon: 3 months into the future  

---

## 🛠️ Approach

### 🔧 Feature Engineering

Over 20 features were created to capture trends, seasonality, and cyclic patterns in sales. Notable ones include:

- **Lag features** (e.g., 91-day lag to capture quarterly seasonality)  
- **Rolling averages and std devs** to smooth fluctuations  
- **Exponential weighted moving averages** for recent trend focus  
- **Calendar-based indicators**: weekday, month, quarter, is_weekend, is_month_start, etc.  

### 🤖 Model Selection

Three modeling strategies were evaluated:

1. **Statistical Models**: ARIMA, SARIMA (limited due to scale)
2. **Machine Learning Models**:
   - `LightGBM` (primary model)
   - `XGBoost`, `RandomForest`, and `LinearRegression` as benchmarks
3. **Tuning**:  
   - `Optuna` was used for LightGBM hyperparameter optimization  
   - Feature importances were analyzed using `SHAP`

### 📊 Evaluation Metrics

- **RMSE** – Root Mean Squared Error: Primary metric for penalizing large errors  
- **MAE** – Mean Absolute Error: For consistency in prediction quality  

Cross-validation was done using **TimeSeriesSplit** with an expanding window and a 7-day gap to prevent leakage.

---

## 📈 Results

- **Best performing model**: LightGBM with Optuna tuning  
- **MAE / RMSE** values (sample): _[Insert actual scores from notebook]_  
- **Key insights**:
  - Seasonality is strong around weekends and holidays  
  - Lag-based features contributed most to predictive power  
  - Model generalized well across both low- and high-volume stores  

---

## 🚀 Future Work

- Integrate external data: promotions, weather, holidays  
- Explore deep learning models like LSTM/Transformer  
- Build real-time forecasting pipeline with batch/stream ingestion  
- Deploy as an interactive dashboard (Streamlit/FastAPI)

---

## 📦 Run Locally

```bash
git clone https://github.com/Raghavgali/Store-Item-Forecasting.git
cd Store-Item-Forecasting
pip install -r requirements.txt
jupyter notebook
