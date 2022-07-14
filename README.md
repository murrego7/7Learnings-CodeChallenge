# 7LearningsCodeChallenge
Solution to 7Learnings Data Science Challenge

## Set up

- Pre-requirements: In order to run the challenge solution you will need to be able to use BigQuery in Jupyter Notebook.

After cloning the repository you will need to load a list of requirements.

```
pip install -r requirements.txt

```
Then you will need to load the IPython Magics for Bigquery

```
%load_ext google.cloud.bigquery
```

# Welcome to challenge's solution!

Hi! In this challenge I aim to solve the following question:

**Will it snow tomorrow 13 years ago?**

In order to answer this question, I will be using the GSOD public dataset, which contains different variables related with weather. This is a time series dataset and the the target variable in this case is a boolean categorial variable. 

For this I will be using 2 models, with 3 different scenarios:

1. Logistic Regression.

2. Logistic Regression - Hyperparameter optimization with GridSearch

3. XGBoost - Hyperparameter optimization with GridSearch

I start querying the data through Big Query and then the query is converted into a dataframe in order to manipulate and preprocessing the data with Pandas. Nonetheless converting to dataframe requires more computational time.

#Points to have in mind:

## Train, test, evaluation split
I create two different functions for achieving the split:

1. Split the date in train, test AND evaluation. 

*Note*: After evaluating the models, I was not having the best accuracy with this strategy. So I decided to make a traditional train-test split.

2. Split the date in train and test.

> Both functions split under the condition: *testset should begin with "str(dt.datetime.today()- dt.timedelta(days=13*365)).split(' ')[0]" row.*


## Normalization: 
> It is a good practice to normalize features when these are in different scales. Nonetheless, after evaluating the models, I get to the conclusion that this is not necessary in this case.

# Modeling and evaluation
I will predict whether will snow tomorrow 13 years ago using two different models Logistic Regression and Random Forest, but also I will apply a Grid Search to the Logistic model. 

> *Metric for evaluation*: Since this is a binary **classification** problem, I will choose the ROC score.

# Conclusions:
 - All of the models used predict that during our target date WON'T SNOW.
 
 - In this case, the best model was a Logistic Regression (1) without hyperparameter optimization. Having in mind the trade-off: computational resourses vs accuracy.
 
 - Tomorrow 13 years ago WON'T snow, which makes sense, having in mind we are in july at the moment I solve the challenge :) 


## Thing to improve: 
- The code can be more "parametric", in order to deploy the process with other related data sets or with this dataset if changes in the future. 
- Find a way to avoid all of the "trash info" that is deployed when we train the model.






