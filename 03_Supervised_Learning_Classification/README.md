
# Loan Default Prediction — Supervised Learning Classification

This project extends my previous Loan Default EDA and preprocessing work into supervised classification.

The main goal was not only to train classification algorithms, but also to understand how different models behave, evaluate their predictions, and investigate unusual results.

## Models Implemented

- Logistic Regression
- K-Nearest Neighbors (KNN)
- Gaussian Naive Bayes
- Decision Tree

## Workflow

- Reused the cleaned and preprocessed Loan Default dataset
- Applied Label Encoding and One-Hot Encoding
- Performed Train/Test Split
- Applied Standard Scaling where required
- Trained multiple classification models
- Evaluated models using:
  - Accuracy
  - Precision
  - Recall
  - F1 Score
- Compared model performance
- Performed controlled feature-selection experiments
- Investigated False Negatives from Logistic Regression
- Analyzed suspicious Decision Tree performance

## Initial Model Results

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---:|---:|---:|---:|
| Logistic Regression | 0.874 | 0.930 | 0.529 | 0.675 |
| KNN | 0.891 | 0.837 | 0.695 | 0.759 |
| Naive Bayes | 0.926 | 0.773 | 0.990 | 0.868 |
| Decision Tree | 1.000 | 1.000 | 1.000 | 1.000 |

## Key Investigation

The Decision Tree initially achieved perfect classification results.

Instead of assuming that it was simply the best-performing model, I investigated the reason behind this unusually high performance.

Feature-importance analysis showed that the tree relied heavily on features such as:

- `Interest_rate_spread`
- `credit_type_EQUI`
- `Upfront_charges`

Further analysis of the original dataset revealed that missing values in several features were strongly associated with the target variable.

For example:

- Missing `Interest_rate_spread` → almost always `Status = 1`
- Missing `rate_of_interest` → almost always `Status = 1`
- Missing `LTV` and `property_value` → almost always `Status = 1`
- `credit_type = EQUI` → almost always associated with `Status = 1`

This explained why the Decision Tree was able to achieve unusually high performance.

Therefore, its perfect score should be interpreted carefully rather than automatically considering it the best model.

## Feature Selection Experiment

`ID` and `year` were removed because:

- `ID` was only an identifier and provided no meaningful loan information.
- `year` was constant across the dataset and therefore provided no discriminative information.

Removing `ID` slightly improved KNN performance, particularly Recall and F1 Score.

## Logistic Regression Error Analysis

Logistic Regression achieved high Precision but relatively low Recall.

To understand this, the positive class was divided into:

- True Positives — correctly detected positive cases
- False Negatives — positive cases missed by the model

A major observation was that Logistic Regression detected `credit_type_EQUI` positive cases very well, while many of the missed positive cases belonged to non-EQUI credit types.

Further comparison showed differences in features such as:

- Property value
- Loan amount
- Income
- Debt-to-income ratio
- Loan-to-value ratio

This analysis helped identify where the model was struggling rather than relying only on the final evaluation score.

## Key Learning

This project helped me understand that:

- Accuracy alone is not enough for evaluating classification models.
- Precision and Recall can reveal very different model behavior.
- F1 Score provides a useful balance between Precision and Recall.
- Low Pearson correlation does not mean a feature has no predictive relationship.
- Missingness itself can contain strong information about the target.
- Different ML algorithms can detect very different patterns in the same dataset.
- Extremely high model performance should be investigated rather than accepted immediately.
- Feature engineering should be based on model behavior and data understanding rather than randomly changing features.

## Future Work

I plan to revisit this project after learning model optimization techniques and explore:

- Hyperparameter tuning
- Cross-validation
- Class imbalance handling
- Further feature engineering
- Precision–Recall optimization
- More robust model comparison

## Dataset

Loan Default dataset obtained from Kaggle.

---

Part of my **Machine Learning Series**, where I am learning ML concepts through practical implementation and experimentation.
