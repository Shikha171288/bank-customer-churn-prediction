# Bank Customer Churn Prediction

## Project Overview

Customer churn occurs when customers stop using a company’s products or services. Predicting churn helps a bank identify customers who may leave and take preventive action.

This project analyses bank customer behaviour and builds machine-learning models to predict whether a customer is likely to churn.

## Business Problem

The bank wants to:

- Identify customers who are at risk of leaving.
- Understand the factors associated with customer churn.
- Support targeted customer-retention campaigns.
- Reduce the financial cost of losing customers.

## Dataset

The dataset contains 10,000 customer records and 14 original columns.

Target variable:

- `Exited = 0`: Customer stayed with the bank.
- `Exited = 1`: Customer left the bank.

The dataset includes:

- Credit score
- Geography
- Gender
- Age
- Tenure
- Account balance
- Number of products
- Credit-card ownership
- Active-member status
- Estimated salary

The identifier columns `RowNumber`, `CustomerId`, and `Surname` were removed before model training.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Google Colab

## Project Workflow

1. Data understanding
2. Data cleaning
3. Exploratory data analysis
4. Feature selection
5. One-hot encoding
6. Numerical-feature standardisation
7. Train-test split
8. Baseline-model training
9. Random Forest training
10. Class-imbalance experiment
11. Hyperparameter tuning
12. Final model evaluation
13. Business recommendations

## Exploratory Data Analysis

Important observations from the analysis:

- The overall churn rate was 20.37%.
- Customers from Germany had a churn rate of 32.44%.
- Female customers showed higher observed churn than male customers.
- Inactive customers showed considerably higher churn than active customers.
- Older customers had a higher tendency to churn.
- Customers using three or four products showed unusually high churn.
- Credit-card ownership had little relationship with churn.
- Customers with a non-zero balance showed higher churn than zero-balance customers.

These observations represent associations in this dataset and do not necessarily prove causation.

## Data Preprocessing

The following preprocessing steps were performed:

- Removed identifier columns.
- Checked missing values and duplicate records.
- One-hot encoded `Geography` and `Gender`.
- Standardised numerical features.
- Split the data into 80% training and 20% testing sets.
- Used `random_state=42` to make the results reproducible.

## Model Performance

| Model | Accuracy | Precision | Recall | F1-score |
|---|---:|---:|---:|---:|
| Logistic Regression | 80.80% | 58.91% | 18.67% | 28.35% |
| Random Forest | 86.45% | 78.33% | 46.19% | 58.11% |
| Tuned Random Forest | 86.55% | 78.28% | 46.93% | 58.68% |

The tuned Random Forest produced the strongest overall performance.

## Final Confusion Matrix

```text
[[1540, 53],
 [216, 191]]
```

The model correctly identified:

- 1,540 customers who stayed.
- 191 customers who churned.

It incorrectly classified:

- 53 customers as churned when they stayed.
- 216 churned customers as customers who would stay.

## Best Model Parameters

```python
{
    "n_estimators": 100,
    "max_depth": None,
    "min_samples_split": 5,
    "min_samples_leaf": 1
}
```

## Important Features

The most influential features in the Random Forest model included:

1. Age
2. Estimated salary
3. Credit score
4. Account balance
5. Number of products
6. Tenure
7. Active-member status
8. Geography

## Business Recommendations

- Create retention campaigns for inactive customers.
- Give additional attention to older and high-risk customers.
- Investigate the high churn observed among German customers.
- Examine why customers with three or four products show unusually high churn.
- Contact high-risk customers with personalised offers or loyalty benefits.
- Use the model as an early-warning system for the customer-retention team.
- Retrain and monitor the model as new customer data becomes available.

## Limitations and Future Improvements

Although the model achieved 86.55% accuracy, its churn recall was 46.93%. This means that it missed some customers who actually left the bank.

Future improvements could include:

- Decision-threshold adjustment
- SMOTE or other resampling methods
- Cost-sensitive learning
- Gradient-boosting models
- SHAP-based model explanations
- Deployment as an interactive prediction application

## Repository Files

- `Bank_Customer_Churn_Prediction.ipynb`: Complete analysis and model development
- `Churn_Modelling.csv`: Project dataset
- `README.md`: Project documentation
- `.gitignore`: Files excluded from version control

## Final Conclusion

The project developed a machine-learning model capable of predicting bank customer churn with 86.55% accuracy. It also identified customer groups associated with higher churn.

The model can support customer-retention decisions, but recall should be improved before using it as the only system for business decisions.
