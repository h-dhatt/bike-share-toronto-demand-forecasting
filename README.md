# Bike Share Toronto Demand Forecasting (2024)

## Project Overview
This project analyzes Bike Share Toronto ridership patterns and builds short-term demand forecasts using historical trip and weather data. The goal is to understand seasonal trends, weekday patterns, and the extent to which simple forecasting models can predict daily ridership.

The analysis focuses on January–September 2024 and compares a baseline seasonal model against an improved regression-based approach.

---

## Data Sources
- **Bike Share Toronto Ridership Data (2024)**  
  Trip-level data published by the City of Toronto Open Data portal.
  Raw Bike Share trip files are not included due to size constraints; processed daily datasets are provided for reproducibility.

- **Daily Weather Data (Toronto City Centre)**  
  Environment and Climate Change Canada historical daily climate data.

---

## Data Preparation
- Combined monthly trip-level CSV files into a single dataset
- Aggregated trips to **daily ridership**
- Created time-based features (day of week, month, weekend indicator)
- Merged daily ridership with daily weather variables
- Engineered lag features (previous day, same weekday last week)

---

## Exploratory Analysis
Key patterns observed:
- Strong seasonal growth in ridership from winter into summer
- Clear weekday effects, with midweek days showing higher average usage
- A strong positive relationship between temperature and daily trips  
  (correlation ≈ 0.91)

---

## Forecasting Approach

### Baseline Model
- **Seasonal naïve (lag-7)**  
  Forecasts daily trips using ridership from the same weekday in the previous week.

### Improved Model
- **Linear regression** using:
  - Lagged ridership (1-day and 7-day)
  - Day-of-week indicators
  - Mean temperature
  - Daily precipitation

Models were evaluated on the **last 28 days** of data.

---

## Model Performance

| Model | MAE (trips) | MAPE |
|-----|------------|------|
| Baseline (Lag-7) | 3,193 | 11.33% |
| Improved Regression | 2,533 | 8.24% |

The improved model reduced average error by approximately **27%** relative to the baseline, though it still tended to underpredict extreme peak days.

An approximate 95% prediction interval was constructed using training residuals, covering **96.4%** of test-period observations.

---

## Dashboard
An interactive Power BI report was created with two pages:
1. **Demand Overview** – daily trends, seasonality, weekday patterns, and weather relationships
2. **Forecasting** – comparison of actual ridership against baseline and improved forecasts, including uncertainty bands

### Demand Overview
![Demand Overview Dashboard](images/overview_dashboard.jpg)

### Forecasting
![Forecasting Dashboard](images/forecast_dashboard.jpg)
---

## Limitations
- Analysis covers January–September 2024 only
- Weather effects are modeled linearly and may not capture extreme conditions
- Forecasts are short-term and not intended for operational deployment

---

## Tools Used
- Python (pandas, matplotlib, scikit-learn)
- Kaggle Notebooks
- Power BI
- GitHub
