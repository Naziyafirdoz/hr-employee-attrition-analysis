# Cleaning Log — HR Employee Attrition Analysis

This log documents the sequence of data preparation and transformation steps performed in notebook/HR_Attrition_Analysis.ipynb. Each entry explains purpose, method, and the business reason for the operation. All steps are taken directly from the notebook and do not invent additional transformations.

## 1. Dataset loading
- Purpose: Load the source CSV into a working DataFrame for analysis.
- Method: pd.read_csv("data/WA_Fn-UseC_-HR-Employee-Attrition.csv")
- Business reason: Start analysis from the raw IBM HR Employee Attrition dataset.

## 2. Initial inspection and shape
- Purpose: Understand raw dataset size and columns.
- Method: df.head(), df.shape, df.info()
- Notebook outputs: original shape reported as (1470, 35).
- Business reason: Confirm data volume is sufficient for cohort analysis and that types are as expected.

## 3. Missing value checking
- Purpose: Identify null or missing entries that need handling.
- Method: df.isnull().sum()
- Business reason: Ensure data completeness and identify fields requiring imputation or removal before aggregation. The notebook uses this check to confirm that no major missingness blocks the EDA.

## 4. Duplicate checking
- Purpose: Remove exact duplicate records that could bias counts and rates.
- Method: df = df.drop_duplicates()
- Business reason: Ensure attrition counts are not inflated by duplicate rows; typical in published datasets.

## 5. Removing unneeded columns
- Purpose: Drop columns that are constant or not useful for analysis.
- Method: df = df.drop(columns = ["EmployeeCount", "Over18", "StandardHours"])
- Business reason: These columns provide no analytical value (e.g., constant values) and removing them simplifies downstream analysis and visuals.

## 6. Feature engineering — Attrition flag
- Purpose: Create a binary numeric target for easy calculations and grouping.
- Method: df["Attrition_Flag"] = df["Attrition"].apply(lambda x: 1 if x=="Yes" else 0)
- Business reason: Binary flag simplifies computation of attrition rates (means) and is suitable for modeling and group summaries.

## 7. Feature engineering — Salary Band
- Purpose: Bucket MonthlyIncome into human-friendly bands for stakeholder reporting.
- Method: A salary_band function is defined in the notebook and applied: df["Salary Band"] = df["MonthlyIncome"].apply(salary_band)
- Business reason: Salary bands are easier for non-technical stakeholders to interpret and compare than raw income values.

## 8. Feature engineering — Experience Level
- Purpose: Derive experience cohorts from TotalWorkingYears.
- Method: A mapping function exp_level is applied: df["Experience Level"] = df["TotalWorkingYears"].apply(exp_level)
- Business reason: Segmenting by experience (Junior/Mid/Senior) reveals different attrition dynamics and helps tailor retention programs.

## 9. Feature engineering — Age Group
- Purpose: Bucket Age into cohort labels (Young, Mid - Career, Experienced).
- Method: Notebook creates Age Group using an age binning function and assigns df["Age Group"].
- Business reason: Age cohorts help HR target early-career retention and succession planning.

## 10. Feature engineering — Risk Flag
- Purpose: Produce a compact high-risk/low-risk label to shortlist employees for intervention.
- Method: Notebook defines rules combining overtime and low satisfaction signals to label rows "High Risk" or "Low Risk" (df["Risk Flag"]).
- Business reason: Prioritize limited HR capacity to employees most likely to leave soon (cost-effective intervention).

## 11. GroupBy summaries
- Purpose: Compute attrition rates and aggregated summaries for stakeholder insight.
- Method: Examples from notebook:
  - Department attrition: summary = df.groupby("Department")["Attrition_Flag"].mean().reset_index()
  - Overtime vs attrition: df.groupby("OverTime")["Attrition_Flag"].mean() * 100
- Business reason: Simple group summaries quantify differences across units and signals and support recommendations.

## 12. Visualizations generated
- Purpose: Create static visual assets to communicate findings.
- Method: Matplotlib / Seaborn plots saved to visuals/ using plt.savefig(...)
- Business reason: Static charts are included in the repository (visuals/) for easy stakeholder sharing and inclusion in reports.

Generated visual files (examples):
- visuals/attrition_by_dept.png
- visuals/attrition_rate_pie.png
- visuals/age_distribution.png
- visuals/correlation_heatmap.png
- visuals/salary_boxplot.png

## 13. CSV exports
- Purpose: Persist cleaned data and summary tables.
- Method: df.to_csv("outputs/cleaned_hr_data.csv", index=False)
          summary.to_csv("outputs/dept_attrition_summary.csv", index=False)
- Business reason: Provides ready-to-use artifacts for dashboards, modeling, or client handoffs.

## 14. Final dataset shape
- Purpose: Document the final data available for downstream work.
- Notebook outputs: final shape reported as (1470, 33) after dropping unneeded columns and adding engineered features.
- Business reason: Shows the cleaned dataset retains full row coverage while adding analysis-ready variables.

---

Notes and limitations
- The notebook focuses on deterministic feature creation and descriptive summaries. It does not impute missing values because the initial null check indicated no blocking missingness for the analyzed columns.
- All engineering choices (band thresholds and bucket boundaries) are implemented in named functions within the notebook; refer to those functions for exact cut points when converting to a production pipeline.
