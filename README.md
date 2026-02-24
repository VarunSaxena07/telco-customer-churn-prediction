# 📊 Telco Customer Churn Prediction

## 📌 Project Overview

This project focuses on predicting customer churn in a telecom company using machine learning.  
The goal is to identify customers who are likely to leave the service, enabling proactive retention strategies.

The project follows a complete ML workflow:
- Data Cleaning
- Exploratory Data Analysis (EDA)
- Feature Engineering
- Model Training
- Model Evaluation
- Model Comparison

---

## 🎯 Business Objective

Customer churn directly impacts revenue.  
The objective is to:

- Identify high-risk customers
- Understand key churn drivers
- Build an interpretable and reliable predictive model

---

## 🗂 Dataset Description

The dataset contains customer demographic, service usage, and billing information such as:

- Demographics (Age, Gender, Dependents)
- Contract Type
- Tenure in Months
- Monthly Charges
- Add-on Services (OnlineSecurity, TechSupport, etc.)
- Payment Method
- Internet Service Details

Target Variable:
- `ChurnLabel` (0 = No, 1 = Yes)

---

## 🧹 Data Preprocessing

### 1️⃣ Removed Irrelevant & Leakage Columns
The following columns were dropped:
- CustomerID (identifier)
- ChurnScore, CLTV, ChurnCategory, ChurnReason (target leakage)
- Geographic columns (City, State, ZipCode, Latitude, Longitude)
- Quarter (single unique value)
- Population (negligible correlation)

### 2️⃣ Missing Values Handling
Missing categorical values (e.g., Offer, InternetType) were treated as meaningful categories rather than dropped.

### 3️⃣ Train-Test Split
- 80% Training
- 20% Testing
- Stratified split to maintain churn distribution

### 4️⃣ Encoding
- One-hot encoding applied after splitting
- Test set aligned with training feature columns
- LabelEncoder used only for target if necessary

### 5️⃣ Feature Scaling
- StandardScaler applied for Logistic Regression
- Scaling ensures stable convergence for gradient-based models

---

## 📊 Exploratory Data Analysis (Key Insights)

- Customers with Month-to-Month contracts churn more frequently.
- Higher Monthly Charges increase churn probability.
- Low tenure customers are significantly more likely to churn.
- Add-on services like OnlineSecurity and TechSupport reduce churn risk.
- SatisfactionScore was highly predictive and significantly increased separability.

After removing SatisfactionScore to avoid dominance:
- Model performance stabilized at realistic levels.

---

## 🤖 Models Used

### 1️⃣ Logistic Regression (Baseline Model)
- Interpretable
- Scaled features
- Strong linear separation observed

### 2️⃣ Random Forest
- Tested for nonlinear relationships
- Performance similar to Logistic Regression

---

## 📈 Model Performance

### Logistic Regression (Final Model)
- Accuracy: ~96%
- Recall (Churn class): Strong detection rate
- ROC-AUC: ~0.90 (after removing SatisfactionScore)

### Random Forest
- ROC-AUC: ~0.89
- No significant improvement over Logistic Regression

Conclusion:
The dataset exhibits strong linear separability, making Logistic Regression a suitable final model.

---

## 🔍 Key Drivers of Churn

Top influential features:

- Tenure in Months
- Monthly Charge
- Contract Type (Two-Year reduces churn)
- Online Security
- Number of Referrals
- Dependents

These align well with business expectations.

---

## 💡 Final Conclusion

- The model effectively identifies high-risk churn customers.
- Performance is strong without target leakage.
- Logistic Regression chosen for interpretability and comparable performance.
- Results suggest pricing, tenure, and contract structure are major churn drivers.

---

## 🚀 Future Improvements

- Threshold tuning for recall optimization
- Cross-validation for robustness
- Hyperparameter tuning
- SHAP analysis for feature interpretability
- Deployment using Flask/FastAPI

---

## 🛠 Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib / Seaborn
- Scikit-learn

---

## 📌 Author

Built as part of a structured end-to-end Machine Learning project to demonstrate:
- Data preprocessing discipline
- Leakage handling awareness
- Model comparison strategy
- Business-focused interpretation
