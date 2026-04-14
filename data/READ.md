# 📈 Time Series Forecasting of U.S. Economic Indicators (CPI & Unemployment Rate)
> **Modeling and Forecasting U.S. Economic Indicators using ARIMA and SARIMA via the Box-Jenkins Methodology**  
> Stevens Institute of Technology —  Time Series Analysis I 

---

## 📌 Overview

This project applies the **Box-Jenkins methodology** to model and forecast two critical U.S. macroeconomic indicators:

- 📉 **Unemployment Rate (UNRATE)** — Monthly data sourced from FRED
- 📊 **Consumer Price Index (CPI)** — Monthly data sourced from FRED

The analysis covers stationarity testing, model identification, parameter estimation, diagnostic checking, and short-term forecasting — using **ARIMA** for non-seasonal data and **SARIMA** for seasonal patterns.

---

## 🎯 Objectives

- Apply the Box-Jenkins methodology end-to-end on real-world economic time series
- Use Augmented Dickey-Fuller (ADF) tests to assess and achieve stationarity
- Identify optimal ARIMA/SARIMA model orders using ACF, PACF, AIC, and BIC
- Validate models with Ljung-Box residual diagnostics
- Generate reliable short-term forecasts for CPI and Unemployment Rate

---

## 🗂️ Repository Structure

```
Time-Series-Analysis/
│
├── data/
│   ├── UNRATE.csv                          # U.S. Unemployment Rate (FRED)
│   └── cpiai.csv                           # U.S. CPI & Inflation (FRED)
│
├── outputs/
│   ├── Unemployment Rate forecast.png      # ARIMA forecast plot
│   └── Seasonal Forecast.png              # SARIMA forecast plot
│
├── reports/
│   ├── Research_Report.pdf        # Full report with appendix
│   └── FINAL-NON-SEASONAL.pdf    # Non-seasonal (UNRATE) analysis
│
└── README.md
```

---

## 📊 Datasets

| Dataset | Source | Frequency | Description |
|---|---|---|---|
| **UNRATE** | [FRED](https://fred.stlouisfed.org/series/UNRATE) | Monthly | % of U.S. labor force unemployed (from 1966) |
| **CPI** | [FRED](https://fred.stlouisfed.org/series/CPIAUCSL) | Monthly | U.S. Consumer Price Index (from 1913) |

Both datasets are complete with no missing values and exhibit non-stationary behavior with long-term trends.

---

## 🔬 Methodology

### 1. Exploratory Data Analysis
- Visualized raw time series for both UNRATE and CPI
- Identified non-stationarity, trends, and cyclical patterns
- CPI exhibited seasonal behavior; UNRATE showed gradual cyclical trends

### 2. Stationarity Testing — ADF Test
- **UNRATE**: Non-stationary → required **first-order differencing (d=1)**
- **CPI**: Seasonal non-stationarity → required **regular + seasonal differencing (d=1, D=1)**

### 3. Model Identification
- Used ACF and PACF plots post-differencing to identify AR and MA orders
- AIC/BIC criteria for model selection

| Series | Model | Order |
|---|---|---|
| Unemployment Rate | ARIMA | (0, 1, 1) |
| CPI | SARIMA | (1, 1, 1)(1, 1, 1)[12] |

### 4. Parameter Estimation
- **ARIMA(0,1,1)** for UNRATE: small positive drift capturing gradual upward trend
- **SARIMA(1,1,1)(1,1,1)[12]** for CPI: significant negative seasonal coefficients reflecting annual inflation cycles

### 5. Diagnostic Checking
- Residual analysis — no significant autocorrelation
- ACF plots of residuals confirmed white noise behavior
- **Ljung-Box test** validated both models as adequately fitted

### 6. Forecasting
- Generated short-term forecasts with 95% confidence intervals
- UNRATE: ARIMA forecast reflects stable near-term labor market projections
- CPI: SARIMA captures annual seasonality in inflation trends

---

## 📉 Results

### Unemployment Rate — ARIMA(0,1,1) Forecast
![Unemployment Rate Forecast](outputs/Unemployment%20Rate%20forecast.png)

### CPI — SARIMA(1,1,1)(1,1,1)[12] Seasonal Forecast
![Seasonal CPI Forecast](outputs/Seasonal%20Forecast.png)

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| **Python** | Core programming |
| **statsmodels** | ARIMA, SARIMA modeling |
| **pandas** | Data manipulation |
| **matplotlib / seaborn** | Visualization |
| **scipy / numpy** | Statistical tests |

---

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas numpy matplotlib statsmodels scipy
```

### Clone the Repository
```bash
git clone https://github.com/nidhigurukumar/Time-Series-Analysis.git
cd Time-Series-Analysis
```

### Run the Analysis
```bash
# If a notebook/script is available
jupyter notebook time_series_analysis.ipynb
# or
python time_series_analysis.py
```

---

## 📋 Key Findings

- **ARIMA(0,1,1)** effectively modeled the non-seasonal unemployment rate, capturing gradual labor market trends
- **SARIMA(1,1,1)(1,1,1)[12]** successfully captured annual seasonality and inflationary cycles in CPI
- Both models passed Ljung-Box diagnostics, confirming no remaining autocorrelation in residuals
- The Box-Jenkins approach proved versatile for both seasonal and non-seasonal economic time series

---

## 📄 Report

Full methodology, statistical tests, model outputs, and appendix available in:  
📎 [`Research_Report.pdf`](reports/Research_Report.pdf)

---


