 Customer Churn Prediction Project

---

 📌 1. Project Overview

### 🎯 Objective

The objective of this project is to build a machine learning model that predicts whether a customer is likely to churn based on their demographic and service usage data.

### 💼 Business Context

Customer churn is a major challenge for subscription-based businesses. Retaining existing customers is more cost-effective than acquiring new ones. By identifying high-risk customers in advance, companies can:

* Offer targeted retention strategies
* Improve customer satisfaction
* Increase long-term revenue

---

 📊 2. Dataset Description

The dataset contains customer-level information including service usage, billing, and contract details.

### 🔑 Features:

* **CustomerID** – Unique identifier (removed during modeling)
* **Tenure** – Number of months customer has stayed
* **MonthlyCharges** – Monthly bill amount
* **TotalCharges** – Total bill amount
* **Contract** – Type of contract (Monthly, One year, Two year)
* **PaymentMethod** – Mode of payment
* **PaperlessBilling** – Whether billing is paperless
* **SeniorCitizen** – Whether customer is senior
* **Churn** – Target variable (Yes/No)

---

🧹 3. Data Preprocessing Pipeline (With Rationale)

### 🔹 Column Standardization

* Converted all column names to lowercase and removed spaces

**Why?**
Prevents errors during column access and ensures consistency.

---

### 🔹 Data Type Conversion

* Converted `TotalCharges` to numeric format

**Why?**
It was stored as string, which prevents mathematical operations.

---

### 🔹 Missing Value Handling

* Removed rows with missing values

**Why?**
The number of missing values was minimal, and removing them avoided introducing bias through imputation.

---

 🔤 4. Encoding Strategy

### 🔹 Label Encoding

Applied to:

* Churn
* PaperlessBilling

**Why?**
These are binary variables, making them suitable for direct numeric mapping (0/1).

---

### 🔹 One-Hot Encoding

Applied to:

* Contract
* PaymentMethod

**Why?**
These are categorical variables without order. One-hot encoding prevents incorrect ordinal assumptions.

---

 📏 5. Feature Scaling

Two scaling techniques were explored:

### 🔹 Standard Scaling

* Normalizes data to mean = 0 and standard deviation = 1

### 🔹 Min-Max Scaling

* Scales values between 0 and 1

**Final Choice:**
Standard scaling was used for model training as it performed more consistently.

---

 🚨 6. Outlier Detection

### Methods Used:

* Interquartile Range (IQR)
* Z-score

**Observation:**
Outliers were identified but retained to preserve real-world variability in customer behavior.

---

⚙️ 7. Feature Engineering

The following features were created to enhance predictive performance:

| Feature           | Description                    | Purpose                       |
| ----------------- | ------------------------------ | ----------------------------- |
| CLV               | MonthlyCharges × Tenure        | Measures customer value       |
| AvgSpend          | TotalCharges ÷ Tenure          | Captures spending behavior    |
| PaymentEfficiency | TotalCharges ÷ MonthlyCharges  | Indicates payment consistency |
| TenureGroup       | Categorized tenure             | Captures loyalty segments     |
| HighValue         | Binary based on median charges | Identifies premium customers  |

**Impact:**
These features improved the model’s ability to capture customer behavior patterns.

---

 🔎 8. Feature Selection

* Correlation heatmap used for numerical features
* Removed irrelevant features like CustomerID

**Key Insight:**
Tenure and MonthlyCharges showed strong relationships with churn.

---
🤖 9. Model Selection

### Model Used: Random Forest Classifier

**Why Random Forest?**

* Handles both categorical and numerical data
* Captures non-linear relationships
* Reduces overfitting through ensemble learning
* Provides feature importance

---

📈 10. Model Evaluation

### Metrics Used:

* **Accuracy** – Overall correctness
* **Precision** – Correct positive predictions
* **Recall** – Ability to detect churn cases
* **F1 Score** – Balance between precision and recall

### 🔍 Key Insight:

Recall is particularly important because failing to identify a churning customer can lead to revenue loss.

---

 🧪 11. Validation Strategy

* Train-Test Split (80:20)
* Stratified sampling used to maintain class balance

---

 📊 12. Visualizations

The following visualizations were used:

* Correlation Heatmap
* Confusion Matrix
* ROC Curve
* Feature Importance Plot

---

 🧠 13. Key Insights

* Customers with longer tenure are less likely to churn
* Higher monthly charges are associated with increased churn risk
* Contract type significantly impacts customer retention

---

🏁 14. Conclusion

This project demonstrates a complete machine learning workflow including preprocessing, feature engineering, and model evaluation.

The inclusion of engineered features and proper preprocessing significantly improved model performance and interpretability.

---

 🚀 15. Future Improvements

* Apply advanced models (XGBoost, LightGBM)
* Perform hyperparameter tuning
* Handle class imbalance using SMOTE
* Deploy model using Streamlit or Flask

---

 ⚙️ 16. Setup Instructions

```bash
pip install -r requirements.txt
```

Run the notebook:

1. Open Jupyter Notebook
2. Load `churn_prediction_pipeline.ipynb`
3. Run all cells

---

 📁 17. Project Structure

```
customer-churn/
│
├── churn_prediction_pipeline.ipynb
├── churn_data.csv
├── preprocessing_report.md
├── feature_engineering_documentation.md
├── requirements.txt
└── README.md
```

---
