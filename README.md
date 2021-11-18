
# Predicting Ames Housing Prices Using Linear Regression  

**Author: Faisal Kalema**  

**Checkout [The Magic of LASSO Regression Model](https://medium.com/swlh/the-magic-of-lasso-regression-model-3a79328013f0) on medium**  

## Contents:  

Problem Statement  
Data Dictionary  
Executive Summary  
Results Table  
Further Steps  


### Problem Statement
The goal of this project is to build a model that is capable of predicting housing prices given training data.

### Data Dictionary
The full data dictionary of the original Ames dataset can be found [here](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt).

### Executive summary
This project was part of a Kaggle competition that involved general Assembly students from across the United States. The project's objective was to predict home prices in Ames, Iowa. The dataset included 2051 observations and 80 features, each of which contained 79 explanatory variables that described the quality and quantity of numerous physical attributes of the property, as well as a response variable. The majority of the variables correspond to the types of information that a normal house buyer would like to know about a potential property, such as lot size, building type, property condition, and kitchen quality. The characteristics included a variety of data types, including continuous variables such as lot and living area measures, discrete variables such as the number of beds and bathrooms, and several categorical factors such as street (gravel or paved).

I began by conducting exploratory data analysis to develop intuition about the data, conducting sanity checks to ensure that the insights I'm drawing are from the correct dataset, checking for missing values, determining the presence of outliers, and summarizing the data. Fortunately, all variables were of the correct data type; nevertheless, several values were missing. I removed features with missing values in excess of 10% of the data. Some of these features include the lot frontage, the fence, the alley, and the garage year built. Then, I imputed missing values for numerical characteristics by substituting the mean of the relative features for them and N/A for categorical features by substituting zero for N/A. The data cleaning code can be found [here](https://github.com/Kalz123/Ames_housing_prices/blob/master/datasets/01.%20EDA%20and%20Cleaning.ipynb)

Following EDA, I concatenated the training and testing sets to ensure that changes made during feature engineering are consistent throughout the training and testing sets. I used a log transformation on numeric features with an asymmetrical scale, such as the Ground living area and Total rooms above ground. I visualized the variation in categorical data using boxplots and converted categorical variables with a greater variation into dummies (one-hot encoded). Finally, I performed feature interactions on several features in order to improve their impact on the response variable (price) and so optimize model performance. The feature engineering code is available [here](https://github.com/Kalz123/Ames_housing_prices/blob/master/datasets/02.%20Preprocessing%20and%20Feature%20Engineering.ipynb) 

Later, because the true relationship between the response variable and the explanatory variables was essentially linear, I trained a linear regression. On the training and testing sets, the model achieved an accuracy of 89 and 71%, respectively, with a root mean squared error (RMSE) of 289,496,2.222. Due to the low bias and high variance in this model, I used Lasso regression to minimize the features without significantly raising the bias, hence improving the model's performance. After performing lasso regression, the model achieved an accuracy of 88 and 73% on the training and testing sets, respectively, with a root mean square error of 40,869,658. I took the log of the response variable to improve the model's performance, and the RMSE was lowered to 24,119.96. Even though the model produced fairly decent results, I would consider experimenting with different models and comparing the outcomes. The code for model tuning is available [here](https://github.com/Kalz123/Ames_housing_prices/blob/master/datasets/03.%20Model%20Benchmarks.ipynb) and [here](https://github.com/Kalz123/Ames_housing_prices/blob/master/datasets/04.%20Model%20tuning.ipynb). 

### Results table

|  | Training (%)| Testing (%)| RMSE |
|---|---|---|---|
|  Linear regression|89  |71  |2,894,962  |
|  Lasso regression|  88|  73|40,870  |
|  Lasso regression(log transformation)|  _ |  _ |24,119|

### Further Steps
Moving foward, I'll build other models and compare the results of the different model performances.