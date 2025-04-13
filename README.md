# 📊 Customer Churn Prediction

This project aims to build predictive models to identify customer churn using a classification-based approach. The dataset contains customer-level information, including both numerical and categorical features, with the target variable `churn` indicating whether a customer has left the service (`1`) or not (`0`).

---

## 📁 Dataset Overview

- **Total Rows:** 5000  
- **Total Columns:** 20  
  - **Numerical Features:** 15  
  - **Categorical Features:** 5  
- **Target Column:** `churn` (0: No, 1: Yes)

---

## 🔍 Exploratory Data Analysis

- No missing or duplicate values found.
- Most features follow an approximately normal distribution.
- Outliers detected using **IQR method**:
  - Majority of features had outliers in the range **0–2%**
  - `number_customer_service_calls` had ~**8%** outliers
- **Label encoding** applied to categorical features
- **Feature scaling** with MinMaxScaler (after train-test split to avoid data leakage)

---

## 🔄 Data Transformations

- **Box-Cox Transformation** applied to numerical variables to stabilize variance and make data more normally distributed
- **Yeo-Johnson Transformation** used for features with non-positive values
- Outliers excluded using IQR method
- **One-hot encoding** used for categorical variables in later experiments

---

## ⚙️ Modeling Pipeline

- **Train-Test Split:** 70-30  
- **Scaling:** MinMaxScaler  
- **Target Class Imbalance:** Present (Handled using SMOTE & its variants)

### Algorithms Used:

- Logistic Regression
- Random Forest
- Support Vector Machine (SVM)
- K-Nearest Neighbors (KNN)
- Naive Bayes
- AdaBoost
- Gradient Boosting
- XGBoost

---

## 🧪 Evaluation Metrics

- **Accuracy**
- **Recall**
- **ROC-AUC**
- **Matthews Correlation Coefficient (MCC)**

> MCC is a reliable metric for imbalanced datasets as it accounts for true/false positives and negatives.

---

## 🧾 Initial Model Performance (Without Resampling)

| Model              | Test Accuracy | Test MCC | Test ROC-AUC |
|-------------------|---------------|----------|--------------|
| Logistic Regression | 0.8400        | 0.1992   | 0.7123       |
| Random Forest      | 0.9033        | 0.6110   | 0.7939       |
| SVM                | 0.8593        | 0.3572   | 0.7734       |
| KNN                | 0.8527        | 0.3304   | 0.6794       |
| AdaBoost           | 0.8493        | 0.2895   | 0.7340       |
| Gradient Boosting  | 0.8987        | 0.5880   | 0.7965       |
| XGBoost            | 0.8973        | 0.5839   | 0.7927       |

---

## 📌 Performance After SMOTE

| Model              | Test Accuracy | Test MCC |
|-------------------|---------------|----------|
| Logistic Regression | 0.7127        | 0.2717   |
| Random Forest      | 0.8847        | 0.5544   |
| SVM                | 0.7973        | 0.3865   |
| KNN                | 0.6753        | 0.2254   |
| Naive Bayes        | 0.7607        | 0.3279   |
| AdaBoost           | 0.7947        | 0.3334   |
| Gradient Boosting  | 0.8813        | 0.5369   |
| XGBoost            | 0.8900        | 0.5624   |

---

## ⚖️ Oversampling Techniques Comparison (Gradient Boosting)

| Technique           | Test Accuracy | Test MCC |
|---------------------|---------------|----------|
| SMOTE               | 0.9014        | 0.5862   |
| BorderlineSMOTE-1   | 0.8943        | 0.5517   |
| BorderlineSMOTE-2   | 0.8943        | 0.5553   |
| SVMSMOTE            | 0.8900        | 0.5301   |
| ADASYN              | 0.8929        | 0.5425   |

---

## 🚀 Future Enhancements

- Hyperparameter tuning for top-performing models
- Explore advanced feature transformation techniques
- Try alternative encoding and scaling methods
- Refine outlier removal techniques
- Explore ensemble stacking and blending
---

## 🧠 Key Takeaways

- Class imbalance significantly affects model performance
- MCC provides better evaluation for imbalanced classification
- Boosting methods, especially Gradient Boosting and XGBoost, show strong performance
- SMOTE and its variants improved generalization and recall
---
