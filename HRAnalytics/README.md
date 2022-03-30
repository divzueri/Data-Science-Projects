# HR Analytics: Likelihood a Data Scientist is Looking for a Job Change

## Context


Company X offers a few training courses related to data science and big data. Many people enroll in these courses. Of those who successfully complete and pass the course, only some are actively looking for a job change. Company X has collected demographic, educational, and career information on all course graduates in order to better understand which individuals are more likely to be looking for a job change.

As resources are limited, Company X wants to reduce the cost and time of reaching out to candidates who are less likely to be interested in working for them. The aim of this project was to build a predictive model that determines which candidates are most likely to be looking for a job change, prioritizing reducing Type II errors. Additionally, the results from this project might add more insight into which types of workers are more likely to be open to a job change in general.

## Objective
1. Build a predictive model (prioritizing precision) to select candidates that are open to a job change.

2. Identify the most influential features in predicting whether or not a candidate is open to a job change.

## Data

-   Sourced from Möbius on [kaggle](https://www.kaggle.com/arashnic/hr-analytics-job-change-of-data-scientists)
    
-   After cleaning and preprocessing, pre-split dataset contained 18,280 candidates and 40 features.

-   Features included:
	-  a) Demographic Information
	- b) Educational Background
	- c) Work Experience

- **Target Feature**: Looking for a job change (1 or 0)


## Procedure
• **Tools:** Pandas, NumPy, Matplotlib, Seaborn, Category Encoders, Scikit-Learn, Imbalanced-Learn

• **Data:** Some modications were made to the raw dataset.
1. Experience was binned into larger ranges.
2. Cities that represented less than 1% of total candidates were binned into an 'Other' category.
3. Rows with more than 5 missing values (out of 14 total columns) were dropped.

• **Modeling:** Four general types of models were trained and tested:

1. Logistic Regression
2. Random Forest Classifier
3. Support Vector Machine (Linear and RBF Kernels)
4. Gradient Boost Classifier (XGBoost).

Due to the imbalanced nature of the target feature (only ~25% positive case), each model was tested both with **a) different class weights** parameters, and **b)** **oversampling** of the minority class using the imbalanced-learn library. As the goal was to reduce Type II errors, each model was also tuned for precision using Grid Search CV.

## Model Metrics:

| Model |Precision  | Recall | Accuracy | F0.5 | AUC 
|--|--|--|--|--|--|--|
| Baseline: Dummy Classifier | 0.00 | 0.00 | 75.29 | 0.00 | .50 
| Logistic Regression | 59.16 | 55.67 | 79.54 | 58.42 | .797
| Random Forest Classifier | 58.95 | 62.90 | 80.23 | 59.89 | .800 | 
| SVC Linear | 59.16 | 54.10 | 79.42 | 58.07 | .797 | 
| SVC RBF | 57.91 | 59.45 | 79.29 | 58.20 | .790 | 
| **XGBoost**  | **60.10** | **59.92** | **80.24** | **60.04** | **.796** 


## Key Insights

Attributes that highly influenced candidate interest in working for Company X:
-   City development index
-   Years of experience
-   Current company information missing
-   Lack of relevant experience
-   Current full-time university student

Company X could either prioritize candidates meeting some (or all) of these criteria, or develop specific train-to-hire programs for certain candidate demographics (e.g. internship opportunities for students, career switch programs, etc).