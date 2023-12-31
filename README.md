# Credit-Card-Fraud-Detection---Predictive-Model
(data was taken from [kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud))

## Introduction
The datasets contains transactions made by credit cards in **September 2013** by european cardholders. This dataset presents transactions that occurred in two days, where we have **492 frauds** out of **284,807 transactions**. The dataset is **highly unbalanced**, the **positive class (frauds)** account for **0.172%** of all transactions.

It contains only numerical input variables which are the result of a **PCA transformation**.

Due to confidentiality issues, there are not provided the original features and more background information about the data.

Features **V1, V2, ... V28** are the **principal components** obtained with **PCA**;
The only features which have not been transformed with PCA are **Time and Amount**. Feature Time contains the seconds elapsed between each transaction and the first transaction in the dataset. The feature Amount is the transaction Amount, this feature can be used for example-dependant cost-senstive learning.
Feature Class is the response variable and it takes value 1 in case of fraud and 0 otherwise.

## Conclusions
We investigated the data, checking for data unbalancing, visualizing the features and understanding the relationship between different features. We then investigated two predictive models. The data was split in 3 parts, a train set, a validation set and a test set. For the first three models, we only used the train and test set.

We started with **RandomForrestClassifier**, for which we obtained an AUC scode of **0.85** when predicting the target for the test set.

We followed with an **AdaBoostClassifier model**, with lower AUC score (**0.83**) for prediction of the test set target values.

We then followed with an **CatBoostClassifier**, with the AUC score after training 500 iterations **0.86**.

We then experimented with a **XGBoost** model. In this case, se used the validation set for validation of the training model. The best validation score obtained was **0.984**. Then we used the model with the best training step, to predict target value from the test data; the AUC score obtained was **0.974**.

We then presented the data to a **LightGBM** model. We used both train-validation split and cross-validation to evaluate the model effectiveness to predict 'Class' value, i.e. detecting if a transaction was fraudulent. With the first method we obtained values of AUC for the validation set around **0.974**. For the test set, the score obtained was **0.946**.
With the cross-validation, we obtained an AUC score for the test prediction of **0.93**.

## References
- Credit Card Fraud Detection Database, Anonymized credit card transactions labeled as fraudulent or genuine, [kaggle](https://www.kaggle.com/mlg-ulb/creditcardfraud).
- Principal Component Analysis, [Wikipedia Page](https://en.wikipedia.org/wiki/Principal_component_analysis)
