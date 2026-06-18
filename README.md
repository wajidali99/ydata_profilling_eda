# 📊 Automated EDA with YData Profiling — Telecom Churn Dataset

## Overview

This section of the project demonstrates the use of **YData Profiling** (formerly Pandas Profiling) to automate the entire Exploratory Data Analysis process on the Telco Customer Churn dataset containing **7,032 customer records** and **21 features**.

Instead of writing dozens of lines of code manually for each column, YData Profiling generates a **single comprehensive interactive HTML report** that covers everything a data scientist needs to understand a dataset — in just one line of code.

---

## Why YData Profiling?

In a real data science workflow, EDA is the most time-consuming step. A data scientist typically has to:

- Check data types for every column
- Count missing values
- Plot distributions for each feature
- Calculate correlations between variables
- Identify outliers and skewed columns
- Flag potential data quality issues

Doing all of this manually for a 21-column dataset takes **hours**. YData Profiling automates every single one of these steps and packages the results into a clean, interactive HTML report — reducing that effort to **under 2 minutes**.

---

## What the Report Contains

### 1. Dataset Overview
A high-level summary of the entire dataset including total rows, total columns, total missing values, duplicate rows, and memory usage. This gives an instant health check of the data before any analysis begins.

### 2. Variable Analysis (Per Column)
For every single column in the dataset, the report provides:

- **Data type** — numeric, categorical, boolean
- **Distinct values** — how many unique values exist
- **Missing values** — count and percentage
- **Distribution plot** — histogram or bar chart automatically generated
- **Min, Max, Mean, Median** — for numeric columns
- **Most frequent values** — for categorical columns

### 3. Correlations
An automatic correlation matrix is generated showing the relationship between all numeric variables. This includes:

- **Pearson correlation** — linear relationships
- **Spearman correlation** — rank-based relationships
- **Phik correlation** — works for both numeric and categorical

For our dataset, this confirmed what we found manually — `MonthlyCharges` has the strongest positive correlation with `Churn`, while `tenure` has a negative correlation.

### 4. Missing Values Analysis
A dedicated section showing exactly where missing values exist across the dataset, with both a count table and a visual heatmap. In our Telco dataset, this highlighted the 11 blank rows in `TotalCharges` that needed cleaning.

### 5. Warnings & Alerts
One of the most powerful features — YData Profiling automatically flags potential issues such as:

- **High cardinality** — columns with too many unique values
- **Skewed distributions** — columns that are not normally distributed
- **High correlation** — variables that are too similar to each other
- **Zeros/Constant columns** — columns with little variation

### 6. Interactions
Scatter plots between pairs of variables, showing how two features relate to each other visually — similar to a pair plot but built directly into the report.

---

## Key Findings from the Report

| Feature | Finding |
|---------|---------|
| `TotalCharges` | Had 11 missing values — flagged as warning |
| `MonthlyCharges` | Right-skewed distribution — most customers on lower plans |
| `tenure` | Bimodal distribution — peaks at both very low and very high tenure |
| `Churn` | Imbalanced — ~73% No, ~27% Yes |
| `SeniorCitizen` | Highly imbalanced — mostly 0 (non-senior) |
| `customerID` | Flagged as high cardinality — should be dropped before modeling |

---

## Manual EDA vs YData Profiling

| Task | Manual EDA | YData Profiling |
|------|-----------|-----------------|
| Check data types | `df.dtypes` | ✅ Automatic |
| Missing values | `df.isnull().sum()` | ✅ Automatic |
| Distribution plots | `sns.histplot()` per column | ✅ Automatic |
| Correlation matrix | `sns.heatmap(df.corr())` | ✅ Automatic |
| Outlier detection | Manual box plots | ✅ Automatic |
| Warnings & alerts | Not available | ✅ Automatic |
| **Time required** | **2-3 hours** | **2 minutes** |

---

## Code Used

```python
# Install
!pip install ydata-profiling

# Import
from ydata_profiling import ProfileReport

# Generate report
profile = ProfileReport(df, title="Telecom Churn EDA Report", explorative=True)

# View in notebook
profile.to_notebook_iframe()

# Export as HTML file
profile.to_file("telecom_churn_report.html")
```

---

## Important Note

While YData Profiling is an excellent tool for **quick automated analysis**, it does not replace manual EDA entirely. A data scientist still needs to:

- **Interpret** what the numbers and plots mean
- **Ask the right business questions** from the data
- **Decide** which features matter for modeling
- **Understand** domain context behind the numbers

YData Profiling gives you the **what** — your expertise gives you the **so what**.

---

## Output

The final output is a fully interactive **HTML report** (`telecom_churn_report.html`) that can be:

- Opened in any browser
- Shared with teammates or stakeholders
- Added to a GitHub repository
- Included as a portfolio deliverable

---

*Part of the Telecom Customer Churn Analysis & Prediction project.*
*By Wajid Ali Khan | NAVTTC AI Engineering | GitHub: wajidali99 | Hugging Face: Wajiddev99*
