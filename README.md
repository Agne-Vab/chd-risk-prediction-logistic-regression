# Regression: Cardiovascular Disease Prediction

## Introduction

This project applies predictive modeling techniques to analyze the Cardiovascular Study Dataset sourced from [Kaggle](https://www.kaggle.com/datasets/christofel04/cardiovascular-study-dataset-predict-heart-disea/data). The goal is to develop a logistic regression model that predicts the 10-year risk of coronary heart disease (CHD). A key part of the project is determining the optimal prediction threshold by selecting and justifying an appropriate classification metric.

## Dataset

The dataset originates from the Framingham Heart Study, a longitudinal study of cardiovascular health and risk factors. It includes various attributes such as demographic information, lifestyle habits, and clinical measurements. The dataset is available on [Kaggle](https://www.kaggle.com/datasets/christofel04/cardiovascular-study-dataset-predict-heart-disea/data) in train.csv format. Please review Kaggle's terms and conditions for more details on dataset usage.

## Objectives

This project aims to predict the 10-year risk of coronary heart disease (CHD) using logistic regression, focusing on the following key goals:

1. Import and prepare the Cardiovascular Study Dataset by addressing most critical data issues. 
2. Performing exploratory data analysis (EDA) to understand the data distribution, identify key patterns, and explore relationships between features and the target variable.
3. Splitting the data and building initial pipeline based on EDA findings. 
4. Accessing feature selection determining multicollinearity.
5. Developing and optimize a logistic regression model with a focus on maximizing recall to minimize false negatives and minimizing negative log loss for better probabilistic predictions.
6. Defining the final model and test its performance on the test dataset.
7. Insights and Recommendations: Provide actionable insights based on the analysis and suggest improvements for future work.

## Methodology 

1. **Data Splitting**: 
    - Stratified splitting ensured proportional representation of the target variable across train and test sets.
2. **Feature Transformation**:
    - Log transformation applied to highly skewed variables (glucose).
    - Standard scaling applied to numerical features for consistency in modeling.
3. **Metric Selection**:
    - Primary focus on F2-score (prioritizing recall for minority classes by balancing it with precision). That's because risk of false negatives in this medical risk assesement setting is higher than false positives. 
    - Using log loss as secondary parameter to make sure probabilistic predictions are not ignored when tuning.
4. **Hyperparameter Tuning**:
    - Utilized GridSearchCV and TunedThresholdClassifierCV.
    - Cross-validation applied for robust evaluation.

## Results

1. **Model Performance:**
    - Improvement in recall for the minority class (individuals at high risk of CHD) after threshold adjustment:
        - Test set recall increased from 70% to 95%.
        - Training set recall increased from 71% to 91%.
    - The model demonstrates a ability to identify high-risk individuals.

2. **Trade-offs:**
    - Accuracy decreased with threshold adjustments:
        - Training accuracy: reduced from 66% to 43%.
        - Test accuracy: reduced from 64% to 41%.
    - Despite lower accuracy, the model outperformed the baseline (~15%).

3. **Class Balance.** The model achieved higher recall for the minority class (70%) compared to the majority class (63%), indicating it is not heavily biased toward the majority.

## Recommendations

As this is project did not test out all possible model improvement techniques, I would not recommend using it in healthcare connext, where predictive outcomes can have serious consequences. However, if it would be used for testing purposes, I would recommend:

1. If used, **continuously track precision, recall, and other metrics in real-world deployments**, especially considering possible data drift, to ensure the model aligns with the intended goals. Additionally, decreasing threshold if higher recall is needed. 
2. **Making sure the recency of medical data is clear** for future training model so that it would be easier to access distribution accuracy. Ensure that data is recent would also make training and testing data reflect current medical practices and behaviors better. 
3. **Starting to track additional variables such as tobacco alternatives in the study.** Their consumption rates are increasing and are present especially among younger people who are still in highschool [(CSD)](https://www.cdc.gov/tobacco/e-cigarettes/youth.html?s_cid=OSH_emg_GL0001&gad_source=1&gclid=Cj0KCQiA4rK8BhD7ARIsAFe5LXJqi-1plgloDCxWMHzUbynqrs2Fo1FNg_ifpU5vu1H-rrbJq7C8JcYaAnOmEALw_wcB). Thus, knowing that smoking is one of the top predictors in this model, tracking affect of it's alternatives would help to improve it. 
4. Additionally, **including other possible risk factors to the data tracking.** Not included in dataset but could be relevant [(based on NHS)](https://www.nhs.uk/conditions/cardiovascular-disease/) are kidney disease, family history, alcohol and more. Including them could help improve the model. 

## Possible analysis improvements

1. **Experimenting with alternative feature scaling techniques.** Testing scaling methods like RobustScaler, which is less sensitive to outliers, or MinMaxScaler, to assess if they result in better performance compared to StandardScaler, particularly for recall and log-loss metrics. 
2. **Refine outlier handling**. Revisit outlier detection and removal strategies, including more aggressive thresholds or domain-specific rules, to evaluate their impact on both training and test set performance. Testing techniques like Z-score-based capping.
3. **Improve how class imbalance is addressed**. Evaluating advanced techniques to handle class imbalance, such as SMOTE (Synthetic Minority Oversampling Technique), oversampling or undersampling. 
4. **Test more complex models.** For example, Random Forest to to assess whether they outperform logistic regression in terms of recall and overall accuracy. 
5. **Integrating established cardiovascular risk scores.** This could enhance model performance by leveraging pre-calculated indicators of CHD risk and providing a benchmark for evaluating model's recall and precision.

## How to Use This Repository

1. **Data**: Load the dataset from the provided [Kaggle](https://www.kaggle.com/datasets/christofel04/cardiovascular-study-dataset-predict-heart-disea/data) link or this repository.
2. Install Dependencies: install required packages using [requirements.txt](https://github.com/TuringCollegeSubmissions/avabal-PYDA.4.4/blob/main/requirements.txt).
3. Display the detailed analysis done by opening [notebook](https://github.com/TuringCollegeSubmissions/avabal-PYDA.4.4/blob/main/Cardiovascular_Disease_Prediction.ipynb). 

## Contact

Discord - "Agnė Vabalaitė | avabal".
Gmail - vab.agne@gmail.com