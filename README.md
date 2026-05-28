# Medical Insurance Cost Dataset Analysis

> **Comprehensive exploratory data analysis of a medical insurance cost dataset with 7,500 records, featuring advanced segment analysis, correlation matrices, and distribution visualizations.**

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Pandas](https://img.shields.io/badge/pandas-1.3+-green.svg)](https://pandas.pydata.org/)
[![Colab](https://img.shields.io/badge/Open%20in-Colab-orange?logo=google-colab)](https://colab.research.google.com)

---

## Table of Contents

- [Overview](#overview)
- [Dataset Description](#dataset-description)
- [Visual Analysis](#visual-analysis)
  - [Distribution Charts](#1-distribution-charts)
  - [Correlation & Bivariate Analysis](#2-correlation-analysis--bivariate-matrix)
  - [Advanced Segment Analysis](#3-advanced-segment-analysis)
- [Key Findings](#key-findings)
- [Installation](#installation)
- [Usage](#usage)
- [Statistical Insights](#statistical-insights)
- [Data Quality](#data-quality)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

This project delivers a comprehensive exploratory data analysis (EDA) of a medical insurance cost dataset containing **7,500 customer records** across **16 variables**. The analysis explores relationships between demographic factors, lifestyle choices, health indicators, and annual medical costs through advanced visualizations and statistical testing.

**Key Focus Areas:**
- 📊 Univariate & multivariate distribution analysis
- 🔗 Correlation matrices and bivariate relationships
- 🏥 Advanced segment analysis by region, occupation, and lifestyle
- 📈 Statistical hypothesis testing and validation

---

## Dataset Description

### Variables

| Variable | Type | Description | Range/Values |
|----------|------|-------------|--------------|
| `customer_id` | String | Unique identifier | MIC100001 - MIC107500 |
| `age` | Integer | Customer age in years | 18 - 65 |
| `gender` | Categorical | Biological sex | Male, Female |
| `bmi` | Float | Body Mass Index | 16.0 - 45.0 |
| `children` | Integer | Number of dependent children | 0 - 5 |
| `smoker` | Categorical | Smoking status | Yes, No |
| `region` | Categorical | Geographic region | Northeast, Northwest, Southeast, Southwest, Central |
| `occupation` | Categorical | Employment type | Driver, Doctor, Teacher, Engineer, Nurse, Lawyer, etc. |
| `annual_income_usd` | Integer | Annual income in USD | 18,000 - 176,977 |
| `exercise_level` | Categorical | Physical activity level | Low, Moderate, High |
| `chronic_diseases` | Integer | Number of chronic conditions | 0 - 5 |
| `doctor_visits_per_year` | Integer | Annual physician visits | 0 - 15 |
| `hospitalizations_last_year` | Integer | Hospital admissions (prior year) | 0 - 3 |
| `alcohol_consumption_per_week` | Integer | Weekly alcohol units | 0 - 14 |
| `insurance_plan` | Categorical | Coverage tier | Basic, Standard, Gold, Premium |
| `annual_medical_cost_usd` | Float | Target variable - annual medical costs | 1,500 - 49,333 |

**Dataset Size:** 7,500 records × 16 variables  
**Missing Values:** None  
**Duplicate Rows:** None

---

## Visual Analysis

### 1. Distribution Charts

<img src="https://raw.githubusercontent.com/Riddhi712/CodeAlpha_Data_Analysis_Task_2/main/Distribution%20Charts.png" alt="Distribution Charts" width="600">

**Key Observations from Distribution Analysis:**

| Metric | Value | Interpretation |
|--------|-------|--------------|
| **Mean Medical Cost** | $17,913 | Higher than median due to right skew |
| **Median Medical Cost** | $16,362 | More representative central tendency |
| **Age Distribution** | Uniform (18-65) | Evenly distributed across working ages |
| **BMI Peak** | ~25-30 | Centered in overweight category |
| **Income Floor** | $18,000 | Artificial minimum affecting 3.5% of records |

**Critical Findings:**
- 🚬 **Smoking Impact:** Smokers average **$29,152** vs non-smokers **$15,170** — a **92% increase**
- 🏃 **Exercise Benefit:** High exercise reduces costs by **17.6%** ($19,563 → $16,110)
- 🏥 **Plan Tier Effect:** Gold plans show highest average costs ($23,559), suggesting adverse selection
- 📉 **Chronic Disease Prevalence:** 49.8% have zero chronic diseases; 7 have 5+ conditions

---

### 2. Correlation Analysis & Bivariate Matrix

<img src="https://raw.githubusercontent.com/Riddhi712/CodeAlpha_Data_Analysis_Task_2/main/Correlation%20Analysis%20and%20Bivariate%20Matrix.png" alt="Correlation Analysis and Bivariate Matrix" width="700">

**Correlation Matrix Insights:**

| Variable Pair | Correlation | Strength | Interpretation |
|---------------|-------------|----------|----------------|
| **Smoker × Medical Cost** | **r = 0.73** | **Strong** | 🔥 Dominant cost driver |
| **Chronic Diseases × Cost** | **r = 0.38** | **Moderate** | Key health indicator |
| **Doctor Visits × Cost** | **r = 0.34** | **Moderate** | Utilization drives costs |
| **Hospitalizations × Cost** | **r = 0.24** | **Weak-Moderate** | Acute care impact |
| **Age × Cost** | **r = 0.16** | **Weak** | Age alone not predictive |
| **BMI × Cost** | **r = 0.07** | **Very Weak** | BMI less impactful than expected |
| **Income × Cost** | **r = 0.02** | **Negligible** | Wealth doesn't drive spending |

**Bivariate Scatter Analysis:**
- **Age vs Cost by Smoking:** Clear separation — smokers (red) cluster at higher costs across all ages
- **BMI vs Cost by Exercise:** Exercise level shows minimal cost differentiation at given BMI
- **Chronic Diseases Boxplot:** Dramatic cost escalation with each additional disease (0 diseases: ~$15K → 5 diseases: ~$35K+)

---

### 3. Advanced Segment Analysis

<img src="https://raw.githubusercontent.com/Riddhi712/CodeAlpha_Data_Analysis_Task_2/main/Advanced%20segment%20analysis.png" alt="Advanced Segment Analysis" width="700">

**Regional & Occupational Insights:**

| Segment | Average Cost | Notable Finding |
|---------|--------------|-----------------|
| **Southwest Region** | $18,114 | Highest regional costs |
| **Central Region** | $17,598 | Lowest regional costs |
| **Teachers** | $18,441 | Highest occupational costs |
| **Office Workers** | $17,344 | Lowest occupational costs |
| **Regional Variance** | $516 | Relatively small (2.9%) |
| **Occupational Variance** | $1,097 | Larger (6.3%) |

**Alcohol Consumption Analysis:**
- **0-2 drinks/week:** Baseline cost ~$17,500
- **3-5 drinks/week:** Slight increase to ~$18,000
- **6-10 drinks/week:** Cost decline (counterintuitive — possible healthy user bias)
- **11-15 drinks/week:** Cost stabilization
- **Doctor visits peak** at 3-5 drinks/week, then decline

**Income vs Medical Cost by Insurance Plan:**
- **Flat trend line** (slope = -0.0050) confirms **no income-cost relationship**
- **Premium plans** (yellow) cluster at higher costs regardless of income
- **Basic plans** (green) concentrated at lower cost ranges
- **Adverse selection evident:** Higher-cost individuals gravitate toward Gold/Premium plans

---

## Key Findings

### Primary Cost Drivers (Ranked by Impact)

| Rank | Factor | Impact | Evidence |
|------|--------|--------|----------|
| 1 | **Smoking Status** | **+$13,982 (92%)** | t = 93.3, p < 0.001 |
| 2 | **Chronic Diseases** | **+$20,000+ (5 diseases)** | r = 0.38, p < 0.001 |
| 3 | **Insurance Plan Tier** | **+$7,000 (Gold vs Basic)** | F = 274.7, p < 0.001 |
| 4 | **Doctor Visits** | **+$15,000 (15 visits)** | r = 0.34, p < 0.001 |
| 5 | **Exercise Level** | **-$3,453 (High vs Low)** | Observable difference |
| 6 | **Age** | **+$5,000 (18→65)** | r = 0.16, weak |
| 7 | **BMI** | **Minimal** | r = 0.07, negligible |
| 8 | **Income** | **None** | r = 0.02, p = 0.159 |

### Surprising Discoveries

1. **Income Irrelevance:** Annual income has virtually no correlation with medical costs — healthcare needs are health-driven, not wealth-driven
2. **BMI Weakness:** Despite common assumptions, BMI shows minimal cost correlation (r = 0.07)
3. **Exercise Paradox:** High exercise shows cost reduction, but moderate vs. high exercise differentiation is minimal
4. **Alcohol Non-Linearity:** Alcohol consumption shows non-monotonic cost relationship, suggesting complex health behaviors

---


### requirements.txt
```
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
scipy>=1.7.0
```

---

## Usage


## Statistical Insights

### Hypothesis Testing Results

| Hypothesis | Test | Statistic | P-Value | Verdict |
|------------|------|-----------|---------|---------|
| Smoking increases costs | Independent t-test | t = 93.317 | < 0.001 | ✅ **Confirmed** |
| Insurance plans differ | One-way ANOVA | F = 274.735 | < 0.001 | ✅ **Confirmed** |
| Age correlates with cost | Pearson correlation | r = 0.159 | < 0.001 | ✅ **Weak positive** |
| BMI correlates with cost | Pearson correlation | r = 0.066 | < 0.001 | ⚠️ **Negligible** |
| Income correlates with cost | Pearson correlation | r = 0.016 | 0.159 | ❌ **Rejected** |
| Chronic diseases correlate | Pearson correlation | r = 0.376 | < 0.001 | ✅ **Confirmed** |
| Gender affects smoking | Chi-square test | χ² = 0.042 | 0.838 | ❌ **No association** |

### Effect Sizes

| Factor | Effect Size | Interpretation |
|--------|-------------|----------------|
| Smoking | Cohen's d = 2.15 | **Very large effect** |
| Insurance Plan | η² = 0.099 | **Medium effect** |
| Chronic Diseases | r² = 0.141 | **Medium effect** |
| Age | r² = 0.025 | **Small effect** |

---

## Data Quality

### Issues Identified

| Issue | Severity | Description | Recommendation |
|-------|----------|-------------|----------------|
| **Income Floor** | Medium | 259 records (3.5%) at exactly $18,000 | Flag for income analysis; exclude if modeling |
| **Right-Skewed Costs** | Low | Skewness = 0.858 | Apply log transformation for regression |
| **BMI Boundaries** | Low | Hard limits at 16.0 and 45.0 | Verify against clinical standards |
| **Zero Inflation** | Low | 49.8% zero chronic diseases | Legitimate — use zero-inflated models if needed |



```

---
