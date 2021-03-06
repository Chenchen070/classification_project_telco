# classification_project_telco

## Project Goals

My goal is to identify key drivers of churn, which group of customers are more likely to churn. Then make recommendations for changes so that we can reduce the monthly churn rate and increase customer retention.

## Project Description

* How to reduce the customer churn rate is pretty much every single company's all-year-round mission. What kind of marketing strategies the company need to use. What is the main group the company need to focus on base on their products. What kind of services the company can offer to retain the current customers and attract more new customers. 
* In this report, we will analyze the attributes of customers who were more or less likely to churn, develop a model for predicting churn rate based on those attributes, and leave with both recommendations for Telco company and predictions of churn rate for a list of customers (delivered via csv). 

## Initial Questions

1. Is the churn rate effected by monthly charges?

2. Does churn rate related to tenure?

3. Does the churn rate related to the additional services?

4. Does the churn rate effeted by contract type?



## Data Dictionary

Variables are used in this analysis: 

* churn
* monthly charges
* tenure
* contract types: month-to-month, one-year, two-year
* additional services: online security, online backup, tech support, streaming tv, streaming movies


## Steps to Reproduce

1. You will need an env.py file that contains the hostname, username and password of the mySQL database that contains the telco_churn table. Store that env file locally in the repository.
2. Clone my repo (including the acquire_telco.py and prepare_telco.py) (confirm .gitignore is hiding your env.py file)
3. Libraries used are pandas, matplotlib, seaborn, numpy, sklearn.
4. You should be able to run telco_churn_report.

## Plan

### Wrangle

Modules (acquire.py + prepare.py)

1. Test acquire function
2. Add to acquire.py module
3. Write code to clean data in notebook
4. Merge code into a single function & test
5. Write code to split data in notebook
6. Merge code into a single function & test
7. Merge functions in a single function & test
8. Add all 3 functions (or more) to prepare.py file
9. Import into notebook and test functions

### Missing Values (report.ipynb)

There are 11 missing value for total charge. Since 11 rows is a very small portion of the whole data set, so I just dropped it.

### Data Split (prepare.py (def function), report.ipynb (run function))

* train = 56%
* validate = 24%
* test = 20%

### Using your modules (report.ipynb)

once acquire.py and prepare.py are created and tested, import into final report notebook to be ready for use.

### Set the Data Context

1. Overall churn rate
* run train.shape to show the data rows and columns inforamtion (4500,55)
* run train.churn.value_counts() to show the number for churn
* plot a hist chart, x is churn, y is churn count

2. churn rate by service type
* run pd.crosstab to show the percentage of each service type
* plot a hist chart, x is service type, y is churn count

3. churn rate by contract type
* run pd.crosstab to show the percentage of each contract type
* plot a hist chart, x is contract type, y is churn count

### Explore

1. Is the churn rate effected by monthly charges?
2. Does churn rate related to tenure?
3. Does the churn rate related to the additional services?
4. Does the churn rate effeted by contract type?

### Exploring through visualizations (report.ipynb)

1. Is the churn rate effected by monthly charges?
* what is the mean for chun and non-churn customers? plot a boxplot to show the differece between each group, x is churn, y is monthly charges
* what is the distribution looks like? plot a kdeplot to visualize change of churn with monthly charges, x is monthly charge, y is density.
* run a t-test (2 samples 1-tailed) on monthly charge and churn

2. Does churn rate related to tenure?
* what is the mean difference of tenure between churn and non-churn? plot a boxplot for tenure and churn, x is churn, y is tenure.
* use groupby to see the mean of churn and non-churn
* run a t-test (2 samples 1-tailed) on tenure and churn

3. Does the churn rate related to the additional services?
* what is the churn difference between additional service numbers? plot a countplot, x is addtional service number use, y is churn count.

4. Does the churn rate effeted by contract type?
* crosstab contract type and churn
* what is the difference between different contrat types? plot a countplot, x is contract type, y is churn count.

### Summary (report.ipynb)

1. Customers who have high monthly charges are more like to churn.
2. The churn customers have less tenure.
3. The more additional services use, the churn rate is lower.
4. Month-to-month contract type has higher churn rate.

Therefore, features I will use are: 
* monthly charges
* tenure
* addtional services
* contracts type

## Modeling

### Select Evaluation Metric (Report.ipynb)
Because churn is a boolean/yes or no value, I will use classification machine learning algorithms to fit to the training data and evaluate on validate set.

Then I will pick the best model using accuracy as the metric because it's very easy to understand.

### Evaluate Baseline (Report.ipynb)
The baseline I set for train set is the mode of churn (churn = 0).

### Develop 3 Models (Report.ipynb)
* Decision tree
* KNN
* Logistic regression

### Evaluate on Train (Report.ipynb)

### Evaluate on Validate (Report.ipynb)

### Evaluate Top Model on Test (Report.ipynb)
The top model is logistic regression.


## Report (Final Notebook)

### Code commenting (Report.ipynb)

### Written Conclusion Summary (Report.ipynb)
From the model test result, we can see the best accuracy on the test set is achieved by the logistic regression with 79.67%. The features I use for this model are: monthly charges, tenure, contract type and additional services.

### conclusion recommendations (Report.ipynb)
1. Better price for long-term contract or have more different types of contracts.
2. Offer more popular and useful addtional services for the customers.
3. Get better deal from different providers to make the company more competitive.

### conclusion next steps (Report.ipynb)
1. In my first round of exploration, I found out that six features could effect the churn rate. But after the modeling part, I found two of them actually don't have positive influence with my models so I took those two off. I would like to explore more features and use different combination to improve my result.
2. In this report, I only use the accuracy as the compare score for different models and the best perform test accuracy is 79.67%. I would like to dig more deeper into the modeling part, use different metric, different algorithm to improve the overall performence.
3. Since I already know that price is one of the important attributes for the churn rate. But the price columns I have here are only monthly charges and total charges. I would like to have more detail price for different categories so I can get a better prediction on the churn rate.

### no errors (Report.ipynb)

## Live Presentation

### Intro (live)

### audience & setting (live)
Target audience for is my direct manager and Telco manager.

### content (live)

### Verbal Conclusion (findings, next steps, recommendations) (live)

### time (live)
5 minutes.

## Deliver Predictions
Deliver predictions with telco_churn_prediction.csv.
