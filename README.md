# us-cancer-death-rate-analysis
Analyzing how income, poverty, unemployment, and healthcare access predict cancer death rates across 3,044 U.S. counties using linear regression, VIF diagnostics, and 10-fold cross-validation in R.


# 🏥 U.S. Cancer Death Rate Analysis

Analyzing how income, poverty, unemployment, and healthcare access predict cancer death rates across 3,044 U.S. counties using linear regression, VIF diagnostics, and 10-fold cross-validation in R.

📄 See the full project report: [SocioeconomicDemographicDR.pdf](SocioeconomicDemographicDR.pdf)

---

## 📋 Project Overview

Cancer mortality in the United States is not uniformly distributed — socioeconomic conditions play a measurable role in shaping outcomes across communities. This project uses county-level public health data to investigate which demographic and economic factors most strongly predict cancer death rates, and builds progressively refined regression models to quantify those relationships.

**Author:** Jayant Manem

---

## 📁 Repository Structure

```
us-cancer-death-rate-analysis/
│
├── SocioeconomicDemographicCancerDR.Rmd   # R Markdown analysis
├── dataset1-3.csv                          # U.S. county-level dataset
├── SocioeconomicDemographicDR.pdf          # Full rendered report
└── README.md
```

---

## 📊 Dataset

- **3,044 U.S. county observations** (5 removed due to missing data)
- Source: U.S. government public health repositories
- Outcome variable: `deathRate` — average cancer deaths per 100,000 people per county
- Predictors include: median income, poverty rate, unemployment, median age, household size, marriage rate, education levels, private/public insurance coverage, and birth rate

---

## 🔍 Analysis Pipeline

**Exploratory Data Analysis**
- Compared cancer death rates across high vs. low income counties
- Two-sample t-test to assess statistical significance of income group differences
- Correlation heatmap to identify relationships between all predictors and the outcome

**Geographic Visualization**
- Distribution of cancer death rates across U.S. counties by mortality quartile
- Reveals regional disparities, with southeastern and Appalachian counties showing elevated death rates

**Multicollinearity Check**
- Variance Inflation Factor (VIF) analysis performed before modeling
- Identified collinear predictors (e.g., medIncome & povertyPercent, private & public coverage)
- Results informed predictor selection for Model 3

---

## 🤖 Models

| Model | Predictors | Adj. R² | Avg. RMSE |
|---|---|---|---|
| Model 1 | povertyPercent, medIncome, PctUnemployed16_Over | 0.2274 | 24.39 |
| Model 2 | Model 1 + MedianAge, PctPrivateCoverage, PctPublicCoverage, BirthRate | 0.2364 | 24.31 |
| Model 3 (VIF-Refined) | Low-VIF predictors only | 0.2076 | 24.74 |

All models validated with residual diagnostics (histogram + Q-Q plot) and 10-fold cross-validation.

---

## 📈 Key Findings

- Higher poverty and unemployment rates are strongly associated with increased cancer death rates
- Higher median income is associated with lower cancer mortality
- Model 2 achieved the best predictive performance (lowest RMSE)
- Model 3 demonstrated that a multicollinearity-corrected model can achieve competitive performance with fewer, more stable predictors
- Geographic analysis revealed substantial regional disparities in cancer mortality across U.S. counties

---

## 🚀 How to Run

### 1. Clone the repository
```bash
git clone https://github.com/jayantm1216/us-cancer-death-rate-analysis.git
```

### 2. Open in RStudio
Open `SocioeconomicDemographicCancerDR.Rmd` in RStudio.

### 3. Install required packages
```r
install.packages(c("ggplot2", "caret", "corrplot", "car", "maps", "dplyr", "knitr"))
```

### 4. Knit to PDF
Click **Knit → Knit to PDF** in RStudio.

---

## 🛠️ Requirements

- R 4.3.2+
- ggplot2
- caret
- corrplot
- car
- maps
- dplyr
- knitr

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
