# Loan Default Risk Prediction Using Optimized Logistic Regression

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python&logoColor=white)
![Colab](https://img.shields.io/badge/Google_Colab-Run_in_Colab-orange?logo=googlecolab&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

A complete **end-to-end machine learning project** to predict high-risk borrowers using Python, Logistic Regression, and advanced feature engineering techniques. Balances **predictive performance** with **interpretability**, ideal for financial institutions.

---

## Project Overview
This project builds a **statistically grounded, machine-learning-driven system** to predict loan defaults. Using **Logistic Regression**, **Recursive Feature Elimination (RFE)**, and **SMOTE** for class balancing, the model identifies high-risk borrowers while remaining **interpretable for audits and compliance**.  

This mirrors **real-world workflows** used by banks and fintech companies.

---

## Business Problem
Loan defaults can lead to:  
- Revenue loss  
- Increased financial risk  
- Poor loan portfolio performance  
- Regulatory scrutiny  

**Challenges:**  
- Defaults are rare → dataset is highly imbalanced  
- Misclassifying risky borrowers (False Negatives) is extremely costly  
- Models must be interpretable for regulatory compliance  

**Goal:** Build a transparent, predictive model for risk assessment.

---

## Objectives
- Predict probability of default using **Logistic Regression** (interpretable)  
- Handle severe class imbalance with **SMOTE**  
- Optimize features via **RFE** for predictive power and stability  
- Validate statistical significance using **p-values** and coefficient analysis  
- Evaluate using metrics that prioritize **Recall** (catching defaults)

---

## Dataset

**Name:** L & T Vehicle Loan Default Prediction  
**Source:** [Kaggle Dataset](https://www.kaggle.com/datasets/mamtadhaker/lt-vehicle-loan-default-prediction)  
**Size:** 41 columns, 233,000+ rows  

**Description:** Loan applicant information, demographics, financial attributes, and loan characteristics, useful for predictive modeling.  

**Key Fields:**  
- `Loan_default`: Response variable (1 = default, 0 = no default)  
- `Unique_id`: Unique identifier for each loan application  
- `Asset_cost`: Cost of the asset  
- `Disbursed_amount`: Loan amount disbursed  
- `Date_of_Birth`: Customer’s date of birth  
- `PERFORM_CNS_SCORE_DESCRIPTION`: Bureau score description  

---

## Project Pipeline

### Data Preprocessing
- **Steps:**
  - Handled missing values
  - Encoded categorical variables
  - Split into train/test sets
  - Normalized numerical features
- **Code Example:**
```python
from sklearn.preprocessing import StandardScaler
from sklearn.model_selection import train_test_split

# Split dataset
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Normalize features
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```
Output: Cleaned dataset ready for modeling.

### Handling Class Imbalance — SMOTE

- **Steps:**
  - Applied SMOTE to oversample minority default cases

- **Impact:** 
  - Model learned patterns from defaults → higher recall

- **Code Example:**
```python
from imblearn.over_sampling import SMOTE

smote = SMOTE(random_state=42)
X_res, y_res = smote.fit_resample(X_train_scaled, y_train)
```

### Feature Selection — RFE

- **Steps:**
  - Used Recursive Feature Elimination (RFE) to select the most predictive features
  - Reduced noise and improved model stability and interpretability

- **Impact:** 
  - Selected top predictive features → improved interpretability & stability

- **Code Example:**
```python
from sklearn.feature_selection import RFE
from sklearn.linear_model import LogisticRegression

lr = LogisticRegression()
selector = RFE(lr, n_features_to_select=10)
X_selected = selector.fit_transform(X_res, y_res)
```

### Model Building & Validation

- **Steps:**
  - Built Logistic Regression on the balanced dataset
  - Added constant term for intercept using `statsmodels`
  - Extracted coefficients and p-values for statistical validation

- **Impact:** 
  - Logistic Regression on balanced dataset
  - Provides interpretable coefficients for auditing and compliance

- **Code Example:**
```python
import statsmodels.api as sm

# Add constant term
model = sm.Logit(y_res, sm.add_constant(X_selected))

# Fit the model
result = model.fit()

# Display summary
print(result.summary())
```

## Results & Visuals

### Baseline Model (Before SMOTE)
- **Accuracy:** High but misleading
- **Recall (Default):** < 10%
- **Precision:** Moderate
- **ROC-AUC:** Poor

> Biased toward non-default → not usable in lending.

**Confusion Matrix:** 

<img width="940" height="627" alt="image" src="https://github.com/user-attachments/assets/8e25578d-2c6f-4830-92eb-2f555beb52cc" />

**ROC Curve:** 

<img width="879" height="709" alt="image" src="https://github.com/user-attachments/assets/2ea2d4c7-cd8f-42e6-a56f-9d1c7bda6009" />

### Optimized Logistic Regression (After SMOTE + RFE)
- **Recall (Default):** ~62% 
- **Accuracy:** ~56% (expected trade-off for optimizing Recall)
- **F1-Score:** ~58.9%
- **ROC-AUC:** ~0.65

> Optimized model effectively detects high-risk borrowers.

**Model Comparison Visualization:**  

<img width="940" height="563" alt="image" src="https://github.com/user-attachments/assets/ce09a2dd-2248-41a6-8e5e-78e7ffcc7d20" />

**Key predictors:**  
- Credit History Length  
- Overdue Accounts  
- Disbursed Amount  

> Features have clear positive/negative relationships → informs underwriting policies

### Comparative Analysis: Interpretability vs Predictive Power
| Model                  | Recall (Default) | Advantage                | Policy Context                   |
|------------------------|----------------|-------------------------|----------------------------------|
| Optimized LR           | 62%            | High interpretability    | Suitable for regulated environments |
| Ensemble (Random Forest/GBM) | 75%    | Higher predictive power | Internal risk monitoring          |

> Ensemble models detect more defaults but lack coefficient transparency for audits.

## Challenges
- Severe class imbalance → initial model ignored defaults  
- Risk of overfitting → solved via RFE  
- Misleading accuracy metrics → required focus on Recall  
- Need for interpretability → Logistic Regression limited choice  
- Statistical validation → additional modeling with statsmodels  

## Recommendations
- Strengthen Borrower Screening using high-risk attributes  
- Implement Pre-Loan Risk Flags for manual review  
- Integrate Cost-Sensitive Learning to reduce financial loss  
- Use as Ensemble Baseline for Random Forest/XGBoost  

## Organizational Impact
- Reduce loan default losses  
- Improve underwriting decisions  
- Support regulatory compliance  
- Build scalable ML risk frameworks  


## Run the Project on Google Colab

- **Description:**  
  You can view and run the notebook directly in Google Colab without installing anything locally.

- **Steps:**  
  - Click the link below to open the notebook.  
  - Run each cell in order to see the data preprocessing, modeling, and results.

- **Colab Link:**  
https://colab.research.google.com/drive/1rfP2pTl-andn6AT385VK4cbGUTRfo77w?authuser=0#scrollTo=fcX-LrTm0qG6

## Outputs
- Model evaluation metrics
- Confusion matrix & ROC curves
- Feature importance & coefficients

## Conclusion
This project demonstrates:
- End-to-end ML engineering
- Statistical analysis & feature optimization
- Handling class imbalance
- Real-world business impact & interpretability


## Project Structure

``` text
├── data/
│   ├── raw/
│   │   └── train.csv
│   └── processed/  # optional cleaned/processed datasets

├── notebooks/
│   └── loan_default_prediction_code.ipynb

├── visuals/
│   ├── model_comparison.png
│   └── roc_curve.png

├── reports/
│   └── assignment_2_report.pdf

├── src/
│   └── data_preprocessing.py

├── README.md
├── .gitignore
├── requirements.txt
```
