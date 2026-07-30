# Data Dictionary — IBM HR Employee Attrition Dataset

This data dictionary documents the primary columns used in this project, their types, example values, and business meaning. Use this as a quick reference when reviewing the notebook, cleaned dataset (outputs/cleaned_hr_data.csv), or building downstream models and dashboards.

---

Age
- Data Type: Integer
- Description: Employee age in years
- Example Values: 22, 34, 49
- Business Meaning: Proxy for career stage; age cohorts often have different retention dynamics and benefits expectations.

Attrition
- Data Type: Categorical (string)
- Description: Original dataset label indicating whether the employee left the company
- Example Values: Yes, No
- Business Meaning: Primary target/indicator of turnover events used to compute attrition rates and derived flags.

Attrition_Flag
- Data Type: Integer (binary)
- Description: Engineered binary flag derived from Attrition (Yes -> 1, No -> 0)
- Example Values: 1, 0
- Business Meaning: Easier to use in calculations and visualizations (percentages, group means) and as a modeling target.

BusinessTravel
- Data Type: Categorical
- Description: Frequency of business travel
- Example Values: Travel_Rarely, Travel_Frequently, Non-Travel
- Business Meaning: Travel intensity may affect work-life balance and attrition risk for certain roles.

Department
- Data Type: Categorical
- Description: Organizational department where the employee works
- Example Values: Sales, Research & Development, Human Resources
- Business Meaning: Useful for grouping attrition by organizational unit to prioritize interventions.

DistanceFromHome
- Data Type: Integer
- Description: Distance in miles (or nearest unit) from employee home to workplace
- Example Values: 1, 8, 24
- Business Meaning: May relate to commute burden; can influence retention, particularly for lower-paid roles.

Education
- Data Type: Integer (ordinal)
- Description: Education level coded numerically (higher = more education)
- Example Values: 1, 3, 5
- Business Meaning: Controls for qualifications that may correlate with job level, pay, and mobility.

EducationField
- Data Type: Categorical
- Description: Primary field of study
- Example Values: Life Sciences, Medical, Marketing, Other
- Business Meaning: May be relevant for skill-based attrition patterns in specialized roles.

EnvironmentSatisfaction
- Data Type: Integer (ordinal)
- Description: Employee reported satisfaction with the work environment (1–4)
- Example Values: 1, 3, 4
- Business Meaning: Low values indicate dissatisfaction that could drive turnover; used for risk segmentation.

Gender
- Data Type: Categorical
- Description: Employee gender
- Example Values: Male, Female
- Business Meaning: Useful for demographic analysis of attrition and equity reviews.

HourlyRate
- Data Type: Integer
- Description: Hourly wage rate
- Example Values: 40, 72, 97
- Business Meaning: Compensation component used alongside MonthlyIncome to understand pay structure.

JobInvolvement
- Data Type: Integer (ordinal)
- Description: Self/manager-reported involvement level in job (1–4)
- Example Values: 1, 3, 4
- Business Meaning: Lower involvement can be an early-warning sign for attrition risk.

JobLevel
- Data Type: Integer (ordinal)
- Description: Organizational level of the job (1 = entry, higher = senior levels)
- Example Values: 1, 3, 5
- Business Meaning: Strongly linked to pay and responsibility; used as a control and explanatory variable.

JobRole
- Data Type: Categorical
- Description: Specific functional role title
- Example Values: Sales Executive, Research Scientist, Laboratory Technician
- Business Meaning: Role-specific attrition patterns help target role-level interventions.

JobSatisfaction
- Data Type: Integer (ordinal)
- Description: Employee reported job satisfaction (1–4)
- Example Values: 1, 2, 4
- Business Meaning: Directly related to retention; used to identify high-risk employees when combined with other signals.

MaritalStatus
- Data Type: Categorical
- Description: Marital status of the employee
- Example Values: Single, Married, Divorced
- Business Meaning: May correlate with mobility and commitment factors affecting attrition.

MonthlyIncome
- Data Type: Integer
- Description: Monthly base income
- Example Values: 2028, 5993, 15427
- Business Meaning: Key compensation variable — used to create Salary Band and analyze pay-related retention effects.

MonthlyRate
- Data Type: Integer
- Description: Internal pay rate code or monthly compensation proxy
- Example Values: 19479, 24907, 23159
- Business Meaning: Auxiliary pay field in the original dataset; MonthlyIncome is primary for business interpretation.

NumCompaniesWorked
- Data Type: Integer
- Description: Number of prior employers
- Example Values: 0, 2, 8
- Business Meaning: Proxy for job mobility and experience; higher counts may indicate higher turnover propensity.

OverTime
- Data Type: Categorical (Yes/No)
- Description: Whether the employee works overtime
- Example Values: Yes, No
- Business Meaning: Strongly associated with attrition in this analysis; used to identify high-risk employees.

PercentSalaryHike
- Data Type: Integer
- Description: Most recent salary increase percentage
- Example Values: 11, 20, 23
- Business Meaning: Compensation movement; useful to evaluate retention after raises.

PerformanceRating
- Data Type: Integer
- Description: Recent performance rating (typically 3–4 in this dataset)
- Example Values: 3, 4
- Business Meaning: Helps identify whether high performers are leaving and correlate performance with attrition.

RelationshipSatisfaction
- Data Type: Integer (ordinal)
- Description: Satisfaction with workplace relationships (1–4)
- Example Values: 1, 3, 4
- Business Meaning: Social factors that influence retention and engagement.

StockOptionLevel
- Data Type: Integer
- Description: Stock option level awarded to the employee
- Example Values: 0, 1, 2
- Business Meaning: Long-term compensation component influencing retention for senior staff.

TotalWorkingYears
- Data Type: Integer
- Description: Total years of professional experience
- Example Values: 0, 6, 17
- Business Meaning: Used to derive Experience Level; controls for tenure and marketability.

TrainingTimesLastYear
- Data Type: Integer
- Description: Number of training sessions the employee attended last year
- Example Values: 0, 3, 5
- Business Meaning: Investment in development; low values combined with other factors may signal disengagement.

WorkLifeBalance
- Data Type: Integer (ordinal)
- Description: Self-reported work-life balance (1–4)
- Example Values: 1, 3, 4
- Business Meaning: Directly tied to burnout and overtime; relevant for retention strategies.

YearsAtCompany
- Data Type: Integer
- Description: Number of years the employee has been with the company
- Example Values: 0, 5, 25
- Business Meaning: Tenure metric used for retention segmentation and promotion pipeline planning.

YearsInCurrentRole
- Data Type: Integer
- Description: Years in the current role
- Example Values: 0, 3, 7
- Business Meaning: Short tenure in role may signal role mismatch or rapid progression.

YearsSinceLastPromotion
- Data Type: Integer
- Description: Years since last promotion
- Example Values: 0, 1, 4
- Business Meaning: Long time without promotion can be a retention risk for career-oriented employees.

YearsWithCurrManager
- Data Type: Integer
- Description: Years working with current manager
- Example Values: 0, 5, 8
- Business Meaning: Manager relationship matters for retention; short manager-tenure may signal instability.

---

Engineered / Notebook-derived Columns

Salary Band
- Data Type: Categorical
- Description: Salary bucket derived from MonthlyIncome (labels such as Low, Mid, High used in the notebook)
- Example Values: Low, Mid, High
- Business Meaning: Simplifies pay analysis for stakeholders and highlights pay-group differences in attrition.

Experience Level
- Data Type: Categorical
- Description: Bucketed TotalWorkingYears into experience bands (e.g., Junior, Mid, Senior) using a simple mapping function in the notebook
- Example Values: Junior, Mid, Senior
- Business Meaning: Useful to compare early-career vs experienced-worker attrition patterns and prioritize retention programs.

Age Group
- Data Type: Categorical
- Description: Age bucket derived from Age (e.g., Young, Mid - Career, Experienced)
- Example Values: Young, Mid - Career, Experienced
- Business Meaning: Readily communicates which age cohorts are leaving and helps design targeted retention measures.

Risk Flag
- Data Type: Categorical
- Description: Simple risk segmentation flag created in the notebook to label employees as High Risk or Low Risk for attrition. The notebook implements this using a rule combining overtime status and low satisfaction signals.
- Example Values: High Risk, Low Risk
- Business Meaning: Shortlist of employees requiring fast interventions (stay interviews, manager outreach, workload review).

---

How HR managers can use these variables

- Prioritization: Use Department, JobRole, and Risk Flag to prioritize interventions where attrition counts or rates are highest.
- Targeting: Combine Salary Band, Experience Level, and Age Group to design tailored retention offers (compensation review, mentoring programs, role redesign).
- Early warning: Use OverTime, JobSatisfaction, EnvironmentSatisfaction, and WorkLifeBalance as leading indicators to perform proactive stay interviews.
- Measurement: Track Attrition_Flag over time by department and cohorts to measure impact of retention pilots and adjust investments.

For implementation: the cleaned dataset (outputs/cleaned_hr_data.csv) contains these engineered columns and can be loaded directly into dashboards or modeling pipelines.
