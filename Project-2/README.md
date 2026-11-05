# House Price Prediction: Advanced Regression

A regression project that predicts **house prices (INR)** and compares regularized linear models, tree-based models and Support Vector Regression, using several cross-validation strategies.

---

## Project Structure

| File | Description |
|---|---|
| `Predictive_Insight_Engine.ipynb` | Part A: Simple, Multiple and Polynomial Regression, Gradient Descent, bias-variance analysis (dataset: `RealEstate_HousePrice_Dataset.csv`) |
| `regularized_regression.py` | Parts B, C, D: preparation, Ridge/Lasso, cross-validation strategies |
| `part_efg.py` | Parts E, F, G: Decision Tree, Random Forest, SVR, final comparison |
| `Advanced_Regression_HousePrice.csv` | Dataset for Parts B to G (3,800 rows) |
| `model_comparison.csv`, `coefficients.csv`, `cv_comparison.csv` | Output tables from Parts C and D |
| `model_comparison_all.csv` / `.png` | Final comparison of all models (Part G) |
| `alpha_and_coef_paths.png` | Alpha tuning curve and Ridge/Lasso coefficient paths |

---

## Dataset (Parts B to G)

- **Rows:** 3,800, with no missing values
- **Target:** `house_price_inr`
- **Features (9):**

| Group | Columns |
|---|---|
| Size / structure | `area_sqft`, `bedrooms`, `bathrooms` |
| Location | `location_score`, `distance_city_km`, `near_school`, `near_metro`, `crime_rate_index` |
| Age | `property_age` |

- `property_id` is only an identifier, so it is excluded.
- `sale_date` is not a feature. It is used only to order the data for Time Series cross-validation.

---

## Methodology

- **Split:** 80% train / 20% test (`random_state=42`)
- **Scaling:** `StandardScaler` inside a `Pipeline`, so it is fit only on training folds (no data leakage)
- **Tuning:** `GridSearchCV` with 5-fold CV, scored on RMSE
- **SVR:** both features and target are scaled (`TransformedTargetRegressor`), since prices are in the millions
- **Metrics:** MSE, MAE, RMSE, R² (train and test), plus the train-test R² gap to detect over/underfitting

---

## Parts and Tasks

| Part | Tasks | Topic |
|---|---|---|
| B | 6 to 8 | Features/target, train-test split, scaling |
| C | 9 to 12 | Ridge (L2), Lasso (L1), alpha tuning, comparison |
| D | 13, 14 | K-Fold, Stratified K-Fold, Leave-One-Out, Time Series Split |
| E | 15 to 18 | Decision Tree, complexity control, Random Forest, tree vs ensemble |
| F | 19 to 21 | SVR (linear, RBF), tuning C, gamma, epsilon |
| G | 22 to 24 | Metrics, model-family comparison, overfitting/underfitting |

---

## Key Results

### Part C: Regularized models
Best alpha: **Ridge ≈ 1.94**, **Lasso ≈ 12,638**.

| Model | Train RMSE | CV RMSE | Test RMSE | Test R² |
|---|---|---|---|---|
| OLS | 2.5006M | 2.5117M | 2.5581M | 0.919 |
| Ridge | 2.5006M | 2.5117M | 2.5587M | 0.919 |
| Lasso | 2.5008M | 2.5114M | 2.5611M | 0.919 |

Regularization barely changes performance, because the data has few features, many rows and little collinearity. `area_sqft` and `location_score` dominate the coefficients. Lasso shrinks weak features (`near_school`, `distance_city_km`) the most.

### Part D: Cross-validation strategies (mean RMSE)

| Strategy | Ridge | Lasso |
|---|---|---|
| K-Fold (k=5) | 2,516,718 | 2,516,725 |
| K-Fold (k=10) | 2,515,271 | 2,515,400 |
| Stratified K-Fold (k=5) | 2,514,824 | 2,514,691 |
| Leave-One-Out | 2,518,003 | 2,518,202 |
| Time Series Split (k=5) | 2,524,435 | 2,523,985 |

All strategies agree within about 0.4%. Stratified K-Fold has the lowest fold variance. Time Series Split gives the highest error because it trains on the past and tests on the future.

### Parts E, F, G: All models (test set)

| Model | Test RMSE | Test R² | Train R² | Gap |
|---|---|---|---|---|
| **SVR (RBF)** | **2.29M** | **0.935** | 0.942 | 0.008 |
| Random Forest (tuned) | 2.41M | 0.928 | 0.964 | 0.037 |
| OLS / Ridge / Lasso | 2.56M | 0.919 | 0.916 | ≈ 0 |
| SVR (linear) | 2.58M | 0.917 | 0.915 | ≈ 0 |
| Decision Tree (tuned) | 2.74M | 0.907 | 0.930 | 0.023 |
| Decision Tree (unrestricted) | 3.38M | 0.858 | 1.000 | 0.142 |

Best hyperparameters:
- **Decision Tree:** `max_depth=8`, `min_samples_leaf=20`
- **Random Forest:** `max_depth=None`, `min_samples_leaf=5`, `max_features=1.0`
- **SVR (RBF):** `C=10`, `gamma=0.03`, `epsilon=0.1`
- **SVR (linear):** `C=1`

### Conclusions
- **Best model:** RBF SVR has the lowest error and the smallest train-test gap, which suggests a mild non-linear pattern in the data.
- **Overfitting:** the unrestricted Decision Tree memorizes the training data (train R² = 1.0, test 0.858). Limiting depth and leaf size fixes most of it.
- **Ensemble vs single tree:** Random Forest clearly beats a single tree (R² 0.928 vs 0.907).
- **Underfitting:** linear models (OLS, Ridge, Lasso, linear SVR) are slightly underfit, since they miss the non-linear pattern, but they do not overfit.
- **Feature importance (Random Forest):** `area_sqft` (~76%) and `location_score` (~21%) drive almost all predictions.

---

## How to Run

### 1. Install requirements
```bash
pip install numpy pandas scikit-learn matplotlib seaborn jupyter
```

### 2. Run Parts B to D
```bash
python regularized_regression.py
```

### 3. Run Parts E to G
```bash
python part_efg.py
```
This takes a few minutes because of the grid searches (SVR and Random Forest). Both scripts read the CSV from the path set near the top of the file, so update it to match your folder.

### 4. Run Part A
Open `Predictive_Insight_Engine.ipynb` in Jupyter and run the cells top to bottom (with `RealEstate_HousePrice_Dataset.csv` in the same folder).

> **Note:** a few cells in the notebook need fixes before "Run All" works: some variable names are undefined (`linear_model`, `y_pred_linear`, `X_train_scaled`, `y_train_scaled`) and `time` is not imported.

---

## Notes

- Leave-One-Out fits the model 3,800 times, so it is the slowest step.
- Stratified K-Fold needs classes, so the continuous price is binned into 5 quantile groups only to define the folds.
- The alpha grid for Ridge/Lasso is very wide (0.01 to 10⁷) because the target is in the millions.

---

## Tech Stack

Python · NumPy · Pandas · scikit-learn · Matplotlib · Seaborn
