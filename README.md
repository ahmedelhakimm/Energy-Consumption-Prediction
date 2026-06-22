# Energy Consumption Prediction

A linear regression model that predicts building energy consumption (kWh) based on structural, environmental, and operational features. Built as part of the Data Mining course (CSEN911) at the German University in Cairo.

---

## Overview

Energy consumption varies significantly across buildings depending on size, type, location, occupancy, and temperature. This project builds a predictive model using real building data to estimate energy usage — a practical tool for electricity companies and urban planners.

---

## Dataset

The dataset contains building-level energy readings across multiple Egyptian governorates (Cairo, Giza, Alexandria). Each row represents a building observation with the following features:

| Feature | Description |
|---|---|
| Building Type | Residential, Commercial, Industrial, Educational |
| Governorate / Neighborhood | Location in Egypt |
| Square Footage (m²) | Total floor area |
| Average Temperature (°C) | Ambient temperature during measurement |
| Occupancy Level | Low / Medium / High |
| Appliances Usage Level | Low / Medium / High |
| Days Since Last Maintenance | Engineered from maintenance date |
| Day Type | Weekday or Weekend |
| **Energy Consumption (kWh)** | Target variable |

---

## Methodology

### 1. Data Cleaning
- Converted `SquareFootage` and `Energy_Consumption` from string format (e.g. `"450m2"`, `"1200 kWh"`) to numeric values
- Handled missing values: categorical columns filled with **mode**, numerical columns with **median**
- Standardized inconsistent entries in the `Neighborhood` and `Day_of_Week` columns

### 2. Feature Engineering
- Created `days_since_last_maintenance` from the maintenance date column
- Encoded ordinal features (`Occupancy_Level`, `Appliances_Usage_Level`) using ordinal encoding (Low=0, Medium=1, High=2)
- Encoded nominal features (`Building_Type`, `Governorate`, `Neighborhood`, `Day_Type`) using one-hot encoding
- Derived `day_type` (Weekday / Weekend) from `Day_of_Week`

### 3. Exploratory Data Analysis
Key findings from EDA:
- **Top neighborhoods by building count:** Smouha, Dokki, Gleem
- **Highest average energy consumption:** Industrial buildings
- **Widest distribution of consumption:** Residential buildings
- **Positive correlation:** Building size (m²) and energy consumption
- **No correlation:** Days since last maintenance and energy consumption
- **No multicollinearity** detected among features (all correlations below ±0.8)

### 4. Modelling
- Algorithm: **Linear Regression** (scikit-learn)
- Train/Test split: **80% / 20%** (random state = 42)

---

## Results

| Metric | Value |
|---|---|
| R² (R-squared) | **0.944** |
| MSE | 47,929 kWh² |
| RMSE | **218.9 kWh** |

The model explains **94.4%** of the variance in energy consumption, with an average prediction error of approximately **219 kWh** per building.

---

## Technologies

- Python 3
- pandas, NumPy
- scikit-learn
- Matplotlib, Seaborn
- Jupyter Notebook

---

## Course Info

**Course:** Data Mining (CSEN911) — Winter 2025  
**Institution:** German University in Cairo (GUC)  
**Instructor:** Dr. Ayman Alserafi
