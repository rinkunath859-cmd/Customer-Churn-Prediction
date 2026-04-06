 ⚙️ Customer Churn Prediction – Feature Engineering Documentation

1. Introduction

Feature engineering is a crucial step in the machine learning pipeline that involves creating new features from existing data to improve model performance. In this project, several meaningful features were derived from the original dataset to better capture customer behavior and enhance churn prediction.

---

 2. Objectives of Feature Engineering

The main goals of feature engineering in this project were:

* To extract deeper insights from existing variables
* To improve model predictive power
* To capture customer value and behavior patterns
* To reduce reliance on raw features

---

 3. Engineered Features

### 3.1 Customer Lifetime Value (CLV)

**Formula:**
CLV = MonthlyCharges × Tenure

**Description:**
Represents the total revenue generated from a customer over their lifetime.

**Reason for Creation:**
Customers with higher lifetime value are often less likely to churn.

---

### 3.2 Average Monthly Spend (AvgSpend)

**Formula:**
AvgSpend = TotalCharges ÷ (Tenure + 1)

**Description:**
Indicates the average amount spent by a customer per month.

**Reason for Creation:**
Helps identify spending patterns and detect irregular payment behavior.

---

### 3.3 Payment Efficiency

**Formula:**
PaymentEfficiency = TotalCharges ÷ MonthlyCharges

**Description:**
Measures consistency between expected and actual payments.

**Reason for Creation:**
Lower efficiency may indicate missed payments or churn risk.

---

### 3.4 Tenure Group

**Definition:**
Customers were grouped into categories based on tenure:

* New (0–12 months)
* Mid (12–24 months)
* Loyal (24–48 months)
* Long-term (48+ months)

**Description:**
Categorical representation of customer duration.

**Reason for Creation:**
Customer loyalty often correlates strongly with churn behavior.

---

### 3.5 High Value Customer Indicator

**Definition:**
Binary feature:

* 1 → MonthlyCharges above median
* 0 → Otherwise

**Description:**
Identifies high-paying customers.

**Reason for Creation:**
High-value customers may behave differently in terms of churn.

---

4. Encoding of Engineered Features

* The **Tenure Group** feature was converted into numerical form using One-Hot Encoding.
* Binary features such as High Value were already in numeric format.

---

 5. Impact on Model Performance

The engineered features contributed to:

* Improved model accuracy and recall
* Better identification of high-risk customers
* Enhanced interpretability of model predictions

Key influential features (based on model importance):

* CLV
* MonthlyCharges
* Tenure
* Contract type

---
6. Assumptions and Considerations

* A small constant (+1) was added to Tenure in division to avoid division-by-zero errors.
* Feature scaling was applied after feature creation to maintain consistency.
* No domain-specific financial adjustments were made to CLV.

---

 7. Conclusion

Feature engineering significantly enhanced the dataset by introducing meaningful derived variables that better represent customer behavior. These features played a vital role in improving the predictive capability of the churn model.

---
