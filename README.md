# Machine_Learning

## Objectives
The goals of this challenge is to:

- Implement machine learning models
- Use resampling to attempt to address class imbalance
- Evaluate the performance of machine learning models

## Technoligies
- Python (version 3.7.7)

## Resources

- Dataset: cf. *LoanStats_2019Q1.csv* in [Resources](/Resources) folder
- Notebook: cf. *credit_risk_ensemble.ipynb* and *credit_risk_resampling.ipynb* files

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

| |Precision |Recall|
|---|-----------|-----------------|
|*EasyEnsembleClassifier*|
|High Risk|0.09|0.92|
|Low Risk|1.00|0.94|
|*BalancedRandomForestClassifier*|
|High Risk|0.02|0.61|
|Low Risk|1.00|0.84|
|*RandomOverSampler*|
|High Risk|0.01|0.71|
|Low Risk|1.00|0.61|
|*SMOTEENN*|
|High Risk|0.01|0.73|
|Low Risk|1.00|0.59|
|*SMOTE*|
|High Risk|0.01|0.62|
|Low Risk|1.00|0.69|
|*ClusterCentroids*|
|High Risk|0.01|0.67|
|Low Risk|1.00|0.40|