# House_Price_Prediction-Advance_Regression
Dataset: https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data

## Objective:
To predict sale price of house based on house description.

## Metric
Submissions are evaluated on Root-Mean-Squared-Error (RMSE) between the logarithm of the predicted value and the logarithm of the observed sales price. 

## Breakdown of project:
    1. Exploratory Data Analysis
    2. Data preparation and Cleaning
    3. Data Transformation
    4. Feature engineering
    5. Advanced regression models
    6. Stacking and ensembling models
    
## 1. EDA 
    - There are few fetures which has missing value in test set but not in training set.
    - Test set features have few extra category of value which is not present in training set.
    - There are few features which are highly correlated like "GarageCars" and "GarageArea" & "GarageYrBlt" and "YearBuilt". I will not be droping highly correlated featues as the number of features is reasonable.
    - There are few outliers which need to be taken care.
    
## 2. Data preparation and Cleaning
    - Cocatinating training and testing data to handle missing categories of data from training set.
    - Correcting data type of column. 
    - Handling missing values of categorical and numeric features separately. Replacing nan value of categorical feature with mode or "None" based on what "NA" represent in the feature.
    - Fitting model on numeric feature to predict missing values and replacing missing value with predicted values. 
   
## 3. Feature Engineering
    Created 4 new features to enhance ML model and to reduce RMSE score. 
    
## 4. Feature Transformation
    - It is observed that there are many features which has skewed data distribution. I have performed log transformation to transform skewed distributed data into normal form. 
    - Perfored cyclic transformation on "MoSold".
    - Encoding categorical features.
    - Log transforming target variable.
 
## 5. Modeling
    - Selecting top 5 models from compare_model function result.
    - Tuning and fine tuning all the models
    - Gradient Boosting found working best of all other model. **(RMSE score : 0.12339)**
    
## 6. Stacking and ensembling models
    Top 4 models are stacked together to perform final prediction. 
    ---------------------------------------------------------------
    final_predictions = (
    0.3 * np.exp(models['catboost'].predict(test_final)) +
    0.05 * np.exp(models['lightgbm'].predict(test_final)) +
    0.2 * np.exp(models['bayes_ridge'].predict(test_final)) +
    0.45 * np.exp(models['gb'].predict(test_final))
)
</br>
</br>
## Minimum RMSE score achived is 0.12095 which is under top 5%
  
  # Thank you :)
