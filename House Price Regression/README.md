<div align="center">

# 🏠 House Price Prediction Using Machine Learning

### 📊 Regression Models for House Price Estimation

Predicting house prices using multiple machine learning regression algorithms and comparing their performance.

<br>

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-orange?style=for-the-badge&logo=scikitlearn)
![Status](https://img.shields.io/badge/Project-Completed-success?style=for-the-badge)

</div>

---

# 📌 Project Overview

This project focuses on predicting house prices using different Machine Learning Regression models.

The complete workflow includes:

- Data Exploration
- Data Preprocessing
- Feature Scaling
- Model Training
- Cross Validation
- Model Evaluation
- Model Comparison

The objective is to compare different regression algorithms and identify the model that gives the best prediction performance.

---

# 🎯 Project Objective

The main objective of this project is to build and evaluate multiple regression models for house price prediction.

By comparing different algorithms, we can understand which model performs best on the given dataset.

---

# 📂 Dataset Information

The dataset contains house-related numerical features and a target variable.

### Target Variable

```text
house_price_inr
```

### Dataset Analysis Performed

✔ Dataset Shape

✔ Dataset Information

✔ Missing Value Analysis

✔ Statistical Summary

✔ Numerical Feature Analysis

---

# 🔍 Exploratory Data Analysis (EDA)

Before training the models, the dataset was explored to understand its structure and quality.

### EDA Steps

- Viewing sample records
- Checking dataset dimensions
- Inspecting data types
- Finding missing values
- Understanding feature distributions
- Generating summary statistics

These steps helped in preparing the dataset for machine learning.

---

# ⚙️ Data Preprocessing

### Feature and Target Separation

```text
X → Input Features

y → House Price
```

### Train-Test Split

The dataset was divided into:

```text
80% → Training Data

20% → Testing Data
```

This allows the model to learn from one portion of the data and be evaluated on unseen records.

### Feature Scaling

StandardScaler was used to standardize numerical features before training certain models.

Benefits:

- Brings features to a similar scale
- Improves model performance
- Helps algorithms converge efficiently

---

# 🤖 Machine Learning Models Used

## 1️⃣ Ridge Regression

Ridge Regression is a regularized regression model that helps reduce overfitting by adding a penalty term.

### Advantages

✔ Reduces overfitting

✔ Handles multicollinearity

✔ Improves model stability

---

## 2️⃣ Lasso Regression

Lasso Regression also applies regularization and reduces the influence of less important features.

### Advantages

✔ Feature selection capability

✔ Reduces model complexity

✔ Improves interpretability

---

## 3️⃣ Decision Tree Regression

Decision Tree Regression learns patterns through a tree-like structure of decision rules.

### Advantages

✔ Easy to understand

✔ Captures non-linear relationships

✔ Requires minimal preprocessing

---

## 4️⃣ Random Forest Regression

Random Forest combines multiple decision trees and produces predictions using ensemble learning.

### Advantages

✔ Better accuracy

✔ Reduced overfitting

✔ Strong prediction performance

✔ Works well on complex datasets

---

## 5️⃣ Support Vector Regression (SVR)

Support Vector Regression was implemented using:

### Linear Kernel

Used for learning linear relationships.

### RBF Kernel

Used for learning more complex non-linear relationships.

---

# 🔄 Cross Validation Techniques

To evaluate model reliability, the following validation techniques were used.

## K-Fold Cross Validation

The dataset is divided into multiple folds.

Each fold gets a chance to be used as testing data while the remaining folds are used for training.

### Benefits

✔ Better performance estimation

✔ Reduced evaluation bias

---

## Leave-One-Out Cross Validation (LOOCV)

In LOOCV:

```text
1 Observation → Testing

Remaining Observations → Training
```

This process is repeated for every observation in the dataset.

---

# 📊 Evaluation Metrics

The performance of each model was measured using:

| Metric | Description |
|----------|------------|
| MAE | Mean Absolute Error |
| MSE | Mean Squared Error |
| RMSE | Root Mean Squared Error |
| R² Score | Measures prediction accuracy |

---

# 📈 Model Performance Comparison

| Model | R² Score |
|---------|---------|
| Ridge Regression | 0.9187 |
| Lasso Regression | 0.9187 |
| Decision Tree Regression | 0.8836 |
| Random Forest Regression | **0.9265** |
| Linear SVR | -0.0019 |
| RBF SVR | -0.0029 |

---

# 🏆 Best Performing Model

<div align="center">

# 🥇 Random Forest Regression

</div>

### Why It Performed Best?

✔ Highest R² Score

✔ Better prediction accuracy

✔ Reduced overfitting

✔ Strong generalization ability

✔ Consistent performance on unseen data

---

# 💡 Key Learnings

Through this project, the following concepts were explored:

- Data Exploration
- Data Preprocessing
- Feature Scaling
- Ridge Regression
- Lasso Regression
- Decision Tree Regression
- Random Forest Regression
- Support Vector Regression
- Cross Validation
- Model Evaluation
- Model Comparison

---

# 🛠️ Technology Stack

| Technology | Purpose |
|------------|----------|
| Python | Programming Language |
| Pandas | Data Analysis |
| NumPy | Numerical Operations |
| Matplotlib | Data Visualization |
| Scikit-Learn | Machine Learning |
| Jupyter Notebook | Development Environment |

---

# 📁 Project Structure

```text
House_Price_Prediction/
│
├── House_Price_Regression_Notebook.ipynb
├── Dataset.csv
├── README.md
│
└── Outputs/
```

---

# 🎯 Conclusion

This project demonstrates a complete Machine Learning workflow for predicting house prices using multiple regression algorithms.

Several models were trained, evaluated, and compared using standard performance metrics.

Among all models, **Random Forest Regression** achieved the highest R² Score and delivered the best overall performance on the dataset.

This project helped build practical understanding of regression modeling, model evaluation, feature scaling, and cross-validation techniques.

---

<div align="center">

## ⭐ Thank You for Visiting This Project ⭐

### 👨‍💻 Author

**Keval Rampariya**

</div>



