# Multi-Echelon Inventory Demand Forecasting System

![Python](https://img.shields.io/badge/Python-3.7%2B-blue) ![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange) ![Pandas](https://img.shields.io/badge/Library-Pandas-150458) ![Status](https://img.shields.io/badge/Status-Prototype-green)

## 📋 Project Overview
This project implements a **Demand Forecasting System** designed for high-volume retail travel stops. It utilizes historical sales data, weather conditions, and holiday schedules to predict SKU-level demand for the next 14 days.

The system addresses common supply chain challenges such as **data volatility**, **missing historical records (SAP outages)**, and **seasonal demand spikes**. It concludes by generating an order file formatted specifically for ingestion by SAP ERP systems, including calculated safety stock buffers.

## 🚀 Key Features

* **Synthetic Data Generator**: Simulates 3 years of industrial retail data, including:
    * Sales patterns with seasonality (Summer/Winter spikes).
    * Randomized "SAP system failures" (missing data points).
    * External factors (Temperature, Precipitation, Holidays).
* **Robust Data Cleaning**: Handles missing time-series data using **Linear Interpolation**, ensuring continuity for lag-based features.
* **Feature Engineering**:
    * **Lag Features**: 7-day lags to capture weekly travel patterns.
    * **Rolling Statistics**: 7-day and 30-day moving averages.
    * **Volatility Metrics**: Rolling standard deviation to identify unstable products.
* **Machine Learning Model**: Uses a **Random Forest Regressor** to capture non-linear relationships between weather, holidays, and sales.
* **Safety Stock Logic**: Automatically calculates dynamic safety stock buffers for volatile SKUs to prevent stockouts.

## 🛠️ Technology Stack

* **Language**: Python 3.x
* **Data Manipulation**: Pandas, NumPy
* **Machine Learning**: Scikit-Learn (RandomForestRegressor)
* **Deployment**: Docker (Containerization ready)

## 📂 Project Structure

```bash
├── multi_echelon_inventory_forecast.py   # Main pipeline script
├── Dockerfile                            # Container configuration
├── requirements.txt                      # Python dependencies
├── README.md                             # Project documentation
└── data/                                 # Generated CSVs (created at runtime)
    ├── historical_sales_sap.csv
    ├── weather_data.csv
    ├── holiday_data.csv
    └── final_sap_orders.csv
