# Predicting Term Deposit Subscription

## Project Overview

This project aims to predict whether a client will subscribe to a term deposit based on various features related to the client's demographics, past interactions, and economic context. The purpose is to enhance the efficiency of marketing campaigns by identifying the main characteristics that lead to successful subscriptions.

## Dataset Characteristics

The dataset used in this project is sourced from a direct marketing campaign of a Portuguese banking institution. It contains information collected from telephone calls made to clients. The dataset includes the following features:

- **Age**: Age of the client (numeric)
- **Job**: Type of job (categorical)
- **Marital**: Marital status (categorical)
- **Education**: Level of education (categorical)
- **Default**: Has credit in default? (categorical)
- **Housing**: Has a housing loan? (categorical)
- **Loan**: Has a personal loan? (categorical)
- **Contact**: Contact communication type (categorical)
- **Month**: Last contact month of the year (categorical)
- **Day of Week**: Last contact day of the week (categorical)
- **Duration**: Last contact duration in seconds (numeric)
- **Campaign**: Number of contacts performed during this campaign (numeric)
- **Pdays**: Number of days since the client was last contacted from a previous campaign (numeric)
- **Previous**: Number of contacts performed before this campaign (numeric)
- **Poutcome**: Outcome of the previous marketing campaign (categorical)
- **Emp.var.rate**: Employment variation rate (numeric)
- **Cons.price.idx**: Consumer price index (numeric)
- **Cons.conf.idx**: Consumer confidence index (numeric)
- **Euribor3m**: Euribor 3 month rate (numeric)
- **Nr.employed**: Number of employees (numeric)
- **Target Variable (y)**: Has the client subscribed to a term deposit? (binary)

### Summary Statistics

The dataset consists of 41,188 instances with 21 features. Below are the summary statistics for numerical features:

### Distribution of Numerical Features
![Screenshot 2024-06-01 at 12 11 54 PM](https://github.com/Ohmae22/Predicting-Term-Deposit-Subscription/assets/88304497/b7df3c43-dbef-41e0-a58d-19592a0c79ed)

### Distribution of Categorical Features
<img width="929" alt="Screenshot 2024-06-01 at 12 13 26 PM" src="https://github.com/Ohmae22/Predicting-Term-Deposit-Subscription/assets/88304497/a6d309bd-35d8-402f-ad15-49b032a76788">

### Correlation Matrix
<img width="972" alt="Screenshot 2024-06-01 at 12 14 01 PM" src="https://github.com/Ohmae22/Predicting-Term-Deposit-Subscription/assets/88304497/ae8df4b9-690b-4f7c-afbd-bd2bc15b76fa">

### Target Variable Distribution
<img width="618" alt="Screenshot 2024-06-01 at 12 14 57 PM" src="https://github.com/Ohmae22/Predicting-Term-Deposit-Subscription/assets/88304497/35896721-e342-4dfd-b2e3-6063a9b93560">


## Key Findings and Results

After conducting hyperparameter tuning and feature engineering, we obtained the following results for various models:

| Model                         | Train Accuracy | Test Accuracy | Precision | Recall | F1-score | ROC-AUC |
|-------------------------------|----------------|---------------|-----------|--------|----------|---------|
| Logistic Regression (Initial) | 0.9097         | 0.9115        | -         | -      | -        | -       |
| KNN (Initial)                 | 0.9304         | 0.9033        | -         | -      | -        | -       |
| Decision Tree (Initial)       | 1.0000         | 0.8912        | -         | -      | -        | -       |
| SVM (Initial)                 | 0.8979         | 0.8971        | -         | -      | -        | -       |
| Logistic Regression (Tuned)   | 0.9097         | 0.9124        | 0.6813    | 0.4140 | 0.5150   | 0.9302  |
| KNN (Tuned)                   | 0.9304         | 0.9072        | 0.6177    | 0.4572 | 0.5254   | 0.9107  |
| Decision Tree (Tuned)         | 0.9163         | 0.9163        | 0.6612    | 0.5241 | 0.5847   | 0.9261  |
| SVM (Tuned)                   | 0.9044         | 0.9044        | 0.6962    | 0.2657 | 0.3846   | 0.9126  |


1. Logistic Regression:
Initial vs. Tuned: The performance slightly improved after tuning, with test accuracy increasing from 0.9115 to 0.9124. Precision and recall indicate that the model correctly identifies positive cases reasonably well but struggles with false negatives, reflected in a moderate recall.
Overall Performance: Logistic Regression is robust, showing balanced accuracy and good ROC-AUC scores.

2. K-Nearest Neighbors (KNN):
Initial vs. Tuned: Test accuracy improved from 0.9033 to 0.9072 with tuning. Precision and recall indicate that KNN is more precise in predicting positives but still has room for improvement in recall, leading to moderate F1-scores.
Overall Performance: KNN performs well with an increased number of neighbors (13), showing balanced metrics.

3. Decision Tree:
Initial vs. Tuned: The most significant improvement was observed in Decision Tree, with test accuracy increasing from 0.8912 to 0.9163, and a reduction in overfitting. The model now provides balanced precision and recall, with a good F1-score and ROC-AUC.
Overall Performance: Decision Tree benefits significantly from hyperparameter tuning, particularly in reducing overfitting and improving generalization.

4. Support Vector Machine (SVM):
Initial vs. Tuned: Despite tuning, SVM showed marginal improvement in test accuracy (0.8971 to 0.9044). Precision is high, but recall is notably low, indicating many false negatives and resulting in a lower F1-score.
Overall Performance: SVM, with a linear kernel, offers high precision but struggles with recall, indicating a potential issue with handling imbalanced classes.


### Key Insights

1. **Accuracy Improvement**: All models except SVM showed improved test accuracy after hyperparameter tuning and feature engineering.
2. **Overfitting Reduction**: The Decision Tree model's train accuracy dropped from 1.0000 to 0.9163, indicating a reduction in overfitting.
3. **Comprehensive Metrics**: Precision, recall, F1-score, and ROC-AUC provided a more comprehensive evaluation, revealing that some models (e.g., SVM) had high accuracy but lower recall and F1-scores, indicating potential issues with false negatives.

## Conclusion

### Feature Engineering and Exploration:

1. Interaction Terms: Including interaction terms (e.g., age_campaign) can capture more complex relationships in the data.
2. Additional Features: While the current dataset lacks a gender feature, adding relevant demographic features could provide more insights. Always ensure these features are included ethically and do not introduce bias.

### Hyperparameter Tuning:

1. Grid Search and Randomized Search: Both methods are effective, but can be computationally expensive. Consider using Bayesian Optimization for more efficient hyperparameter tuning.
2. Specific Hyperparameters: Further exploration of hyperparameters such as max_depth and min_samples_split for Decision Tree, and C and gamma for SVM, could yield better results.
Comprehensive Metrics:
3. Balanced Metrics: Precision, recall, F1-score, and ROC-AUC should be considered alongside accuracy to ensure the model performs well across different aspects of prediction.
4. Addressing Class Imbalance: Techniques such as SMOTE (Synthetic Minority Over-sampling Technique) or class weighting can help improve recall in imbalanced datasets.

### Recommendations

1. **More Feature Engineering**: Explore additional features and interaction terms. For example, including demographic features like gender could provide more insights if available.
2. **Hyperparameter Tuning**: Further tune hyperparameters using more advanced techniques such as Bayesian Optimization.
3. **Model Ensembling**: Combine models (e.g., through voting or stacking) to leverage the strengths of multiple classifiers.






