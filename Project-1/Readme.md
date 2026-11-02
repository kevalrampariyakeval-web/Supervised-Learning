🏡 Predictive Insight Engine – Real Estate House Price Prediction
A Machine Learning project that explores real estate data and predicts house prices using regression techniques. The project covers data exploration, visualization, model training, evaluation, Gradient Descent, and bias–variance analysis.
📌 Project Overview
The Predictive Insight Engine uses property-related features to study and predict house prices. The target variable is `house_price_inr`, which represents the house price in Indian Rupees.
The notebook compares Simple Linear Regression, Multiple Linear Regression, and Polynomial Regression, and also demonstrates three Gradient Descent approaches.
🎯 Project Objectives
Explore and understand the real estate dataset.
Analyze how property features relate to house prices.
Visualize data distributions and feature correlations.
Build and compare regression models.
Evaluate predictions using regression metrics.
Understand Gradient Descent and the bias–variance trade-off.
📂 Dataset Description
Dataset: `RealEstate_HousePrice_Dataset.csv`  
Records: 4,200 rows  
Features: 11 input columns and 1 target column
Column	Description
`house_id`	Unique house identifier (excluded from model inputs)
`area_sqft`	House area in square feet
`bedrooms`	Number of bedrooms
`bathrooms`	Number of bathrooms
`location_score`	Numerical location score
`age_years`	Age of the house in years
`distance_city_km`	Distance from the city in kilometres
`lot_size_sqft`	Lot size in square feet
`has_garage`	Indicates whether the property has a garage
`has_pool`	Indicates whether the property has a swimming pool
`renovation_years_ago`	Number of years since renovation
`house_price_inr`	House price in Indian Rupees (target)
🛠️ Technologies and Libraries
Python – Programming language
Jupyter Notebook – Development environment
NumPy – Numerical operations
Pandas – Data loading and manipulation
Matplotlib – Data visualization
Seaborn – Statistical visualization
Scikit-learn – Regression models, data splitting, preprocessing, and evaluation
🔍 Project Workflow
1. Data Loading and Exploration
Load the CSV dataset using Pandas.
Inspect column names, data types, and summary statistics.
Check for missing values and duplicate records.
2. Exploratory Data Analysis (EDA)
The notebook includes:
Scatter plot: house area vs. house price.
Box plot: house prices by number of bedrooms.
Correlation heatmap: relationships between numerical features.
3. Feature Selection
Independent variables (`X`): All columns except `house_id` and `house_price_inr`.
Dependent variable (`y`): `house_price_inr`.
4. Train-Test Split
The dataset is split into 80% training data and 20% testing data using `random_state=42`.
5. Regression Models
Simple Linear Regression: Uses `area_sqft` as the input feature to predict house price.
Multiple Linear Regression: Uses the available property features to predict house price.
Polynomial Regression: Uses a degree-2 polynomial transformation to model a curved relationship between house area and price.
6. Model Evaluation
The models are evaluated using:
Metric	Meaning
MSE	Mean Squared Error; average squared prediction error
MAE	Mean Absolute Error; average absolute prediction error
RMSE	Root Mean Squared Error; error expressed in the target variable's unit
R² Score	Measures how well the model explains variation in house prices
Adjusted R²	R² adjusted for the number of input features
The notebook also compares training and testing R² scores to examine model fit and generalization.
7. Gradient Descent
The notebook demonstrates three optimization methods:
Batch Gradient Descent: Updates parameters using the complete training dataset.
Stochastic Gradient Descent: Updates parameters one training example at a time.
Mini-Batch Gradient Descent: Updates parameters using small groups of training examples.
Their loss values, convergence behaviour, and training times are compared.
8. Bias–Variance Analysis
Simple, Multiple, and Polynomial Regression are compared using training and testing R² scores and evaluation metrics. This helps in understanding underfitting, overfitting, and model generalization.
📁 Project Structure
```text
Predictive-Insight-Engine/
│
├── Predictive_Insight_Engine.ipynb
├── RealEstate_HousePrice_Dataset.csv
└── README.md
```
⚙️ How to Run the Project
Clone or download this repository.
Install Python and Jupyter Notebook.
Install the required libraries:
```bash
   pip install numpy pandas matplotlib seaborn scikit-learn jupyter
   ```
Keep the notebook and CSV dataset in the same folder.
Start Jupyter Notebook:
```bash
   jupyter notebook
   ```
Open `Predictive_Insight_Engine.ipynb`.
Run the notebook cells in order.
📚 Learning Outcomes
Understand a regression-based Machine Learning problem.
Perform data exploration and visualization.
Separate input features and the target variable.
Train and compare regression models.
Evaluate predictions with regression metrics.
Understand Gradient Descent, overfitting, underfitting, and bias–variance analysis.
📝 Conclusion
This project demonstrates an introductory Machine Learning workflow for real estate house price prediction. It uses exploratory data analysis, regression algorithms, optimization techniques, and model evaluation to examine how property features can help estimate house prices.
---
Project Name: Predictive Insight Engine  
Domain: Machine Learning | Real Estate Analytics  
Target Variable: `house_price_inr`