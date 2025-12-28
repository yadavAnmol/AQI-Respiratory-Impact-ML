# AQI Respiratory Impact Analysis (ML)

## Problem Statement
Air pollution is a known contributor to respiratory health issues, but its
yearly impact at the population level is complex and non-linear.  
This project analyzes the relationship between **Air Quality Index (AQI) metrics**
and **respiratory death rates** across U.S. counties (2000–2019) using
machine learning models.

The goal is to understand:
- Whether AQI indicators can explain variations in respiratory death rates
- Which AQI factors contribute most to respiratory health outcomes
- Whether non-linear models perform better than linear models

---

## Dataset Overview
- **Scope:** U.S. county-level data (year-wise)
- **Time period:** 2000–2019
- **Target variable:** `Resp Death Rate`
- **Key features:**
  - AQI exposure days (Good, Moderate, Unhealthy, etc.)
  - AQI intensity metrics (Max AQI, Median AQI, 90th Percentile AQI)
  - Pollutant-specific days (PM2.5, PM10, Ozone, NO2, CO)
  - Temporal feature (`year`)

---

## Methodology

### 1. Data Preprocessing
- Loaded data safely using `dtype=str` to prevent mixed-type corruption
- Removed duplicates and rows with missing values
- Dropped non-informative identifiers (`FIPS,YEAR`, `location_name`, `fips`)
- Converted all features to numeric format
- Applied time-aware train–test split (`shuffle=False`)
- Standardized features for linear modeling

---

### 2. Model Comparison

| Model | MAE | RMSE | R² |
|------|-----|------|----|
| Linear Regression | 6.43e-05 | 8.50e-05 | **0.057** |
| Random Forest Regressor | **5.98e-05** | **7.95e-05** | **0.175** |

**Key observation:**  
Random Forest significantly improved explanatory power, indicating that
the relationship between AQI and respiratory death rates is **non-linear**.

---

## Key Results & Insights

- **Random Forest improved R² by ~3×** compared to Linear Regression
- AQI alone explains only part of respiratory mortality, highlighting the
  influence of additional socio-economic and healthcare factors
- Model selection was driven by empirical evaluation, not assumptions

---

## Feature Importance Insights (Random Forest)

Top contributing features:
1. **Max AQI** — Extreme pollution events have the strongest impact
2. **Days with AQI** — Overall exposure frequency matters
3. **Good Days & Moderate Days** — Long-term air quality trends are highly informative
4. **Year** — Temporal trends reflect regulation, healthcare, and population changes
5. **PM2.5 & Ozone days** — More impactful than CO and NO2 at yearly scale

**Conclusion:**  
Cumulative and moderate pollution exposure influences respiratory health
more than rare hazardous events at an annual scale.

---

## Conclusion
This project demonstrates that:
- Linear models are insufficient for capturing AQI–health relationships
- Non-linear ensemble models provide better explanatory insight
- Feature importance analysis transforms predictions into actionable
  public-health understanding

This makes the model suitable for **risk analysis and trend interpretation**,
not individual-level medical prediction.

---

````md
## Repository Structure
AQI-Respiratory-Impact-ML/
│
├── project_3.ipynb
├── AQI_Respiratory_2000_2019.csv
├── README.md
└── .gitignore


---

## Technologies Used
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib
- Google Colab


