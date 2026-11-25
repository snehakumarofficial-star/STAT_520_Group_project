# Predicting Wildfire Occurrence Using Meteorological Metrics: A Statistical and Machine Learning Approach

**Course:** STAT 520-01 — Applied Multivariate Analysis (Fall 2026)  
**Instructor:** Ryan Paul Lafler  
**Institution:** San Diego State University (SDSU)  
**Project Status:** In Progress — Intended Completion Date: **December 11, 2026**  
**Repository:** [github.com/snehakumarofficial-star/STAT_520_Group_project](https://github.com/snehakumarofficial-star/STAT_520_Group_project)

---

## Project Overview

Severe heat, prolonged drought, and high winds significantly amplify wildfire ignition risk across California and around the globe. This project investigates whether daily atmospheric measurements and multi-day environmental trends can reliably predict daily wildfire occurrence (`0` = No Fire, `1` = Fire Occurred).

Our end-to-end analytical pipeline combines:
1. **Data Ingestion, Cleaning & Feature Engineering:** Standardizing multi-decade meteorological and fire records, resolving missingness, and engineering 7-day lag metrics, diurnal temperature spreads, and wind-to-temperature ratios.
2. **Exploratory Data Analysis (EDA):** Examining distributions, seasonal trends, correlation structures, and group shifts between fire and non-fire days.
3. **Bivariate Inferential Hypothesis Testing:** Evaluating individual predictor differences using parametric (Welch's two-sample $t$-tests) and non-parametric (Mann–Whitney $U$, Chi-square tests of independence) methods alongside power analysis and effect sizes (Cohen's $d$)[cite: 10, 17].
4. **Multivariable Statistical Modeling:** Fitting a **Multiple Logistic Regression** model (with VIF multicollinearity screening) to quantify covariate-adjusted log-odds, odds ratios ($\exp(\beta)$), and practical operational risk scenarios.
5. **Machine Learning & Out-of-Sample Generalizability:** Training and tuning a **Random Forest Classifier** on historical California data (**Phase 1**) and evaluating external validity on a global wildfire dataset without retraining (**Phase 2**).

---

## Research Questions

* **Primary Question:** Can daily atmospheric measurements and multi-day environmental trends reliably predict whether a wildfire ignition occurs on a given day?[cite: 10]
* **Secondary Question (Generalizability):** To what extent does a predictive model trained on regional California weather data generalize when applied to broader, multi-source global wildfire records?

---

## Datasets

| Dataset | Source & Citation | Size & Structure | Role in Study |
| :--- | :--- | :--- | :--- |
| **California Weather and Fire Prediction Dataset (1984–2025) with Engineered Features** | [Georgia Southern University / Zenodo](https://scholars.georgiasouthern.edu/en/datasets/california-weather-and-fire-prediction-dataset-19842025-with-engi/) (NOAA Climate Data Online + CAL FIRE; DOI: `10.5281/zenodo.14712845`)[cite: 13, 15] | ~14,988 daily records, 14 features; binary target `FIRE_START_DAY` (`fire_occurrence`)[cite: 12, 13] | **Primary Cohort:** EDA, hypothesis testing, logistic regression, and Phase 1 Random Forest training/testing[cite: 10, 12] |
| **Global Wildfire Dataset** | [Kaggle](https://www.kaggle.com/datasets/vijayaragulvr/wildfire-prediction) (NASA FIRMS VIIRS + Open-Meteo reanalysis)[cite: 10, 14] | 118,858 spatial grid records, 17 numerical features; binary target `occured` (`fire_occurrence`)[cite: 14] | **External Validation Cohort:** Phase 2 out-of-domain generalizability testing[cite: 10] |

---
### Authorship by Notebook
* **`notebooks/EDA_and_datacleaning.ipynb`** — **Sneha Kumar**
* **`notebooks/EDA_and_datacleaning_v1.1.ipynb`** — **Sneha Kumar** & **Jwann Sy**
* **`notebooks/EDA Fire Data.ipynb`** — **Robin A.**
* **`notebooks/Stat_analysis_Twosample.ipynb`** — **Sneha Kumar**
* **`notebooks/Modeling_Logistic_and_ML.ipynb`** — **Sneha Kumar**

---
## Repository Structure & Notebook Directory

```text
STAT_520_Group_project/
├── data/
│   ├── raw/                  # Original raw datasets (Global dataset CSV)
│   └── processed/            # Cleaned and standardized analytical datasets
├── docs/
│   └── Final-Project-Paper-Outline.pdf
├── notebooks/
│   ├── EDA Fire Data.ipynb
│   ├── EDA_and_datacleaning.ipynb
│   ├── EDA_and_datacleaning_v1.1.ipynb
│   ├── Stat_analysis_Twosample.ipynb
│   └── Modeling_Logistic_and_ML.ipynb
└── README.md