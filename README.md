# Churn-Prediction-at-Ola
Utilized Bagging and Boosting techniques to identify at-risk drivers, enabling Ola to enhance retention strategies and lower recruitment costs 

# Project Title:
Churn Prediction for Ola Drivers: Reducing Attrition through Data-Driven Insights

# Problem Statement:
Ola faces a significant challenge with high driver churn, which negatively impacts business costs and morale. Recruiting new drivers is expensive, and retaining existing ones is more cost-effective. This project aims to predict driver attrition using demographic, tenure, and performance data to reduce churn and support retention strategies.

# Potential Impact:
By identifying drivers at risk of leaving, this project provides insights that can help Ola improve retention strategies, lower recruitment costs, and enhance operational stability. It supports targeted interventions for at-risk drivers, ultimately reducing churn and improving overall business efficiency.

# Approach: 
## 1. Initial Dataset Overview:
- The dataset had 14 features, one of which was a unique identifier for each driver (driver_id). This feature was deleted as irrelevant for prediction.
- The dataset consisted of 19,204 rows and 14 columns.
- Features like "Age" and "Gender" had missing values (61 and 52, respectively), while "Last working date" had 17,408 missing values.
- KNN Imputation was performed to fill in missing values for numerical features.
  
## 2. Data Grouping and Aggregation:
- Since the dataset had multiple rows for each driver, the data was grouped by driver_id.
- Aggregation functions were applied on other features and merged to create a unique dataset for each driver.
  
## 3. New Feature Creation:
- A new target feature was derived from the Last working date. If Last working date was null, it indicated a driver had churned (labeled as 1); otherwise, they had not churned (labeled as 0).
- Two additional features were created to track:
- Whether a driver’s quarterly rating increased from the first to the last reporting date.
- Whether a driver’s income increased across the same period.
  
## 4. Final Dataset:
- Features with a data type of datetime were deleted.
- The final dataset had 2,381 rows and 13 features, including the target variable.
- The feature City was the only object-type feature.
- Driver_id was removed from the final dataset as it was irrelevant for the prediction task.
  
## 5.Univariate Analysis:
- The feature Driver_id exhibited a uniform distribution, which was expected since it uniquely identifies each driver.
- Both Age and Gender showed skewed distributions, indicating an uneven representation of age groups and genders in the dataset.
- A majority of the drivers belonged to C20 city, highlighting its significant presence in the dataset.
  
## 6. Bivariate Analysis:
- The proportion of churn and non-churn drivers remained the same across Gender and Education, suggesting that these features do not have a notable influence - on churn behavior.
- Drivers with a last quarterly rating of 3 or 4 were found to be less likely to leave the company, indicating that higher ratings correlate with retention.
- Drivers whose quarterly ratings increased over time were also less likely to churn, suggesting performance improvement is a key factor in retaining drivers.

## 7. Feature Engineering:
- The categorical City feature was transformed using target encoding to enhance its predictive power.
- The data was then split into training and test sets.
- Both training and test data were standardized using parameters from the training data to ensure consistency during model training and evaluation.
  
## 8. Modeling Approach:
- Multiple models were trained using Bagging with SMOTE and Gradient Boosting with SMOTE.
- After hyperparameter tuning for Random Forest using RandomizedSearchCV (best_parameters : max_Depth = 5, max_leaf_nodes = 20, n_estimators = 150)
- Precision: 85%
- Recall: 90%
- F1 Score: 87%
- ROC_auc: 0.81
- PRcurve_auc: 0.89
  
### After hyperparameter tuning for Gradient Boosting with SMOTE using RandomizedSearchCV (best_parameters : max_Depth = 20, max_leaf_nodes = 80, n_estimators = 150)
- Precision: 85%
- Recall: 90%
- F1 Score: 87%
- ROC_auc: 0.81
- PRcurve_auc: 0.89
  
### After hyperparameter tuning for XG Boosting with SMOTE using RandomizedSearchCV (best_parameters : max_Depth = 7, max_leaf_nodes = 40, n_estimators = 2000)
- Precision: 85%
- Recall: 90%
- F1 Score: 87%
- ROC_auc: 0.81
- PRcurve_auc: 0.89
  
## 9. Important Features:
- Significant features identified through feature importance include:
- For Random Forest:
- Last quarterly rating, 
- total business value.
- Income,
- Quarterlyrating_Increased, and so on
 ![new_image](https://github.com/SachinChauhan0911/Churn-Prediction-at-Ola/blob/main/images/Important%20Features%20coming%20from%20Random%20Forest.png)
  
### For Gradient Boosting:
- Last quarterly rating, 
- total business value.
- Age
- Income, and so on
- Quarterlyrating_Increased, and so on
  ![new_image2](https://github.com/SachinChauhan0911/Churn-Prediction-at-Ola/blob/main/images/Screenshot%202024-10-21%20at%204.33.25%20AM.png)
  
### For XG Boosting:
- Last quarterly rating,
- joining_Designation.
- Income_inc
- Quarterlyrating_Increased, and so on




