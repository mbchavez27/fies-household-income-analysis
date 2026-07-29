# Socioeconomic Determinants of Household Income in the Philippines

> Statistical analysis and predictive modeling of socioeconomic income determinants in the Philippines using Family Income and Expenditure Survey (FIES) microdata.

## 🎯 Study Objectives

This study aims to apply descriptive and inferential statistical methods to the FIES dataset to:

- **Characterize** the distribution of household income and expenditure across the Philippines.
- **Test** whether specific demographic and regional factors are significantly associated with income differences.
- **Build** a predictive regression model identifying the strongest socioeconomic determinants of household income.

---

## ❓ Primary Research Question

**What household and demographic factors are most significantly associated with variation in household income across the Philippines, and how do these factors differ by region?**

---

## 📊 Research Questions and Hypotheses

### Research Question 1: Regional Disparities

**RQ1:** Is there a significant difference in average household income across the different geographic regions of the Philippines?

- **Null Hypothesis ($H_0$):** There is no significant difference in average household income across the different regions of the Philippines; any observed differences are due to random variance.
- **Alternative Hypothesis ($H_1$):** There is a significant difference in average household income across at least two regions in the Philippines.

### Research Question 2: Demographic Associations

**RQ2:** To what extent are demographic characteristics significantly associated with household income levels?

- **Null Hypothesis ($H_0$):** There is no significant association between demographic characteristics and household income levels.
- **Alternative Hypothesis ($H_1$):** There is a significant positive or negative association between specific demographic characteristics (e.g., education, occupation) and household income levels.

### Research Question 3: Predictive Modeling

**RQ3:** Can a combination of regional and household demographic factors reliably predict a household's income, and which variable exerts the strongest determinant effect?

- **Null Hypothesis ($H_0$):** A multiple linear regression model utilizing regional and demographic variables does not significantly predict household income.
- **Alternative Hypothesis ($H_1$):** A multiple linear regression model utilizing regional and demographic variables significantly predicts household income.

---

## 🔑 Key Findings

### RQ1: Regional Disparities
- **Reject H₀.** Income differs significantly across Philippine regions (ANOVA F = 388.97, p < 0.001).
- **Effect size:** Region alone explains ~13% of income variance (η² = 0.130).
- **NCR** has the highest mean income; the NCR–ARMM gap is the largest (176% raw income difference).
- Robust to unequal variances (Welch's F = 465.81) and non-parametric testing (Kruskal-Wallis H = 6021.46).

### RQ2: Demographic Associations
- **Education** is the strongest demographic predictor (η² = 0.289, large effect).
- **Occupation** is second (η² = 0.201, large effect).
- **Class of worker** is medium (η² = 0.069).
- Sex, age, and marital status have small effects (η²/d < 0.05).

### RQ3: Predictive Model
- **Model 2 (with Region × Education interaction):** R² = 0.501, Adjusted R² = 0.500.
- **Education premium varies by region:** The interaction is jointly significant (F = 40.78, p ≈ 0).
- **Strongest predictor:** Education × NCR interaction (standardized β = 0.248).
- **Robustness:** Coefficients stable across full sample, without outliers, and without suspect-age rows.

---

## 📂 Notebooks

| # | Notebook | Description |
|---|----------|-------------|
| 01 | `01-data_cleaning.ipynb` | Data cleaning: null handling, typo fixes, log-transform, outlier flagging. Produces `preprocessed-fies.csv`. |
| 02 | `02-exploratory_data_analysis.ipynb` | EDA: 10 sections covering income distribution, regional analysis, demographics, household composition, assets, correlations. 15 figures. |
| 03 | `03-hypothesis_testing.ipynb` | Hypothesis testing: RQ1 (ANOVA, Welch's, Kruskal-Wallis, Tukey HSD), RQ2 (t-test, Pearson r, ANOVA, η² for 6 demographics). |
| 04 | `04-regression_modeling.ipynb` | Regression: OLS models with/without interaction, assumption checks, HC1 robust SEs, standardized coefficients, robustness checks. |
| 05 | `05-summary_insights.ipynb` | Synthesis: consolidated findings, cross-RQ interpretation, policy implications, limitations. |

---

## 📁 Project Structure

```
├── data/
│   └── preprocessed/
│       └── preprocessed-fies.csv        # Cleaned dataset (41,544 × 63)
├── notebooks/
│   ├── 01-data_cleaning.ipynb
│   ├── 02-exploratory_data_analysis.ipynb
│   ├── 03-hypothesis_testing.ipynb
│   ├── 04-regression_modeling.ipynb
│   └── 05-summary_insights.ipynb
├── outputs/
│   └── figures/                          # 26 generated PNGs
├── pyproject.toml                        # Dependencies (pandas, scipy, statsmodels, scikit-learn, etc.)
├── README.md
└── LICENSE                               # Apache 2.0
```

---

## 🚀 Getting Started

```bash
# Install dependencies
uv sync

# Run notebooks in order (01 → 02 → 03 → 04 → 05)
uv run jupyter notebook notebooks/
```

---

## ⚙️ Technical Details

- **Dataset:** FIES microdata, n = 41,544 households, 63 columns
- **Outcome:** Log Total Household Income (skewness reduced from 8.90 to 0.38)
- **Statistical significance:** α = 0.05; effect sizes reported alongside p-values
- **Robustness:** Welch's ANOVA, Kruskal-Wallis, HC1 robust standard errors, coefficient stability checks
- **Environment:** Python 3.11+, managed via `uv`
