# Model Tuning and Ensemble Learning
This project explores model evaluation, cross-validation, hyperparameter tuning, and ensemble learning using the Breast Cancer Wisconsin dataset.

## Workflow

- Exploratory Data Analysis
- Data Cleaning
- Data Preprocessing and Scaling
- Baseline Classification Models
- 5-Fold Cross-Validation
- Decision Tree Hyperparameter Tuning using GridSearchCV
- Random Forest
- AdaBoost
- Gradient Boosting
- XGBoost
- Stacking

## Models Evaluated

- Logistic Regression
- Naive Bayes
- SVM
- KNN
- Decision Tree
- Random Forest
- AdaBoost
- Gradient Boosting
- XGBoost
- Stacking

## Key Results

Malignant recall was treated as an important evaluation metric because class `0` represents malignant tumors.

- Logistic Regression: ~98% malignant recall
- SVM: ~98% malignant recall
- Tuned Decision Tree: ~95% malignant recall
- Random Forest: ~93% malignant recall
- Stacking: ~98% malignant recall

Cross-validation showed that performance from a single train-test split may not always represent how consistently a model performs.

GridSearchCV improved the Decision Tree's mean malignant recall from approximately 87.6% to 92.9%.

## Key Learning

More complex models do not automatically produce better results. Model performance should be evaluated using metrics that match the problem rather than relying only on accuracy.
