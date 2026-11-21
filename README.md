# Concrete Compressive Strength Prediction Using Machine Learning

## 1. Problem Statement and Project Objective

The objective of this project is to develop a machine learning regression model to predict the compressive strength of concrete based on its ingredients and curing age.

Concrete compressive strength is an important property used to evaluate the quality and durability of concrete. Predicting strength based on the quantities of different ingredients can help in understanding concrete performance and supporting construction material planning.

The project involves performing complete data analysis, building multiple regression models, comparing their performance, selecting the best-performing model, and predicting concrete strength for new input data.

## 2. Dataset Description

The dataset contains 1,030 observations and 9 columns, consisting of 8 quantitative input features and 1 quantitative target variable.

**Input Features:**
1. Cement
2. Blast Furnace Slag
3. Fly Ash
4. Water
5. Superplasticizer
6. Coarse Aggregate
7. Fine Aggregate
8. Age

**Target Variable:**
- Concrete Compressive Strength (MPa)

The target variable represents the compressive strength of concrete measured in Megapascals (MPa).

## 3. Data Understanding and Data Cleaning

Performed initial data inspection using:
- Dataset shape and column information
- Data types
- Statistical summary using `describe()`
- Missing value analysis
- Duplicate record analysis

The dataset contained no missing values. A total of 25 duplicate records were identified and removed, leaving 1,005 observations for further analysis.

## 4. Exploratory Data Analysis (EDA)

Performed univariate and bivariate analysis to understand the distribution of features and their relationships with concrete compressive strength.

The following techniques were used:
- Histograms to understand feature distributions.
- Boxplots to identify potential outliers.
- IQR method for statistical outlier detection.
- Scatter plots to examine relationships between individual features and concrete strength.
- Correlation matrix and heatmap to understand relationships among variables.

**Key Observations:**
- Cement showed a positive relationship with concrete compressive strength.
- Age also showed a positive relationship with strength.
- Water showed a negative correlation with strength.
- Slag, fly ash and superplasticizer contained several zero values, which were treated as valid ingredient quantities rather than missing values.
- Potential outliers were identified and retained because they could represent valid concrete measurements.

## 5. Data Preprocessing

The dataset was divided into independent variables (X) and the target variable (y).

The input features were separated from the concrete strength target variable. Training and testing datasets were created for model development and evaluation.

StandardScaler was applied to the features for algorithms sensitive to feature scaling, particularly KNN and Support Vector Regression. The scaler was fitted on training data and then applied to testing data to avoid data leakage.

## 6. Model Building

Seven regression algorithms were implemented to predict concrete compressive strength:

1. Linear Regression
2. Decision Tree Regressor
3. Random Forest Regressor
4. K-Nearest Neighbors (KNN) Regressor
5. Support Vector Regression (SVR)
6. Gradient Boosting Regressor
7. XGBoost Regressor

Each model was trained using the training dataset and evaluated using the testing dataset.

## 7. Model Evaluation and Comparison Report

The models were compared using four regression evaluation metrics:

- **MAE (Mean Absolute Error):** Measures the average absolute difference between actual and predicted values.
- **MSE (Mean Squared Error):** Measures the average squared prediction error.
- **RMSE (Root Mean Squared Error):** Measures prediction error in the target variable's unit (MPa).
- **R² Score:** Measures how much variation in concrete strength is explained by the model.

**Initial Model Comparison Results:**

| Model | MAE | RMSE | R² Score |
|---|---:|---:|---:|
| Linear Regression | 8.8953 | 11.1913 | 0.5802 |
| Decision Tree | 3.7755 | 5.9238 | 0.8824 |
| Random Forest | 3.4979 | 5.2552 | 0.9074 |
| KNN | 7.1253 | 9.1923 | 0.7168 |
| SVR | 8.3443 | 10.9229 | 0.6001 |
| Gradient Boosting | 4.1289 | 5.6039 | 0.8947 |
| XGBoost | 4.1387 | 5.6126 | 0.8944 |

Based on the comparison, Random Forest Regressor achieved the highest initial R² Score of approximately 90.74%, along with the lowest MAE, MSE and RMSE among the evaluated models.

Therefore, Random Forest was selected for further optimization.

## 8. Hyperparameter Tuning

Random Forest Regressor was optimized using GridSearchCV with 5-fold cross-validation.

The following hyperparameters were explored:
- Number of estimators
- Maximum tree depth
- Minimum samples required to split a node
- Minimum samples required at a leaf node

The best estimator obtained through GridSearchCV was evaluated again using the testing dataset.

**Performance After Tuning:**

- MAE: 3.5329
- MSE: 27.0751
- RMSE: 5.2034
- R² Score: 0.9092 (approximately 90.92%)

The tuned model showed a small improvement in R² Score and RMSE compared with the initial Random Forest model, although MAE increased slightly.

## 9. Model Saving and Prediction on New Data

The tuned Random Forest model was saved using Python's Pickle module so that it could be reused without retraining.

The saved model was loaded and tested using a new concrete sample containing ingredient quantities and curing age.

The model generated a predicted concrete compressive strength value in MPa, demonstrating its ability to make predictions on new input data.

## 10. Challenges Faced and Solutions

**1. Duplicate Records:** Identified and removed 25 duplicate observations.

**2. Missing Values:** Checked all columns and confirmed that no missing values were present.

**3. Outliers:** Used boxplots and the IQR method to identify potential outliers. Retained them because they could represent genuine concrete measurements.

**4. Feature Scaling:** Applied StandardScaler for KNN and SVR to ensure that differences in feature magnitudes did not disproportionately affect predictions.

**5. Model Selection:** Implemented and compared seven regression algorithms using multiple evaluation metrics.

**6. Model Optimization:** Applied GridSearchCV with 5-fold cross-validation to optimize Random Forest hyperparameters.

**7. Model Reusability:** Used Pickle to save and reload the trained model for future predictions.

## 11. Final Project Conclusion

The Concrete Compressive Strength Prediction project successfully demonstrated the application of machine learning regression algorithms to predict concrete strength using its ingredient quantities and curing age.

Complete exploratory data analysis, data cleaning, outlier analysis, correlation analysis, model development and evaluation were performed.

Seven regression algorithms were implemented and compared. Among them, Random Forest Regressor achieved the best initial performance with an R² Score of approximately 90.74%.

After hyperparameter tuning using GridSearchCV, the tuned Random Forest model achieved an R² Score of approximately 90.92% and an RMSE of approximately 5.20 MPa.

The tuned Random Forest Regressor was selected as the final best-performing model among the evaluated algorithms. It was saved using Pickle and successfully used to generate predictions for new concrete samples.

This project demonstrates how machine learning can support concrete strength estimation and provide useful insights into the relationship between concrete ingredients, curing age and compressive strength.
