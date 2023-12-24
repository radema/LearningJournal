---
tags:
  - ml
  - mathematics
  - DataScience
source: Alberto Danese's newsletter
date: 29/09/2023
authors: Alberto Danese
---

# Introduction

One of the most important challenges in machine learning is ensuring that models generalize well to new data.
[[Data drift]], or the change in the underlying distribution of data over time, is a major cause of model overfitting and underperformance in production.
Traditional approaches to evaluating model robustness to data drift can be difficult and time-consuming to implement.
## Adversarial validation

The basic idea is to train a classifier to distinguish between training and test data.
If the classifier can do this with an AUC greater than 0.5, then there is evidence that the training and test data are not statistically indistinguishable.
### Benefits

* Easy to implement 
* It can be used with any type of data, including mixed data types, missing values, and outliers.
* Effective at detecting a wide range of data drift issues, including:
	* [[data leakage]] from the training data to the test data
	* Differences in the distribution of features between the training and test data
	* Changes in the underlying distribution of the target variable
### Conclusion

Adversarial validation is a valuable tool for ensuring that machine learning models generalize well to new data.
It is a simple, effective, and under-appreciated technique that should be considered by any data scientist who is working on a machine learning project.
Additional topics for dedicated notes: