# Machine_Learning

## Objectives
The goals of this challenge is to:

- Implement machine learning models
- Use resampling to attempt to address class imbalance
- Evaluate the performance of machine learning models to predict credit risk.

## Technoligies
- Python (version 3.7.7)

## Resources

- Dataset: cf. *LoanStats_2019Q1.csv* in [Resources](/Challenge/Resources) folder
- Notebook: cf. *credit_risk_ensemble.ipynb* and *credit_risk_resampling.ipynb* files [Challenge](/Challenge) folder

## Results

### Balanced accurancy

> Balanced accurancy recap (best value first):

|Type|Model|Balanced accurancy score|
|---|--|--|
|Ensemble|EasyEnsembleClassifier|0.9316600714093861|
|Ensemble|BalancedRandomForestClassifier|0.7290249400290825|
|Naive Random Oversampling|RandomOverSampler|0.6594349419740851|
|Combination (Over and Under) Sampling|SMOTEENN|0.6593675036353027|
|SMOTE Oversampling|SMOTE|0.6591391394752197|
|Undersampling|ClusterCentroids|0.5378731395122675|

### Confusion matrix

> Confusion matrix recap:


| |High Risk Predicted|Low Risk Predicted|
|---|-----------|-----------------|
|*EasyEnsembleClassifier*|
|High Risk|93|8|
|Low Risk|983|16121|
|*BalancedRandomForestClassifier*|
|High Risk|62|39|
|Low Risk|2665|14439|
|*RandomOverSampler*|
|High Risk|72|29|
|Low Risk|6739|10365|
|*SMOTEENN*|
|High Risk|74|27|
|Low Risk|7080|10024|
|*SMOTE*|
|High Risk|63|38|
|Low Risk|5225|11879|
|*ClusterCentroids*|
|High Risk|68|33|
|Low Risk|10220|6884|

### Precision and recal score

> Precision and recal score recap:

| |Precision |Recall|F1|
|---|-----------|-----------------|---|
|*EasyEnsembleClassifier*|
|High Risk|0.09|0.92|0.16|
|Low Risk|1.00|0.94|0.97|
|*BalancedRandomForestClassifier*|
|High Risk|0.02|0.61|0.04|
|Low Risk|1.00|0.84|0.91|
|*RandomOverSampler*|
|High Risk|0.01|0.71|0.02|
|Low Risk|1.00|0.61|0.75|
|*SMOTEENN*|
|High Risk|0.01|0.73|0.02|
|Low Risk|1.00|0.59|0.74|
|*SMOTE*|
|High Risk|0.01|0.62|0.02|
|Low Risk|1.00|0.69|0.82|
|*ClusterCentroids*|
|High Risk|0.01|0.67|0.01|
|Low Risk|1.00|0.40|0.57|

### Analysis

Based on the balanced accuracy, *EasyEnsembleClassifier* model, with an accuracy of about 90%, outperforms the others five models which are all about 70% of accuracy (except the *ClusterCentroids* which is the less accurate with a 50% mark).
In overall, based on our dataset, all models have quite a perfect precision for predicting low risk credit (about 100%!) but have a really bad precision to predict high risk credit. *EasyEnsembleClassifier* model also outperforms other models but its precision is limited to about 9% which could lead to a lot of false positives (loans detected as high risk whereas they present low risk).
Regarding sensitivity, again, the *EasyEnsembleClassifier* model shows the best results as it correctly caught about 92% of high risk loans and about 94% of low risk ones.
Thus, our objective would mainly be to build/find a model that find the maximum of high risk loans. In that way, *EasyEnsembleClassifier* model could be a could solution but it presents an important flaw which could be problematic: this model would pop-up a lot of loans as high risk ones whereas they present low risk which could lead to a lot of additional work for end-user (which its low F1 score shows).

#### Recommendation

**Even if the *EasyEnsembleClassifier* model ends up with having the best overall results, we would recommend to perform additional tasks:**
- **Deleted some "parasite" features in our dataset which present the lower impact on this model in order to strengthen it**
- **If the model’s precision regarding high risk is significant higher and the precision is acceptable/manageable for end-user:**
    - > ***EasyEnsembleClassifier* model should be picked**
- **If one of the two conditions above is not fulfilled:**
    - > **Another model must be found**

