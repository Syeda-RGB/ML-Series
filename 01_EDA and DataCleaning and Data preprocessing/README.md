# Loan Default : EDA, Data Cleaning & Preprocessing

This is the first hands-on project in my Machine Learning learning series.

The goal of this project was to apply the data preparation concepts I learned before moving to model training.

## What I Practiced

- Exploratory Data Analysis (EDA)
- Numerical and categorical feature analysis
- Missing value handling
- Duplicate checking
- Outlier detection using IQR and boxplots
- Data consistency and domain validation
- Categorical encoding
  - Label Encoding
  - One-Hot Encoding
  - Ordinal Encoding
- Feature standardization using StandardScaler
- Feature selection using:
  - Pearson Correlation
  - Chi-Square Test
  - ANOVA F-Test

## Feature Selection Insights

- No extremely high correlation was found between numerical features.
- Most categorical features showed a significant association with the target.
- `construction_type` and `Security_Type` were identified as weak categorical feature candidates.
- `term` and `Credit_Score` were identified as weak numerical feature candidates.
- These features were not removed yet; their usefulness can later be compared during model training and evaluation.

## Dataset

Loan Default Dataset

Target variable: `Status`

> The dataset file is not included in this repository due to its size.

## Next Step

Model training and evaluation will be explored after learning the relevant machine learning concepts.
