# Data Science Salary Estimator: Project Overview 
* Created a model that estimates data science salaries (MAE ~ $12.0K) to help data scientists negotiate their income when they get a job
* Cleaned over 1000 rows of data, and engineered features from the text of each job description to quantify the value companies put on various skills (python, R, SQL, tableau, spark, aws and excel) and education requirements (bachelor's, master's or PhD)
* Optimized Linear, Lasso, Elastic Net, Kernel Ridge, SVR, Gradient Boosting, XGB and Random Forest Regressors using GridsearchCV to reach the best model (MAE ~ $10.2K)
* Created a hybrid model using 4 different models to make the final predictive model (MAE ~ $12.0K) more robust to overfitting than any single baseline model

## Code and Resources Used 
**Python Version:** 3.7  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn  
**Ken Jee's Project:** This project is based off of Ken Jee's project, with my own various modifications to feature engineering and model building. Here is the link to his github repo: https://github.com/PlayingNumbers/ds_salary_proj  
**Dataset**: The original dataset glassdoor_jobs.csv was scraped by Ken Jee. Glassdoor scraper code can be found in his github repo listed in previous bullet point  


## Data Cleaning
For each job, we have the following variables:
*	Job title
*	Salary Estimate
*	Job Description
*	Rating
*	Company 
*	Location
*	Company Headquarters 
*	Company Size
*	Company Founded Date
*	Type of Ownership 
*	Industry
*	Sector
*	Revenue
*	Competitors 


I made the following changes and created the following variables:
*	Parsed numeric data out of salary 
*	Made columns for employer provided salary and hourly wages 
*	Removed rows without salary 
*	Parsed rating out of company text 
*	Made a new column for company state 
*	Added a column for if the job was at the company’s headquarters 
*	Transformed founded date into age of company 
*	Made columns for if different skills were listed in the job description:
    * Python  
    * R  
    * SQL
    * Tableau
    * Spark 
    * AWS  
    * Excel 
*	Made columns for if different degrees were listed in the job description:
    * Bachelor's / B.S.
    * Master's / M.S.
    * PhD
*	Column for simplified job title and Seniority 
*	Column for description length 

## EDA
I looked at the distributions of the data and the value counts for the various categorical variables.

## Model Building 

First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.   

I tried eight different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in this type of model.   

I then used a mixture of the eight different models to arrive at a robust model with a decently low MAE.


## Model performance
**Baseline Models**: The XGB performed the best
*	**Linear Regression**: MAE = 18.7
* **Lasso Regression**: MAE = 18.66
* **Elastic Net Regression**: MAE = 18.05
* **Kernel Ridge Regression**: MAE = 18.16
* **Support Vector Regression**: MAE = 28.95
* **Gradient Boosting**: MAE = 11.75
* **Extreme Gradient Boosting**: MAE = 10.19
* **Random Forest Regression**: MAE = 12.70

**Hybrid Models**: The second hybrid model performed the best
* **Mixture of linear, lasso, elastic net, kernel ridge, gradient boosting, extreme gradient boosting, random forest**: MAE = 13.07
* **Mixture of linear, elastic net, extreme gradient boosting, random forest**: MAE = 12.03




 
