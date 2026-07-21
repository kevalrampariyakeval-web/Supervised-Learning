# 🛡️ Risk Alert Classifier
 
> A machine learning system that predicts whether a case is **Risky** or **Not Risky**, helping raise early alerts before problems occur.
 
![Python](https://img.shields.io/badge/Python-3.x-blue)
![scikit--learn](https://img.shields.io/badge/scikit--learn-ML-orange)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
 
---
 
## 📖 Overview
 
Risk detection plays a critical role in areas like finance, security, fraud detection and compliance monitoring. A missed risky case can lead to serious consequences, while too many false alarms can make a system unreliable and hard to trust.
 
**Risk Alert Classifier** is an end-to-end machine learning pipeline built to solve exactly this problem — it takes raw data, cleans it, balances it, trains multiple models, tunes the best one, and picks the final model that offers the strongest trade-off between catching real risks and avoiding false alarms.
 
The notebook is written to be beginner-friendly — every code cell is followed by a short **🧠 Intuition** note that explains, in plain and simple words, what that step is doing and why it matters.
 
---
 
## ❓ Problem Statement
 
Given a dataset with multiple features about a case (numerical + categorical), the goal is to classify each case as:
 
- ✅ **Not Risky** — safe, no alert needed
- ⚠️ **Risky** — potential threat, should be flagged
The challenge isn't just building a model — it's building a model that performs well even when risky cases are rare (class imbalance), and one that minimizes **missed risks (Type-II errors)** without triggering too many **false alarms (Type-I errors)**.
 
---
 
## 🔄 Project Workflow
 
1. **🧹 Data Cleaning** — Removing duplicate records and identifying missing values
2. **📊 Exploratory Data Analysis (EDA)** — Studying dataset shape, statistics, target distribution, feature distributions and correlations
3. **🔢 Feature Encoding** — Converting categorical (text) columns into numerical form
4. **🩹 Missing Value Imputation** — Using KNN Imputer to intelligently fill missing data based on similar records
5. **✂️ Train-Test Split** — Splitting the dataset for fair model evaluation
6. **🤖 Baseline Modeling** — Training a Logistic Regression model as a starting benchmark
7. **⚖️ Handling Class Imbalance** — Comparing Random Under Sampling, Random Over Sampling, SMOTE and ADASYN
8. **🌳 Advanced Models** — Training and evaluating Decision Tree and Random Forest classifiers
9. **🛠️ Hyperparameter Tuning** — Improving the Random Forest model with RandomizedSearchCV and GridSearchCV
10. **📉 Final Evaluation** — Comparing all models using ROC Curve, AUC Score and F1-Score to select the best one
---
 
## 📏 Evaluation Metrics Used
 
| Metric | Why It Matters |
|---|---|
| **Accuracy** | Overall correctness of the model |
| **Precision** | How many predicted risky cases were actually risky |
| **Recall** | How many actual risky cases were correctly caught |
| **F1-Score** | Balance between Precision and Recall |
| **Confusion Matrix** | Breakdown of correct vs incorrect predictions |
| **ROC Curve & AUC** | Overall ability of the model to separate risky vs non-risky cases |
 
Special attention is also given to **Type-I errors (false alarms)** and **Type-II errors (missed risks)**, since in a real risk-alert system, missing a genuine risk is usually far more costly than raising an unnecessary alert.
 
---
 
## 🧠 Approach to Class Imbalance
 
Real-world risk data is rarely balanced — risky cases are usually much rarer than safe ones. Training a model directly on such data often makes it biased toward the majority class. To fix this, four different balancing techniques were compared:
 
- **Random Under Sampling** — reduces the majority class
- **Random Over Sampling** — duplicates the minority class
- **SMOTE** — generates new synthetic minority samples
- **ADASYN** — generates more synthetic samples in harder-to-learn regions
Each technique was evaluated fairly using the same test set, so the results reflect real performance differences rather than data leakage.
 
---
 
## 🌟 Models Compared
 
| Model | Type |
|---|---|
| Logistic Regression | Linear baseline model |
| Decision Tree Classifier | Rule-based, easy to interpret |
| Random Forest Classifier | Ensemble of many decision trees |
| Random Forest (RandomizedSearchCV) | Tuned via random hyperparameter search |
| Random Forest (GridSearchCV) | Tuned via exhaustive hyperparameter search |
 
The final model was selected based on the **highest F1-Score**, ensuring a good balance between precision and recall rather than just raw accuracy.
 
---
 
## 🧰 Tech Stack
 
- 🐍 **Python**
- 🐼 **Pandas & NumPy** — data handling
- 📊 **Matplotlib & Seaborn** — visualizations
- 🔬 **Scikit-learn** — models, metrics, and hyperparameter tuning
- ⚖️ **Imbalanced-learn** — SMOTE, ADASYN and sampling techniques
---
 
## ✨ Key Highlights
 
- 📝 Every code cell paired with a simple, beginner-friendly **Intuition** explanation
- ⚖️ Four different imbalance-handling techniques compared side by side
- 🤝 Three core ML models trained and benchmarked against each other
- 🛠️ Two hyperparameter tuning strategies applied for optimization
- 📉 Clear visual evaluation using confusion matrices and ROC curve
---
 
## 💡 Key Takeaway
 
Building a reliable risk alert system isn't just about picking the "best accuracy" model — it's about understanding the real cost of errors, balancing the data fairly, and tuning the model to catch as many genuine risks as possible without overwhelming the system with false alarms.
