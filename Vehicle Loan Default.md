# 📊 Loan Application Risk & Performance Analysis (Power BI)

![Project](https://img.shields.io/badge/Project-Business_Analytics-blue)
![Power BI](https://img.shields.io/badge/Power_BI-Dashboarding-orange?logo=power-bi&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-Data_Processing-green?logo=microsoft-excel&logoColor=white)
![Analytics](https://img.shields.io/badge/Analytics-Risk_Insights-red)
![License](https://img.shields.io/badge/License-MIT-green)

**Author:** Chirayu Dudhade  
**Course:** Data Science for Innovation
**Project Type:** Business Intelligence & Risk Analytics  
**Date:** December 2025

---

## Project Summary

This project develops a comprehensive, four-page interactive dashboard in **Power BI** to analyze the factors influencing loan approval and denial within a lending portfolio. It moves beyond standard reporting to quantify credit risk, assess operational efficiency, and identify potential biases in the lending process.

**Business Value:** Provides loan officers, risk managers, and executive stakeholders with actionable intelligence to refine lending criteria, target optimal market segments, and minimize loan default exposure.

---

## Key Objectives

- **Develop a Single Source of Truth:** Create four linked dashboards covering Executive Summary, Credit Risk, Borrower Segmentation, and Advanced Analytics.  
- **Quantify Risk Drivers:** Analyze interactions between key eligibility metrics such as **LTV, DTI**, and **Credit Score** to identify high-risk applicant profiles.  
- **Implement Advanced DAX:** Utilize DAX for complex calculations, including **Year-over-Year (YoY) Growth**, **Weighted Average Interest Rate**, and **Time Intelligence**.  
- **Assess Fair Lending:** Examine approval rates across demographic groups (`Age` and `Gender`) to identify potential patterns.  
- **Establish Data Foundation:** Perform rigorous **Data Cleaning and Feature Engineering** (creating LTV ranges, risk buckets) using Power Query (M-Language).

---

## Dataset

- **Source:** Sanitized Loan Application Data (Conceptual: US Mortgage / Consumer Loans)  
- **Scope:** Application details, loan terms, borrower demographics, and final approval status (`Status`)  
- **Size:** 233,000+ rows, 41 columns  
- **Key Fields of Analysis:**
  - `Status` (Response Variable: Approved / Denied)  
  - `loan_amount`, `property_value`, `income`  
  - `LTV`, `dtir1` (DTI Ratio)  
  - `Credit_Score`, `Region`, `Gender`, `age`

---

## Methodology

### 1. Data Preparation & Transformation (Power Query/M)

- **Standardization:** Cleaned categorical text fields (e.g., handling "Sex Not Available").  
- **Missing Value Strategy:** Replaced nulls in financial columns (`rate_of_interest`, `Upfront_charges`) with **0** and simultaneously created **Boolean Flag Columns** to track data quality issues.  
- **Data Modeling Prerequisite:** Created a dedicated **Calendar Table** and established relationships for Time Intelligence calculations.

### 2. Feature Engineering & Modeling

- **Risk Bins:** Created analytical groupings for visualization and risk scoring:
  - `LTV_Range` (e.g., 'Below 60%', 'Over 90%')  
  - `Credit_Score_Group` (e.g., 'Poor', 'Fair', 'Good', 'Excellent')  
- **Calculated Ratios:** Engineered **`Loan_to_Income_Ratio` (LTI)** as a key risk metric.

### 3. DAX Measures & Advanced Analytics

- **Core KPIs:** Built foundational metrics like **`Approval Rate %`**, **`Avg. DTI`**, and **`Total Loans`**  
- **Time Intelligence:** Developed measures for **`YoY Approval Rate Growth`** and **`Cumulative Loan Amounts`**  
- **Financial Modeling:** Calculated **`Weighted Average Interest Rate`** to accurately reflect the portfolio's true cost of lending.

### 4. Visualization & Dashboard Structure (Planned)

| Page | Focus Area | Key Visualizations |
| :--- | :--- | :--- |
| **1: Executive Summary** | Portfolio Performance & Trends | KPI Cards, Approval Trend (Line Chart), Approval Rate by Region (Map) |
| **2: Risk & Eligibility** | Why loans are denied | Heatmap (LTV vs. DTI), Clustered Column (Approval by Credit Score Band), Scatter Plot (Loan Amount vs. Interest Rate) |
| **3: Borrower Segmentation** | Who is getting approved | Grouped Column (Approval Rate by Age & Gender), Histogram (Income Distribution), Approval by Loan Purpose |
| **4: Advanced Analytics** | Technical Depth & Forecasting | Time Series (YoY Growth, Cumulative Growth), Risk Persona Cards, Predictive Probability Visuals |

---

## Current Status

**Data Preparation, Feature Engineering, and Data Modeling (including Calendar Table) are conceptually complete.**  

**Next Steps:**

1. Finalize **DAX Measures** for all four dashboards  
2. Develop the four interactive **Power BI Dashboard** pages  
3. Extract **Key Insights** and **Recommendations** based on visualization results

---

## Tools & Technologies

- **Data Processing:** Power Query (M-Language)  
- **Data Modeling & Calculations:** DAX  
- **Visualization:** Power BI Desktop  
- **Skills Demonstrated:** Data Modeling, Advanced DAX, Risk Analysis, Data Storytelling, Business Intelligence Development

## Data Preparation & Feature Engineering

To ensure accurate, consistent, and analysis-ready data for the Loan Analysis project, I performed extensive **data cleaning, transformation, and feature engineering**. These steps were critical in creating a solid foundation for all **DAX calculations** and **interactive dashboard visuals**.

---

## Data Cleaning & Preparation

**Standardization of categorical fields:**

- **Gender** → Replaced `"Sex Not Available"` with `"Unknown"`
- **Status** → Mapped to `Approved = 1`, `Denied = 0`

**Handling missing and null values:**

- Replaced nulls in numeric columns (`rate_of_interest`, `Upfront_charges`) with `0`
- Created **Boolean flag columns** to track missing values for data quality assessment

**Data type conversion:**

- Converted `loan_amount`, `property_value`, `income`, `LTV`, `dtir1` to **Decimal Number**
- Converted `term` to **Whole Number**

**Duplicate removal and irrelevant ID cleanup** to ensure a clean dataset

**Outcome:**  
A standardized and validated dataset ready for feature engineering and advanced analytics.

---

## Feature Engineering

To enhance insights and support risk analysis, I created new **analytical columns and risk indicators**:

- **Credit Score Band:** Categorized into `Poor`, `Fair`, `Good`, `Excellent`
- **LTV Range:** Categorized into `Below 60%`, `60–80%`, `80–90%`, `Over 90%`
- **Loan-to-Income Ratio (LTI):** `[loan_amount] / [income]` to measure financial risk relative to borrower income
- **Term Groups:** Standardized loan durations for segmentation (`180 months → 15 Year`, `360 months → 30 Year`, etc.)
- **Risk Buckets:** Combined LTV and DTI to identify high/medium/low-risk loans

---

## Challenges & Learnings

**Credit Score Band:**

- Initially tried using **parameters and conditional formatting**, but only `"Poor"` and `"Fair"` appeared despite higher scores.
- Resolved by creating a **custom column** with explicit conditions in M code, which correctly categorized all credit scores.

**Term Groups:**

- Initially filtered loans into `5, 10, 15, 20, 25, 30-year` groups, setting others as `"Custom"`.
- Many loans fell between these ranges, so I corrected it using **conditional columns** to ensure accurate grouping.

**Loan-to-Income Ratio (LTI):**

- Some rows had income as `0` or `null`, producing `Infinity` values.
- Replaced these with `0` to maintain data integrity and ensure valid calculations.

---

**Outcome:**  
The dataset is now **feature-rich, clean, and structured**, serving as a strong foundation for creating **advanced DAX measures** and **interactive dashboards**. This process emphasized the importance of **data validation, feature engineering, and troubleshooting real-world dataset challenges**, key skills for effective business intelligence analysis.

# Loan Portfolio Analysis — DAX Measures

This phase involved creating key DAX measures in Power BI to quantify loan portfolio performance, evaluate borrower risk, and calculate financial exposure. These measures form the core analytical foundation for all dashboard visualizations and risk assessment.

## Objective

- Quantify overall loan activity (volume, approvals/denials).  
- Measure portfolio health using averages of credit score, LTV, and DTI.  
- Estimate financial exposure through total loan amounts and interest.  
- Enable risk segmentation and data-driven insights.  

## Key Metrics and Formulas

| Metric | DAX Formula | Interpretation & Insight |
|--------|------------|-------------------------|
| **Total Loans** | `COUNTROWS('Loan_Default')` | Counts all applications; base for all further calculations. |
| **Approval Rate %** | `DIVIDE(CALCULATE(COUNTROWS('Loan_Default'), 'Loan_Default'[Status] = "Approved"), [Total Loans], 0)` | Proportion of approved applications; indicates strictness of lending criteria. |
| **Denial Rate %** | `DIVIDE(CALCULATE(COUNTROWS('Loan_Default'), 'Loan_Default'[Status] = "Denied"), [Total Loans], 0)` | Proportion of denied applications; complements approval rate. |
| **Average Loan Amount** | `AVERAGE('Loan_Default'[loan_amount])` | Shows typical loan size requested. |
| **Average Credit Score** | `AVERAGE('Loan_Default'[Credit_Score])` | Measures overall applicant creditworthiness. |
| **Average LTV** | `AVERAGE('Loan_Default'[LTV])` | Reflects collateral exposure risk. |
| **Average DTI** | `AVERAGE('Loan_Default'[dtir1])` | Indicates borrower leverage and repayment capacity. |
| **Total Loan Amount** | `SUM('Loan_Default'[loan_amount])` | Total portfolio exposure in monetary terms. |
| **Total Interest** | `SUMX('Loan_Default', 'Loan_Default'[loan_amount] * 'Loan_Default'[rate_of_interest] / 100)` | Estimated total interest revenue; critical for profitability analysis. |

## Why These Metrics Were Created

- **Portfolio Scale & Performance:** Total loans, approvals, and denials provide insight into operational efficiency and selection criteria.  
- **Risk Assessment:** Credit Score, LTV, DTI, and loan amount highlight financial risk and borrower quality.  
- **Revenue Estimation:** Total interest quantifies potential income from the portfolio.  
- **Dashboard Foundation:** Enables interactive and insightful Power BI dashboards for executives and analysts.  

## Output & Insights (Executive Summary)

The initial calculation of Core KPIs immediately highlights the lending strategy's profile:

- **Total Loans:** 149K applications  
- **Total Loan Amount:** 49.23 billion AUD  
- **Approved Loans:** 37K (25% approval rate)  
- **Denied Loans:** 112K (75% denial rate)  
- **Avg Credit Score:** 699.79 (Good)  
- **Avg LTV:** 65.36% (low risk)  
- **Avg DTI:** 31.61% (healthy leverage)  
- **Avg Loan Amount:** 331.12K AUD  
- **Total Interest:** 1.50 billion AUD  

### Key Insight: The Low Approval Rate Disconnect

Only 1 out of 4 applications are approved, despite the average applicant showing a **"Good" credit score (~700)**, **low LTV (65%)**, and **healthy DTI (31%)**. This suggests:

- **Policy Tightness:** The current lending criteria is highly restrictive, potentially rejecting profitable, low-risk applicants.  
- **Hidden Risk:** The high volume of denials is likely driven by extreme values in the unapproved segment (e.g., LTV > 90% or DTI > 50%) which are offset by the healthy approved loans, leading to misleading aggregate averages.  

**Outcome:** The dataset is now feature-rich, clean, and structured, serving as a strong foundation for creating advanced DAX measures and interactive dashboards. This process emphasized the importance of **data validation, feature engineering, and troubleshooting real-world dataset challenges**, key skills for effective business intelligence analysis.

# Executive Summary — Portfolio Performance & Trends

This page provides a high-level view of the loan portfolio, focusing on performance, trends, and regional variations. Each visual delivers specific insights to support strategic decision-making.

<img width="1311" height="731" alt="image" src="https://github.com/user-attachments/assets/0029aaa9-2904-43d0-9ad4-eb862bf8bd11" />

## Core Portfolio Metrics

**Data Shown:**

- **Total Loans:** 148,670  
- **Approval Rate:** 24.64%  
- **Average Loan Amount:** 331,117.74 AUD  
- **Average Credit Score:** 699.79  
- **Average LTV:** 65.36%  

**Outcome & Insights:**  
The KPI cards summarize the most critical metrics for the portfolio. The total loans show the scale of operations, while the approval rate highlights that only about 1 in 4 applications is approved, indicating strict lending criteria. The average loan amount shows the typical financial exposure per borrower, and the credit score and LTV indicate generally low- to moderate-risk applicants. These KPIs provide an at-a-glance overview for executives to quickly assess portfolio health.

---

## Approval Rate by Region

**Data Shown:**

- North-East: 30.45%  
- Central: 27.54%  
- South: 26.63%  
- North: 22.51%  

**Outcome & Insights:**  
The line chart reveals regional differences in approval rates. North-East has the highest approval rate, whereas the North has the lowest. This helps identify regions where lending policies or applicant quality differ, enabling targeted risk management and marketing strategies. For example, stricter pre-screening or more selective lending in the North may explain the lower approval rate.

---

## Average Loan Amount by Region

**Data Shown:**

- South: 333,321 AUD  
- North: 330,528 AUD  
- Central: 323,097 AUD  
- North-East: 309,059 AUD  

**Outcome & Insights:**  
This chart highlights regional variations in the average loan amount. The South and North regions have higher average loan sizes, suggesting higher borrower financial capacity or demand for larger loans. This insight can guide regional lending strategies, risk assessment, and product offerings.

---

## Loan Type by Purpose

**Data Shown:**

- **Standard Purchase Loan (Type 1):**  
  - New Vehicle: 26,398  
  - Used Vehicle (Up to 5 yrs): 2,827  
  - Used Vehicle (Older/High Mileage): 41,304  
  - Recreational/Specialty: 42,644  

- **Refinance Loan (Type 2):**  
  - New Vehicle: 5,707  
  - Used Vehicle (Up to 5 yrs): 438  
  - Used Vehicle (Older/High Mileage): 8,549  
  - Recreational/Specialty: 6,068  

- **Lease Buyout / Balloon (Type 3):**  
  - New Vehicle: 2,558  
  - Used Vehicle (Up to 5 yrs): 9  
  - Used Vehicle (Older/High Mileage): 6,081  
  - Recreational/Specialty: 6,087  

**Outcome & Insights:**  
The matrix shows loan demand by type and purpose. Standard purchase loans dominate the portfolio, with significant activity in new and older used vehicles. Refinance and lease buyout loans contribute smaller but relevant portions. This distribution provides insight into product popularity, helps identify high-demand areas, and supports decision-making for marketing, risk evaluation, and product development.


## Overall Outcome

The combination of KPI cards, line and column charts, and the loan type matrix provides a clear snapshot of the portfolio’s scale, performance, regional patterns, and product mix. This foundational view guides deeper analysis in subsequent pages, such as risk assessment and borrower segmentation.

---

# Risk & Eligibility Analysis

This page examines the key risk factors that influence loan approval decisions. By analyzing credit score bands, LTV and DTI ranges, and the relationships between loan amount, interest rate, and approval status, we identify the underlying patterns that shape the bank’s lending decisions.

<img width="1106" height="620" alt="image" src="https://github.com/user-attachments/assets/745dd707-11c1-4703-8c86-fb56e493667d" />

## Approval Rate by Credit Score Band

### **Data Shown**
- **Excellent:** 24.93%  
- **Poor:** 24.66%  
- **Fair:** 24.48%  
- **Good:** 24.16%  
- **Overall Average:** ~25%

### **Outcome & Insights**
- Approval rate remains nearly identical across all credit score bands—including **Excellent** and **Poor**.  
- This indicates **credit score is not a major determining factor** in loan approvals.  
- Other variables such as **LTV, DTI, collateral risk**, and internal scoring models are driving the majority of decisions.  
- This challenges traditional assumptions and shifts focus toward the **actual drivers of approval**.

---

## Total Denied Loans by LTV and DTI Range

### **Data Shown**
Denials across LTV ranges:
- **LTV 60–80%:** 17,193 (High Risk)  
- **LTV Below 60%:** 10,566 (High Risk)  
- **LTV 80–90%:** 8,058 (High Risk)  
- **LTV Over 90%:** 7,167 (High Risk)

### **Outcome & Insights**
- Denials increase significantly in **higher LTV** and **moderate-to-high DTI** combinations.  
- Confirms that **collateral risk (LTV)** and **repayment risk (DTI)** are central to the bank’s underwriting model.  
- Highlights high-risk segments where most denials occur.  
- Supports better **risk segmentation** and potential adjustments to lending rules.

---

## Loan Amount vs Interest Rate (Colored by Status)

### **Data Shown**
- **X-axis:** Loan Amount  
- **Y-axis:** Interest Rate  
- **Color:** Approval Status 1 (Approved) and 0 (Denied)

### **Outcome & Insights**
- Approvals cluster around **moderate loan amounts (under $1M)** and **interest rates between 4%–5%**.  
- Higher loan amounts show fewer approvals.  
- Very low interest rates contain many denials → suggests **data quality issues or strict filtering**.  
- Reveals the bank’s **risk appetite** and the “**sweet spot**” where approvals are most common.  
- Helps identify **profitable and lower-risk product ranges**.

---

## LTV vs DTI (Colored by Status)

### **Data Shown**
- **X-axis:** LTV  
- **Y-axis:** DTI  
- **Color:** Approval Status  
- **Approved Cluster:** Low LTV, Low DTI  
- **Denials Dominate:** High LTV + High DTI and mid-risk zones

### **Outcome & Insights**
- Clearly visualizes the bank’s lending logic.  
- Approved loans cluster in **low-risk zones**: low LTV + low DTI.  
- Denials dominate high-risk regions: **LTV > 120** and **DTI > 50–60** → indicates **hard underwriting limits**.  
- Medium-risk zones showing mixed results suggest influence from **additional risk variables** (e.g., collateral type).  
- Confirms that **LTV and DTI are the strongest predictors of approval**.

---

## **Overall Outcome**

This page provides essential insights into the drivers behind loan approvals and denials:

- **Credit score has minimal influence** on approval outcomes.  
- **LTV and DTI are the primary determinants of eligibility**.  
- Findings reveal clear **risk boundaries**, highlight **profitable borrower segments**, and explain where the bank exercises caution.  
- This analysis forms the foundation for refining risk strategies and optimizing the underwriting process.

---

