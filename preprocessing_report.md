📊 Customer Churn Prediction – Preprocessing Report

 1. Introduction

This report outlines the data preprocessing steps performed on the customer churn dataset. The goal of preprocessing was to clean, transform, and prepare the data for machine learning modeling to predict customer churn.

---

 2. Dataset Overview

The dataset contains customer-related information including tenure, billing details, contract type, and churn status.

**Columns in dataset:**

* CustomerID
* Tenure
* MonthlyCharges
* TotalCharges
* Contract
* PaymentMethod
* PaperlessBilling
* SeniorCitizen
* Churn (Target Variable)

---

 3. Data Cleaning

### 3.1 Column Name Standardization

* All column names were converted to lowercase.
* Leading and trailing whitespaces were removed.

**Reason:**
To ensure consistency and avoid errors such as KeyError during analysis.

---

### 3.2 Data Type Conversion

* The `TotalCharges` column was converted from object (string) to numeric.
* Invalid values were handled using coercion, converting them to NaN.

---

### 3.3 Handling Missing Values

* Rows with missing values were removed using `dropna()`.

**Reason:**
The dataset had minimal missing values, and removal did not significantly affect data size.

---

 4. Encoding of Categorical Variables

Different encoding techniques were applied based on the type of categorical variables:

### 4.1 Label Encoding

* Applied to:

  * Churn (target variable)
  * PaperlessBilling

**Reason:**
These are binary categorical variables, making label encoding suitable.

---

### 4.2 One-Hot Encoding

* Applied to:

  * Contract
  * PaymentMethod

**Reason:**
These are nominal categorical variables with no inherent order.

---

### 4.3 Existing Numeric Encoding

* SeniorCitizen was already encoded as 0 and 1, so no transformation was required.

---

 5. Feature Scaling

Two scaling techniques were applied:

### 5.1 Standard Scaling

* Applied to numerical features such as MonthlyCharges.

**Purpose:**
To standardize data with mean = 0 and standard deviation = 1.

---

### 5.2 Min-Max Scaling

* Applied to MonthlyCharges.

**Purpose:**
To normalize values between 0 and 1.

---

 6. Outlier Detection

Two methods were used to detect outliers in MonthlyCharges:

### 6.1 Interquartile Range (IQR)

* Outliers identified using Q1, Q3, and IQR formula.

### 6.2 Z-Score Method

* Observations with Z-score greater than 3 were flagged as outliers.

**Note:**
Outliers were analyzed but not removed to preserve data integrity.

---

 7. Feature Engineering

Several new features were created to improve model performance:

* **Customer Lifetime Value (CLV):**
  MonthlyCharges × Tenure

* **Average Spend:**
  TotalCharges ÷ Tenure

* **Payment Efficiency:**
  TotalCharges ÷ MonthlyCharges

* **Tenure Group:**
  Customers grouped into categories (New, Mid, Loyal, Long-term)

* **High Value Customer:**
  Binary indicator based on median MonthlyCharges

---

 8. Feature Selection

* Correlation analysis was performed using a heatmap.
* Only numerical features were considered for correlation computation.
* Irrelevant columns such as CustomerID were removed.

---

 9. Data Splitting

* Dataset was split into training (80%) and testing (20%) sets.
* Stratified sampling was used to maintain class distribution.

---

 10. Final Preprocessing Pipeline

The final dataset included:

* Cleaned and standardized features
* Encoded categorical variables
* Scaled numerical variables
* Engineered features

This processed dataset was then used for training a machine learning model (Random Forest Classifier).

---

 11. Conclusion

The preprocessing steps ensured:

* Clean and consistent data
* Proper handling of categorical and numerical features
* Improved feature representation through engineering
* Readiness for machine learning modeling

These steps significantly contributed to building a reliable customer churn prediction model.

---
