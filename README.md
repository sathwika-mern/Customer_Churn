# Customer Churn Dataset — Exploratory Data Analysis (EDA)

## Project Overview
This project explores the **Telco Customer Churn** dataset to understand its structure, identify possible data-quality issues, and discover patterns associated with customer churn.

The analysis is performed on the **raw dataset first**, without cleaning or changing the original values. This follows the instruction to observe and document the data before deciding whether cleaning is needed.

## Objectives
- Load and understand the dataset.
- Inspect its rows, columns, data types, and summary statistics.
- Investigate missing values, blank strings, duplicate customer IDs, and unusual category values.
- Visualize customer distributions and relationships with churn.
- Examine numerical distributions and potential outliers.
- Record evidence-based findings and distinguish genuine data-quality issues from normal patterns.
- Plan any cleaning only after the raw-data investigation is complete.

## Dataset
- **Dataset:** Telco Customer Churn
- **Expected size:** 7,043 rows and 21 original columns (verify this against the file used).
- **Target column:** `Churn`
- **Customer identifier:** `customerID`

### Main columns
- **Customer details:** `customerID`, `gender`, `SeniorCitizen`, `Partner`, `Dependents`
- **Account/service details:** `tenure`, `PhoneService`, `MultipleLines`, `InternetService`, `OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`
- **Billing details:** `Contract`, `PaperlessBilling`, `PaymentMethod`, `MonthlyCharges`, `TotalCharges`
- **Outcome:** `Churn`

`tenure` indicates how long the customer has stayed with the company, in months. `MonthlyCharges` is the monthly amount charged. `TotalCharges` is the total amount charged over the customer's time with the company. `Churn` indicates whether the customer left.

## Tools and Libraries
- Python
- Jupyter Notebook
- pandas
- NumPy
- Matplotlib
- Seaborn

## Workflow
1. Load the CSV file.
2. Inspect the first and last rows and the column names.
3. Review data types and summary statistics.
4. Check missing values and blank strings separately.
5. Inspect `TotalCharges`, which may be stored as text and may contain blank entries.
6. Check duplicate rows and duplicate `customerID` values.
7. Inspect categorical values and their frequencies.
8. Visualize distributions of categorical and numerical variables.
9. Compare churn with contract type, tenure, and monthly charges.
10. Inspect correlations among numerical variables.
11. Document findings before applying any cleaning.

## Key EDA Questions
- How many customers churned compared with customers who stayed?
- Does churn differ across contract types?
- How does tenure differ between customers who churned and those who stayed?
- How do monthly charges differ between these groups?
- Are there missing or blank values, especially in `TotalCharges`?
- Are any customer IDs duplicated?
- Are there unexpected values or data types that may affect analysis?
- Are any potential outliers present, and do they represent errors or valid observations?

## Important Interpretation Notes
- **A blank string is not always counted as a missing value by pandas.** Check blank strings separately from `NaN`.
- **An unusual data type is a warning to investigate, not automatic proof of an error.** For example, `TotalCharges` represents a numeric amount but may be read as text when blank entries exist.
- **An outlier is not automatically an error.** Investigate whether the value is impossible or simply uncommon before deciding what to do.
- **Class imbalance is a property of the target distribution, not necessarily a data-quality error.**
- **Correlation does not prove causation.**
- If a derived column such as `TotalCharges_numeric` is created for investigation, document that transformation. Do not treat its correlation of 1.00 with the original numeric values as evidence of a dataset error; the columns may contain the same information.
- Avoid overwriting the original data during the initial investigation. If a later cleaning stage is approved, work on a separate copy and record each change.

## Preliminary Observations
The notebook includes visual analysis such as:
- Internet service distribution
- Churn by contract type
- Tenure by churn status
- Monthly charges by churn status
- Numerical-variable boxplots
- A correlation heatmap

The displayed graphs suggest that month-to-month customers may churn more frequently, customers who churn tend to have shorter tenure, and churned customers may have higher monthly charges. These are preliminary visual observations; calculate group-wise churn percentages and inspect exact values before reporting final conclusions.

## Data-Quality Findings
Complete this section after running the raw-data checks. Do not claim an issue unless the notebook output supports it.

| Check | Result / evidence | Interpretation / next step |
|---|---|---|
| Missing values (`NaN`) | To be recorded | Inspect affected columns and rows |
| Blank strings | To be recorded | Inspect the raw values |
| `TotalCharges` data type | To be recorded | Check whether numeric conversion is needed later |
| Duplicate rows | To be recorded | Investigate before removing |
| Duplicate `customerID` values | To be recorded | Verify whether records are truly duplicated |
| Unexpected categorical values | To be recorded | Compare against expected categories |
| Potential outliers | To be recorded | Investigate; do not remove automatically |

## How to Run
1. Open the notebook in Jupyter Notebook or Google Colab.
2. Place the CSV file in the notebook's working directory, or update the file path in the loading cell.
3. Run the notebook cells in order.
4. During the initial EDA, do not overwrite, delete, or impute raw values.
5. Record the actual output and evidence in the Data-Quality Findings table.

Example loading code:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("WA_Fn-UseC_-Telco-Customer-Churn.csv")

print("Shape:", df.shape)
df.head()
```

## Conclusion
The purpose of this project is to understand the customer churn dataset and investigate whether data-quality issues exist before cleaning. Conclusions about errors must be based on observable evidence. Once the raw-data investigation is documented, a separate cleaning stage can be planned and its effects compared with the original data.

