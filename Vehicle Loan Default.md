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
