# Lending Business

## Project Description
This project analyzes a synthetic dataset representing a short-term consumer lending portfolio. The dataset contains loan application data, borrower financial characteristics, and repayment information. The objective is to explore borrower risk indicators, approval behavior, and portfolio performance in order to better understand how lending decisions relate to financial conditions and repayment outcomes.

## Data inspection
After importing the dataset, I checked the first few rows using `.head()` and summary statistics using `.describe()` to confirm the structure and ranges of the variables. The dataset contains the following columns:

- **loan_id** – unique identifier of the loan application (and loan if approved)  
- **application_date** – date the financing request was submitted  
- **requested_amount** – amount requested by the borrower  
- **term_days** – loan duration in days  
- **total_repayment_expected** – total contractual repayment amount  
- **total_repayment_received** – total amount repaid to date  
- **last_payment_date** – date of most recent repayment  
- **approval_flag** – indicates whether the loan was approved  
- **customer_id** – unique customer identifier  
- **customer_birth_date** – borrower’s date of birth  
- **verified_monthly_income** – verified monthly income at application  
- **verified_monthly_expenses** – verified monthly living expenses  
- **external_credit_commitments** – ongoing obligations to other lenders  
- **overdue_external_balance** – overdue external debt amount  

## Data cleaning and modifying
- Checked for missing values across all variables.
- Missing values appear only in **last_payment_date**. This is expected because a payment date exists only when repayment occurs. Loans without repayment correctly have no payment date.
- Verified numeric columns and data ranges.
- Created a filtered dataset of approved loans for selected analyses.
- No imputation or structural changes were required.

## Exploratory Data Analysis (EDA)

### Portfolio KPIs
Using aggregated portfolio measures:

- Loan terms confirm a short-term lending product.
- Loan amounts fall within the typical range for small consumer loans.
- Outstanding balance reflects unpaid receivables across issued loans.
- Expected income represents contractual repayment above principal.
- Realized income is currently negative because many loans remain unpaid or only partially repaid.

This indicates that the portfolio is still in the repayment phase and full performance cannot yet be observed.

### Client age
To better understand the borrower base, applicants were grouped by age and compared by approval status.

Approval percentages are similar across age groups, indicating that age alone does not appear to be a primary factor in approval decisions. Borrowers are mostly within working-age ranges, which is typical for short-term credit products.

### Debt-to-Income Ratio (DTI)
DTI was calculated as the ratio of overdue external balance to verified monthly income.

Average DTI is higher among rejected applicants than approved applicants, indicating that larger overdue debt relative to income is associated with lower approval likelihood. However, median DTI equals zero for both groups, meaning that more than half of applicants have no overdue external debt.

This difference between mean and median shows that the distribution is highly skewed. Most borrowers have no overdue obligations, while a smaller group carries large overdue balances.

Boxplot analysis shows that rejected applicants generally have broader and higher DTI ranges, indicating that approvals are more common among borrowers with lower overdue debt burden.

### Expense-to-Income Ratio (EIR)
EIR was calculated as verified monthly expenses divided by verified monthly income.

Rejected applicants show slightly higher average and median EIR values than approved applicants, indicating that higher living-expense burden is associated with reduced approval likelihood. However, the distributions overlap substantially, and many approved borrowers still have relatively high expense burdens.

This suggests that affordability plays a role in lending decisions but is not the only determining factor.

### Client Risk Profile: DTI and EIR
To evaluate combined financial burden, DTI and EIR were compared across approval outcomes.

The scatterplot shows substantial overlap between approved and rejected applicants across both ratios. While higher financial burden appears more common among rejected borrowers, approvals occur across a wide range of values.

This indicates that lending decisions likely incorporate additional variables beyond these two ratios.

### Key Findings
- The portfolio consists of short-term consumer loans with relatively small principal amounts.
- Most borrowers do not have overdue external debt, though a smaller high-risk segment exists.
- Living expenses represent a substantial share of income for many applicants.
- Differences between approved and rejected borrowers in terms of DTI, EIR, and age are present but not large.
- Approval decisions are likely based on multiple factors.
- A significant portion of loans remains unpaid, affecting realized profitability.

## Data Limitations
- The dataset is synthetic and does not represent actual lending activity.
- Repayment data reflects a single observation point rather than full loan lifecycle outcomes.
- DTI is based only on overdue external balances, not total external debt.
- Approval decision criteria are not explicitly defined in the dataset.

## Conclusion
The portfolio primarily serves borrowers with moderate to high financial burden who require short-term financing. Most applicants do not have overdue external debt, but many allocate a large share of income to regular expenses. Approval patterns suggest that lending decisions consider multiple risk indicators rather than relying on a single measure.

Because many loans remain in repayment, current portfolio performance reflects incomplete recovery rather than final profitability. Long-term outcomes depend on future repayment realization and management of higher-risk borrower segments.

Data: synthetic lending dataset
