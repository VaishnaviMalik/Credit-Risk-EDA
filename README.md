# Credit-Risk-EDA
#### Description:
It is a project built in Python and documented as a Jupyter notebook, an exploratory analysis of credit loan applications focused on cleaning and understanding borrower characteristics and their relationship to loan repayment outcomes. The goal is to understand patterns in borrower data and identify features linked to loan repayment behavior, especially how categorical factors like gender, family status, income type, housing type, and occupation relate to defaulters vs non-defaulters.

This project was developed to demonstrate practical understanding of credit risk exploratory data analysis, data cleaning, feature selection, and target-driven EDA workflows in Python.

---

## Project Goals
- Clean and prepare the loan application dataset for analysis by handling missing values and fixing data types.
- Identify and treat outliers in key financial features like AMT_CREDIT, AMT_ANNUITY, and AMT_GOODS_PRICE.
- Explore how borrower characteristics link to loan repayment outcomes using target-based segmentation (TARGET = 0 vs 1).
- Discover patterns in demographic and credit behavior that help explain default risk.

---

## Notebook Workflow
1. Import and inspect the loan dataset
2. Clean data by dropping columns with too many missing values
3. Analyze selected columns with nulls and outliers
4. Impute missing values using median for skewed numeric features
5. Fix incorrect data types
6. Detect and treat outliers using IQR
7. Bin a numeric feature 'AMT_ANNUITY'
8. Perform target-based analysis by splitting on 'TARGET'
9. Build univariate and bivariate visual analysis for loan repayment vs default
    
---

## Files and Notebooks
- `CreditEda.ipynb` — The main implementation notebook. It contains the full exploratory data analysis pipeline for credit loan data:
  - Data import and basic inspection using `pd.read_csv('application_data.csv')`, `loan.info()`, `loan.describe()`, and `loan.shape`.
  - Data cleaning:
    - Drop columns with more than 50% missing values
    - Compute missing-value percentages
    - Inspect and choose median imputation for skewed numeric columns such as `AMT_REQ_CREDIT_BUREAU_QRT`, `AMT_REQ_CREDIT_BUREAU_YEAR`, `AMT_REQ_CREDIT_BUREAU_MON`, `AMT_REQ_CREDIT_BUREAU_WEEK`, and `AMT_REQ_CREDIT_BUREAU_DAY`.
  - Data type correction for columns like `DAYS_BIRTH`, `REGION_RATING_CLIENT`, and `REGION_RATING_CLIENT_W_CITY`.
  - Outlier detection and treatment using the IQR method for financial columns such as `AMT_ANNUITY`, `AMT_CREDIT`, and `AMT_GOODS_PRICE`.
  - Feature binning for `AMT_ANNUITY` into ranges.
  - Target-based analysis:
    - Create `loan1` with selected borrower and loan features
    - Split into `T0` and `T1` by `TARGET`
    - Univariate category plots for gender, family status, income type, housing type, and occupation
    - Bivariate stacked-bar comparisons for categorical variables
  - Extended analysis:
    - Load `previous_application.csv`
    - Merge previous application records with the main loan dataset on `SK_ID_CURR` for deeper analysis
- `application_data.csv` — The primary loan application dataset used in the notebook.
- `previous_application.csv` — Secondary dataset containing past application history, merged into the main analysis later in the notebook.

---

## How to run
1. Install basic dependencies (Python 3.8+ recommended):
  ```bash
  pip install pandas numpy matplotlib seaborn jupyter
  ```

2. Make sure the dataset files are in the same folder as the notebook:
    - `application_data.csv`
    - `previous_application.csv`
    
3. Launch Jupyter Notebook or open the notebook in VS Code:
    - 'jupyter notebook'
    - Open 'CreditEda.ipynb'
      
4. Run the notebook cells in order:
    - data import and inspection
    - cleaning and missing-value handling
    - outlier analysis and binning
    - target-based EDA
    - merge with `previous_application.csv`
      
5. Review the output tables and plots to understand the credit risk analysis.

Example usage is simply executing the notebook from top to bottom and inspecting the visualizations and merged dataset output.

--- 

## Results
- The cleaned dataset removed high-missing columns and imputed key numeric fields using median values.
- Outlier analysis showed extreme values in `AMT_ANNUITY`, `AMT_CREDIT`, and `AMT_GOODS_PRICE`, which were examined with IQR-based filtering.
- Target-based EDA revealed borrower patterns: gender, family status, income type, housing type, and occupation have different distributions for repaid vs defaulted loans.
- Merging `application_data.csv` with `previous_application.csv` added historical loan behavior and enriched the analysis of credit risk factors.

---

## Business Impact
- Helps banks reduce NPAs (Non-Performing Assets)
- Supports better loan approval decisions
- Identifies risky borrower segments early

---

## Future Work and Extensions
- Add more advanced missing-data handling and outlier treatment, including imputation strategies by segment and robust scaling.
- Develop a dashboard or report with interactive visuals so stakeholders can explore risk factors by gender, income, housing, and occupation.
- Validate findings with cross-validation or a holdout set, and measure performance with precision, recall, and ROC/AUC.

---

## License
This project is intended for educational purposes only.

---
