# HR Employee Attrition Analysis

## Project Overview

This project analyzes employee attrition patterns using Python and Exploratory Data Analysis (EDA). The objective is to identify factors contributing to employee turnover and provide business recommendations to improve retention.

---

## Dataset

Dataset: IBM HR Employee Attrition Dataset

Rows: 1470

Columns: 35

After cleaning: 32 columns

---

## Tools & Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## Project Workflow

1. Data Loading
2. Data Understanding
3. Data Cleaning
4. Feature Engineering
5. Core Analysis (GroupBy)
6. Advanced Analysis
7. Visualization
8. Business Insights

---

## Visualizations

- Employee Attrition by Department
- Overall Attrition Rate
- Age Distribution of Employees Who Left
- Correlation Heatmap
- Monthly Income Distribution by Department

---

## Key Business Insights

### 1. Department Attrition

Research & Development records the highest attrition count (133 employees). Potential workload and career growth concerns should be investigated.

### 2. Overtime Impact

Employees working overtime show approximately 30% attrition compared to 10% among employees without overtime.

### 3. Age Group Analysis

Young employees demonstrate elevated attrition patterns indicating possible early career dissatisfaction.

### 4. Salary & Job Role

Managers and Research Directors earn significantly more than operational roles.

### 5. High Risk Employees

Employees with overtime and low satisfaction require early intervention.

### 6. Correlation Findings

Monthly income strongly correlates with JobLevel and TotalWorkingYears.

---

## Business Recommendations

- Reduce overtime burden
- Improve career growth opportunities
- Review compensation structures
- Strengthen employee engagement programs

---

## Project Structure

hr-employee-attrition-analysis/

├── notebook/

│ └── HR_Attrition_Analysis.ipynb

├── data/

│ └── WA_Fn-UseC_-HR-Employee-Attrition.csv

├── outputs/

│ ├── cleaned_hr_data.csv

│ └── dept_attrition_summary.csv

├── visuals/

│ ├── attrition_by_dept.png

│ ├── attrition_rate_pie.png

│ ├── age_distribution.png

│ ├── correlation_heatmap.png

│ └── salary_boxplot.png

└── README.md



