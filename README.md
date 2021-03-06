
# Fraud Detection: One Month of European Credit Card Transactions

[**Dataset**](https://www.kaggle.com/mlg-ulb/creditcardfraud)

The dataset contains transactions made by credit cards in September 2013 by European cardholders.

All the transactions occurred in two days, where we have 492 frauds out of 284,807 transactions. The dataset is highly unbalanced; the positive class (frauds) account for 0.173% of all transactions.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://drive.google.com/file/d/1l3VpRPtDTGvTXDbDImZ2nJR9SM_DH2IB/view?usp=sharing)

## Overview

Anomaly detection (or outlier detection) is the identification of rare items, events or observations which raise suspicions by differing significantly from the majority of the data. Typically, anomalous data can be connected to some kind of problem or rare event such as bank fraud, medical problems, structural defects, malfunctioning equipment etc. This connection makes it very interesting to be able to pick out which data points can be considered anomalies, as identifying these events are typically very interesting from a business perspective.

----

## Key Features

Most of the features are converted with PCA for confidentiality. The exceptions are **time** (seconds elapsed between transactions), **amount** (€), and **fraud** (0 or 1). 

![image](https://storage.googleapis.com/credit_card_fraud247/time-amount.png)
![image](https://storage.googleapis.com/credit_card_fraud247/class-distribution.png)

|Seconds	|Fraud	|Time|
|---------------|-------|----|
|68207.0	|6|	18 hours, 56 minutes and 47 seconds|
|93879.0	|4|	1 day, 2 hours and 4 minutes|
|84204.0	|4|	23 hours, 23 minutes and 24 seconds|

- Notes:
	* Time and amount are evenly dispersed.
	* This is a hostile environment. Fraud is very much outnumbered here, so a misclassification of the majority class will result in a high amount of alerts.
	* There is no one time record that has a high number of fraud.

----

## Integrations

* [ImbLearn](https://imbalanced-learn.org/stable/generated/imblearn.combine.SMOTETomek.html)
* [LightGBM](https://lightgbm.readthedocs.io/en/latest/)
* [Isolation Forests](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.IsolationForest.html)
* [Catboost](https://catboost.ai/)
* [PYOD](https://pyod.readthedocs.io/en/latest/)
* [Optuna](https://github.com/optuna/optuna)
* [TensorFlow](https://www.tensorflow.org/tutorials/generative/autoencoder)
* [XGBoost](https://xgboost.readthedocs.io/en/latest/index.html)

----

## Conclusions

![image](https://storage.googleapis.com/credit_card_fraud247/conclusion.png)

The anamoly detection algorithms are sensitive to alert spam, ie, they will need to contact each customer who has experienced fraud. 

Because of the downsides of false alerts, we can say that **precision is more important than recall** (i.e., we need to reduce the number of false positives versus getting the highest number of true positives). It looks like CatBoost is going to be the best algorithm for a high recall without much of a tradeoff in precision. Precision measures how well our algorithm identifies only anomalies.

Since this is not an unsupervised algorithm, it will only work on labeled data, which means novelty fraud will go undetected. 

From the unsupervised learners, a histogram-based outlier approach may work, or the tensorflow model may also be run to detect new forms of fraud. As for alerting customers, the unsupervised learners are not as reliable as the supervised classifiers.


----

## Questions/Comments

Any contributions are more than welcome!

Feel free to leave me a message on Git or email me at mcclure.dean@gmail.com
