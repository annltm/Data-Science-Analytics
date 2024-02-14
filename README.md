The Dataset - Loan Default Prediction Challenge from Zindi https://zindi.africa/competitions/data-science-nigeria-challenge-1-loan-default-prediction

Objective--
In this project, we developed a binary classification model to assess the repayment of loans within a predefined time-frame. 
Additionally, we constructed a behavior risk model using a client's historical loan repayment data to determine their eligibility for future loans.

Data Preparation--
Three different datasets were used to build the model. 

Demographic Data  - contains demographic attributes of our sample.
Performance Data - contains client’s loan information to determine default. This  
                                      also include good_bad_flag, which is our target variable 
Previous Loan Data - contains data of repayment behaviour for previous loans

1.	Data transformed by renaming, feature engineering, and converting data types.
2.	Merged all three datasets and processed missing values. Filled missing values with  “no disclosure” for 'employment_status_clients', 'bank_branch_clients', 'level_of_education_clients'. For birth data, missing values were filled with mean.
3.	Dropped insignificant feature from our merged datasets such as “approveddate”, “creationdata”, and ‘bank_branch_clients”. 
4.	For categorical features, we implemented one hot encoding, and used MinMaxScaler for numerical values for better results on our model.

Model Design--
We selected  a Balanced Random Forest classifier as it outperformed other classifiers without using PCA. This was observed based on F1 Score and Recall of the minority class (uniquely important to mitigating losses from loan default). A balanced ensemble model was required in order to deal with a very imbalanced data set
Hyper Parameter Tuning
RandomSearchCV tuning gave us the highest F1 Score with below hyperparameters. It improved our weighted avg. F1 Score to 0.72 from 0.69
Best Hyperparameters: {'n_estimators': 135, 'max_samples':0.1 , ‘max_features’:9}
Feature Selection
Eliminating less significant features with importance scores less than 0.002 improved our model.

Model Evaluation--
Using the tuned hyper parameter by RandomSearch and feature selection, results are below.  
Our model has relatively high precision and recall for classifying class 1. We’ve tried to mitigate data imbalance using SMOTE technique, but it was insignificant.
Confusion Matrix--
-	104 True Positive 
-	74 False Positive :  74 instances are predicted incorrectly as positive 
-	482 True Negative
-	158 False Negative :  158 instances are predicted incorrectly as negative 

AUC--
 
AUC being 0.7 is not super powerful, but the model is somewhat better than random guessing. It could be further improved and has potential to optimally predict loan default. 
Conclusions
We were able to build a Balanced Random forest Classifier successfully with support by Random Search Hyperparameter tuning and feature selection,
demonstrating improved performance in predicting loan default. Our model could expect 58 % of default payment, and it offers a moderate solution, 
which could be further improved if time allowed us. 
