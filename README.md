**Predicting 30-Day Hospital Readmissions Among Diabetic Patients**

**Project Overview**

Hospital readmissions can increase healthcare costs and place additional pressure on medical staff. Identifying patients who are more likely to return to the hospital can help healthcare providers plan better follow-up care.

This project uses machine learning to predict the risk of readmission within 30 days of discharge for patients with diabetes. It compares traditional statistical methods with automated machine learning to determine which approach performs better.

The goal is to support hospital decision-making by identifying higher-risk patients who may benefit from additional care after discharge.

**Dataset**

The project uses the publicly available Diabetes 130-US Hospitals dataset, containing 101,766 hospital encounters and 50 original variables.

The analysis focuses on patients admitted through the emergency room. After removing encounters involving death or hospice discharge, the final dataset contained:

55,850 hospital encounters

40,373 patients

11.98% readmission rate within 30 days

The dataset is excluded from this repository. It can be obtained from the UCI Machine Learning Repository.

**Methods**

Two prediction approaches were compared:

Logistic Regression: A traditional statistical method used as the baseline.

XGBoost: A machine learning model selected using FLAML, an automated machine learning (AutoML) Python library that tests and compares different models.

Patient records were divided into training and testing groups, ensuring that encounters from the same patient were not split across both groups.

The models were evaluated using 11,157 previously unseen hospital encounters.

**Model Performance**

Performance Measure             Logistic Regression          XGBoost

ROC AUC                         0.6388                       0.6591

Average Precision               0.2087                       0.2209


XGBoost performed slightly better than logistic regression in identifying patients at higher risk of readmission.

When the highest-risk 20% of encounters were flagged, XGBoost identified 488 of the 1,313 actual readmissions, representing 37.17%.

Of the 2,232 flagged encounters, 21.86% resulted in readmission, compared with the overall test readmission rate of 11.77%.

These results suggest that the model could help hospitals prioritize patients who may need additional follow-up care.

**Model Visualizations**

**Readmission Risk Analysis**

This visualization shows how readmission rates change across patient risk groups and highlights the relationship with previous hospital use.

Model Comparison and Important Predictors

This visualization compares the predictive performance of logistic regression and XGBoost and highlights the factors most useful for predicting readmission.

**Potential Financial Benefits**

A financial simulation was conducted to estimate the potential benefits of using the model to prioritize follow-up care.

For every 10,000 hospital encounters, targeting the highest-risk 20% could potentially prevent an estimated 65.6 readmissions, generating projected net savings of $497,343.36.

These estimates assume that follow-up care prevents 15% of readmissions among correctly identified higher-risk patients, with a cost of $15,200 per readmission and $250 per patient receiving additional support.

These are hypothetical financial projections, not actual hospital savings.

**Technologies Used**

Python

Jupyter Notebook

pandas and NumPy

scikit-learn

FLAML

XGBoost

Matplotlib

**Limitations**

The model was developed using historical hospital data and has not been tested in a real clinical setting. Its predictive performance is modest, so it should support rather than replace clinical judgment.

The current notebook also contains a known data preparation issue where unknown gender values were classified as Female. This requires correction and model retraining before the results can be considered final.

Because the analysis uses discharge-related information, the model is better suited for discharge planning than prediction at initial admission.

**Future Improvements**

Correct the gender data preparation issue and retrain the models.

Evaluate performance using more recent hospital data.

Investigate differences in predictive performance across patient groups.

Improve model performance and assess reliability.

Explore a small clinical pilot to evaluate whether targeted follow-up care reduces readmissions.

**References**

Strack, B., et al. (2014). Impact of HbA1c measurement on hospital readmission rates. BioMed Research International, 2014, Article 781670.

Agency for Healthcare Research and Quality. HCUP Statistical Brief No. 278. Used as a reference for estimated hospital readmission costs.

**Project Purpose**

This project demonstrates the application of machine learning, predictive analytics, and financial analysis to a healthcare challenge. It combines technical modeling with practical recommendations to support better patient care and more efficient use of hospital resources.
