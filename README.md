
# Data Science Salary Estimator: Project Overview
- Created a tool that estimates data science salaries (MAE ~ $ 11K) to help data scientists negotiate their income when they get a job.
- Engineered features from the text of each job description to quantify the value companies put on python, excel, aws, and spark.
- Optimized Linear, Lasso, and Random Forest Regressors using GridsearchCV to reach the best model.

## Contains
1. [Environment Variables](#Environment-Variables)
2. [Data Cleaning](#Data-Cleaning)
3. [EDA](#EDA)
4. [Model Building](#Model-Building)
5. [Model performance](#Model-performance)

## Environment Variables

To run this project, you will need to add the following environment variables to your .env file. Refer `requirements.txt` in the repo.
```python
pip install -r requirements.txt
```
`pandas`
`numpy`
`matplotlib`
`seaborn`
`sklearn` 

## Data Cleaning
After scraping the data, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:
- Parsed numeric data out of salary
- Made columns for employer provided salary and hourly wages
- Removed rows without salary
- Parsed rating out of company text
- Made a new column for company state
- Added a column for if the job was at the company’s headquarters
- Transformed founded date into age of company
- Made columns for if different skills were listed in the job description:
    - Python
    - R
    - Excel
    - AWS
    - Spark

## EDA
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables also an Heat Map.

![avg_salary.png](https://github.com/gagandeepsingh04/data-scientist-salary-analysis/blob/main/avg_salary.png)

![heat_map.png](https://github.com/gagandeepsingh04/data-scientist-salary-analysis/blob/main/heat_map.png)

## Model Building
First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.

I tried three different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.

I tried three different models:

- Multiple Linear Regression – Baseline for the model
- Lasso Regression – Because of the sparse data from the many categorical variables, I thought a normalized regression like lasso would be effective.
- Random Forest – Again, with the sparsity associated with the data, I thought that this would be a good fit.


## Model performance
The Random Forest model far outperformed the other approaches on the test and validation sets.

- Random Forest : MAE = 11.22
- Linear Regression: MAE = 18.86
- Ridge Regression: MAE = 19.67
