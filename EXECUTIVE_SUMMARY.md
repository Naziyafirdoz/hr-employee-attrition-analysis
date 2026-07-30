# Executive Summary

## Business Problem

Why are employees leaving, and which interventions will most cost-effectively reduce attrition? This analysis identifies where turnover is concentrated and which employee signals indicate elevated risk so HR can prioritize targeted interventions.

## Dataset Overview

The analysis uses the IBM HR Employee Attrition dataset (1470 rows, original 35 columns). A cleaned, analysis-ready dataset with engineered features is available at outputs/cleaned_hr_data.csv. Key fields include Attrition, Department, OverTime, Age, MonthlyIncome, JobLevel, TotalWorkingYears, and survey-style satisfaction metrics.

## Key Findings

- Highest attrition department: Research & Development shows the highest raw attrition count in the dataset (133 employees). This unit should be prioritized for diagnosis and pilot interventions.

- Overtime impact: Employees who work overtime show substantially higher attrition (~30%) compared to employees not working overtime (~10%). Overtime is a clear risk signal in this dataset.

- Age group findings: Younger employees display elevated attrition rates relative to mid-career and senior cohorts, suggesting early-career dissatisfaction or role-fit issues.

- Salary observations: Monthly income is strongly associated with JobLevel and TotalWorkingYears; compensation alignment differs across roles and levels. Salary bands were created to simplify stakeholder reporting.

- Correlation findings: A correlation heatmap highlights strong relationships between MonthlyIncome, JobLevel, and TotalWorkingYears; other observed relationships warrant controlled analysis before causal claims.

- High-risk characteristics: The notebook flags employees as "High Risk" when overtime coincides with low satisfaction indicators. This shortlist can be used for immediate stay interviews or manager outreach.

## Business Impact

These findings help HR leaders prioritize where to allocate retention resources. Addressing high-attrition units (e.g., R&D), reducing chronic overtime, and improving early-career experiences are likely to reduce turnover and the associated recruitment and productivity costs.

## Recommendations

1. Prioritize Research & Development for an immediate diagnostic: conduct workload reviews, manager feedback sessions, and targeted stay interviews.
2. Pilot overtime reduction measures (staffing adjustments, task prioritization) in units with high overtime and attrition.
3. Launch early-career retention programs: mentoring, clearer promotion paths, and skill development for junior cohorts.
4. Review compensation competitiveness for high-turnover roles using Salary Band analysis; where budgets are constrained, focus on non-monetary retention levers.
5. Use the Risk Flag to run a focused outreach program (stay interviews) on the identified high-risk cohort before broader rollouts.

## Expected Business Benefits

- Lower turnover and recruitment costs by retaining employees at higher-risk points.
- Faster stabilization of affected teams (e.g., R&D) with preserved institutional knowledge.
- Improved workforce planning and targeted investments where they yield highest retention returns.

## Deliverables

- Notebook: notebook/HR_Attrition_Analysis.ipynb (analysis and narrative)
- Cleaned dataset: outputs/cleaned_hr_data.csv
- Visualizations: visuals/*.png (stakeholder-ready figures)
- Summary CSV: outputs/dept_attrition_summary.csv
- Repository: this project folder with README and supporting documents

---

For questions or a client-ready slide deck, contact the analyst (see README).