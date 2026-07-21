# Message Intelligence: Spam vs. Normal Message Classification

A supervised machine learning project that classifies text messages as **spam** or **normal (legit)** using structured, engineered features rather than raw text. Three classification algorithms — KNN, SVM, and Naive Bayes — are trained and compared on the same dataset.

## Problem Statement

Given a message and a set of derived features (keyword scores, sender behavior, message structure), predict whether it is spam (`1`) or normal (`0`). This is a binary classification problem.

## Dataset

`Message_Intelligence_Dataset.csv` — 5,200 rows, 16 columns.

| Column | Type | Description |
|---|---|---|
| `message_id` | int | Unique row identifier (dropped before modeling) |
| `message_text` | text | Raw message content (not used as model input) |
| `message_length` | int | Character count of the message |
| `word_count` | int | Word count of the message |
| `num_urls` | int | Number of URLs found |
| `num_digits` | int | Number of digit characters |
| `num_special_chars` | int | Number of special characters |
| `spam_keyword_score` | int | Score based on presence of spam-associated keywords |
| `legit_keyword_score` | int | Score based on presence of legitimate-message keywords |
| `sender_activity_score` | float | General activity score of the sender |
| `sender_account_age_days` | int | Sender account age in days |
| `messages_sent_last_24h` | int | Messages sent by the sender in the last 24 hours |
| `timestamp` | datetime | When the message was sent (dropped before modeling) |
| `hour_of_day` | int | Hour extracted from `timestamp` |
| `day_of_week` | int | Day of week extracted from `timestamp` |
| `spam_label` | int | **Target** — `0` = normal, `1` = spam |

**Class balance:** ~81% normal, ~19% spam — the dataset is imbalanced, so accuracy alone isn't a sufficient evaluation metric.

**Missing values:** present in `sender_activity_score`, `sender_account_age_days`, and `messages_sent_last_24h`; handled with median imputation.

## Approach

1. **EDA** — inspected shape, dtypes, summary statistics, missing values, class balance, feature distributions, and a correlation heatmap.
   Strongest correlations with `spam_label`: `num_special_chars` (0.93), `messages_sent_last_24h` (0.85), `spam_keyword_score` (0.76).
2. **Preprocessing**
   - Dropped `message_id`, `message_text`, `timestamp` (not usable as raw numeric input)
   - Median imputation for missing values
   - `StandardScaler` for feature scaling
   - 80/20 train-test split, stratified on `spam_label`
3. **Modeling**
   - **KNN** — swept K from 1–20 and compared Euclidean, Manhattan, and Minkowski distance metrics
   - **SVM** — Linear, RBF, and Polynomial kernels; inspected support vector counts and margins via a 2D PCA projection
   - **Gaussian Naive Bayes** — including a from-scratch Bayes' Theorem calculation, verified against `predict_proba()`
4. **Evaluation** — Accuracy, Precision, Recall, F1, confusion matrices, and classification reports for each model.

## Results

| Model | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|
| KNN (K=1) | 1.00 | 1.00 | 1.00 | 1.00 |
| SVM (Linear) | 1.00 | 1.00 | 1.00 | 1.00 |
| SVM (RBF) | 1.00 | 1.00 | 1.00 | 1.00 |
| SVM (Polynomial) | 1.00 | 1.00 | 1.00 | 1.00 |
| Naive Bayes | 1.00 | 1.00 | 1.00 | 1.00 |

All models achieve a perfect score on the test set, with zero misclassified messages. This indicates the features are highly separable for this dataset — a signal that it's likely synthetic or cleanly generated, rather than noisy real-world traffic. On messier real data, the models would be expected to diverge, with SVM generally favoring precision and Naive Bayes generally favoring recall.

Since every metric ties, model selection for deployment should be based on practical considerations:

- **KNN** — simple, no training cost, but slower at inference on large datasets
- **SVM** — strong margin separation, less interpretable, costlier to train
- **Naive Bayes** — fast and probabilistic, assumes feature independence

## Project Structure

```
.
├── Massage_Intelligence.ipynb        # Full analysis and modeling notebook
├── Message_Intelligence_Dataset.csv  # Dataset
└── README.md
```

## Setup

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

## Running

1. Place `Message_Intelligence_Dataset.csv` in the same directory as the notebook.
2. Launch Jupyter and open `Massage_Intelligence.ipynb`.
3. Run all cells in order.

## Author

keval Rampariya
