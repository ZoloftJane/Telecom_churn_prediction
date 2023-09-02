# Telecom_churn_prediction
## Final project from Practicum by Yandex
The goal of this project was to develop a binary classification model that predicts whether a customer will leave the company soon based on the clientele's personal data, including information about their plans and contracts.

**The ROC_AUC metric on the test set had to be no more than 0.85.**
**The additional metric is accuracy.**

This project's repo includes the project's jupyter notebook (Telecom_churn_prediction.ipynb).

We have completed the following steps in this project:

### 1. Descriptive statistics

We have merged 3 provided dataframes and studied the input.

### 2. Data preprocessing

First, we converted the target variable into a binary numeric one. Then we have converted all column names to lower case letters. We checked the data for duplicates.

Next step was to fill in missing values. It was done by filling them with the 'No' value for those cases when clients were not using the service. The missing internet_service values we will replace with the 'not_available' value.

Then we made some necessary changes in the data types of a few variables.

### 3. EDA

We examined both the features and the target. And also analysed correlation between features with phik.

There are a lot of observations with the total_charges values less than 100 dollars. These are most likely either new clients or those who quickly left the company after just a month. There are quite a lot of 'loyal' customers as well who stayed with the company for more than 5 years based on the days_since_join variable distribution. A big amount of clients pay around 20 dollars a month for Telecom services. Otherwise, there were no visible outliers.

We noticed that our target classes were imbalanced: there are at least twice as many observations for the customers who stayed with Telecom than for those who left. On average, there is a 26.5% probability that a customer will leave the company.

### 4. Additional assignment

We compared the monthly payment distribution (monthly_charges) of all active clients with the clients who have left. The biggest difference between the 2 groups is that there is a big number of active clients who pay only 20 dollars monthly for Telecom services. Exited clients used to pay more, on average. Maybe that was one of the reasons why they left the company.

Then we compared the behavior of the clients from the two above groups for both the usage of the internet services and the phone services.

The share of the internet users from the 'active' clients is 4 times smaller than that of the 'exited' users. There are more 'active' clients who are not using the internet than in the 'exited' clients group. We also see that the network is set up through a fiber optic cable for the 'exited' clients twice as many times as for the 'active' clients. This observation could mean that the quality of the fiber cable internet is lower than that of the DSL internet and that was one of the reasons for the customers to leave the company.

The phone services usage distribution is almost the same for both groups. There are slightly (3.5%) more 'active' users who are not using multiple lines than in the 'exited' group but the difference is not very significant.

### 5. Splitting the data

Data was split into train and test sets with the 25/75 ratio

### 6. Model selection

We have compared Logistic Regression, Random Forest and CatBoost models. We used Pipeline and Transformers for normalizing and encoding features, and GridSearchCV for fitting hyperparameters. We have chosen the CatBoost model based on the ROC_AUC and Accuracy scores.

### 7. Test the model

The test score is 0.1% higher than the train score, no overfitting observed. The target metric was met.


### Results

The LGBM model has shown the best results (test ROC_AUC of 0.93) in terms of quality. The target metric of 0.85 or higher has been reached.
