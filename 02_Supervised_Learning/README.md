
# Energy Efficiency: Linear Regression & Model Evaluation

This is the second hands-on project in my Machine Learning learning series.

In the previous project, I focused on EDA, data cleaning, preprocessing, and feature selection without moving into model training.

After learning the fundamentals of supervised learning and regression, the goal of this project was to take the next step: build and evaluate my first regression model and understand how preprocessing and feature choices affect model performance.

## What I Practiced

- Understanding regression problems and continuous target variables
- Simple vs Multiple Linear Regression
- Focused Exploratory Data Analysis (EDA)
- Numerical feature and distribution analysis
- Domain and logical value validation
- Identifying numerical values that actually represent categories
- One-Hot Encoding using 
- Pearson Correlation analysis
- Train-Test Split
- Preventing data leakage during preprocessing
- Feature standardization using 
- Multiple Linear Regression using Scikit-learn
- Model prediction on unseen test data
- Regression model evaluation using:
  - R² Score
  - Adjusted R²
  - MAE
  - MSE
  - RMSE
- Comparing different feature sets through Model A and Model B

## Dataset

Energy Efficiency Dataset

The dataset contains 8 building-related input attributes and two continuous target variables:

- `Y1` – Heating Load
- `Y2` – Cooling Load

For this project, only **Heating Load (`Y1`)** was selected as the prediction target.

`Y2` was not included as an input feature because it is also a target variable. Predicting Cooling Load can be explored separately in a future experiment.

## Preprocessing Insights

Although all columns were stored as numerical values, `X6` (Orientation) and `X8` (Glazing Area Distribution) represent categories rather than actual numerical quantities.

These features were therefore One-Hot Encoded before model training.

The dataset was split into training and testing data before standardization. `StandardScaler` was fitted only on the training data and the same learned transformation was applied to the test data to avoid data leakage.

Correlation analysis also showed that several input features were strongly related to each other, while some encoded features had very weak individual correlations with Heating Load.

## Model Training & Experiment

Since multiple input features were used to predict one continuous target, **Multiple Linear Regression** was applied using Scikit-learn's `LinearRegression`.

I first created **Model A** using the complete encoded feature set as the baseline model.

Model A achieved approximately:

- R²: `0.921`
- Adjusted R²: `0.913`
- MAE: `2.059`
- MSE: `8.250`
- RMSE: `2.872`

After observing very weak individual correlations between the encoded `X6` and `X8` features and Heating Load, I tested whether removing these features would improve the model.

**Model B** was trained without these features using the same train-test split settings.

Model B achieved approximately:

- R²: `0.912`
- Adjusted R²: `0.908`
- MAE: `2.164`
- MSE: `9.217`
- RMSE: `3.036`

## Model Comparison Insight

Model A performed slightly better than Model B.

Removing features with weak individual correlation did not improve the model. R² and Adjusted R² decreased slightly, while MAE, MSE, and RMSE increased.

This experiment helped me understand that **low individual correlation does not automatically mean a feature is useless to a model**. Feature-removal decisions can be tested by comparing actual model performance instead of relying only on correlation values.

## Learning Progress

This project connected the preprocessing concepts practiced in my first project with actual supervised model training and evaluation.

The focus was not only on implementing Linear Regression, but also on understanding why the data is split before scaling, how unseen test data should be handled, how multiple features are used in Multiple Linear Regression, and how evaluation metrics help compare different model versions.

## Next Step

Continue exploring supervised learning by learning **classification algorithms** and applying them to a classification problem.
