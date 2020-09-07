## Telecom Churn Modeling (Comparision and analysis of models for Imbalanced data)
This project aims to understand how imbanced data imapcts performance of classification models.

In this Telecom churn data set the classes exhibit high imbalance with churned to non churned custumers.



### Initial Modeling

In the initial modeling without handiling the imbalance in the data.

Logistic Regression Model :

Accuracy 81.5%
AUC 72%

Decision Tree Model:

Accuracy 73.4%
AUC 64%

KNN Classifier:

Accuracy 79.1%
AUC 65%

Support Vector Classifier:

Accuracy 79.57%
AUC 64.7%

Neural Network Classifier:

Accuracy 81%
AUC 69.2%

AdaBoost:

Accuracy 82%
AUC 72%

Gradient Boost:

Accuracy 81.5%
AUC 71.1%

Observation:
For the models fit without handing imbalance in data, we obeserve that the models tend to fit with relatively high accuracy around 80% on an average but the observing other metrics such as AUC and F1 score the values tend to be relatively low suggesting that the models tend to learn a bias towards the higher cardinality class.

### Handing the imbalanced data 

The major ways to handle Imbalance in data is by
- Oversampling minority class
- Undersampling majority class

Undersampling majority class is often not ideal as this involves discarding majority class observations ar random such that both the classes have equal cardinality. This discarding of samples means that we throw away useful information that will greatly impact the model's learning.

### SMOTE

SMOTE or Synthetic Minority Oversampling Technique attempts to handle the imbalanced datasets by generating new data points of the minority class such that after new data is added both classes have same cardinality.

SMOTE generates new data points by selecting randomly an observation and using k nearest neighbors of that sample where k is a paramemter set. The synthetic instance is then created by choosing one of the k nearest neighbors b at random and connecting a and b to form a line segment in the feature space. The synthetic instances are generated as a convex combination of the two chosen instances a and b.

This way we have a balance in class and also avoid information loss.

### Modeling using SMOTE

Logistic Regression Model:

Accuracy 86.4%
AUC 86.4%

AdaBoost Model:

Accuracy 85.9%
AUC 85.9%

Gradient Boost Classifier:

Accuracy 86.4%
AUC 86.4%

XGBoost Model:

Accuracy 86.6%
AUC 86.6%

Light GBM:

Accuracy 85.2%
AUC 85.2%

CatBoost:

Accuracy 86.2%
AUC 86.2%


Observation:
Using SMOTE oversampling we can observe that the models greatly improve their performance with an average accuracy of around 86% a 6% increase from initial modeling and other metrics such as F1 and AUC scores tend to be equal or very close to that of the accuracy score. Meaning that the model generalizes for both classes with equal imphasis on reducing FP and FN.
