# Telecom-Churn-Project
Problem Statement:
Business problem overview
In the telecom industry, customers are able to choose from multiple service providers and actively switch from one operator to another. In this highly competitive market, the telecommunications industry experiences an average of 15-25% annual churn rate. Given the fact that it costs 5-10 times more to acquire a new customer than to retain an existing one, customer retention has now become even more important than customer acquisition.
For many incumbent operators, retaining high profitable customers is the number one business goal.
To reduce customer churn, telecom companies need to predict which customers are at high risk of churn.
In this project, you will analyse customer-level data of a leading telecom firm, build predictive models to identify customers at high risk of churn and identify the main indicators of churn.
Definitions of churn:
Revenue-based churn: Customers who have not utilised any revenue-generating facilities such as mobile internet, outgoing calls, SMS etc. over a given period of time. One could also use aggregate metrics such as ‘customers who have generated less than INR 4 per month in total/average/median revenue’.
The main shortcoming of this definition is that there are customers who only receive calls/SMSes from their wage-earning counterparts, i.e. they don’t generate revenue but use the services. For example, many users in rural areas only receive calls from their wage-earning siblings in urban areas.
Usage-based churn: Customers who have not done any usage, either incoming or outgoing - in terms of calls, internet etc. over a period of time.A potential shortcoming of this definition is that when the customer has stopped using the services for a while, it may be too late to take any corrective actions to retain them. For e.g., if you define churn based on a ‘two-months zero usage’ period, predicting churn could be useless since by that time the customer would have already switched to another operator.
In this case study, we will use the usage-based definition to define churn.
High-value churn:
In the Indian and the Southeast Asian market, approximately 80% of revenue comes from the top 20% customers (called high-value customers). Thus, if we can reduce churn of the high-value customers, we will be able to reduce significant revenue leakage.
In this project, we will define high-value customers based on a certain metric (mentioned later below) and predict churn only on high-value customers.
Business Objective:
The business objective is to predict the churn in the last (i.e. the ninth) month using the data (features) from the first three months. To do this task well, understanding the typical customer behaviour during churn will be helpful.The dataset contains customer-level information for a span of four consecutive months - June, July, August and September. The months are encoded as 6, 7, 8 and 9, respectively.
Different Phases in Customer churn:
It is intutive that, to predict whether the customer will churn or not and what are the driving forces behind the customer churn, one must understand the various phases the customer goes through before he/she decides to switch to another network operator.
The good phase: In this phase, the customer is happy with the service and behaves as usual.
The action phase: The customer experience starts to sore in this phase, for e.g. he/she gets a compelling offer from a competitor, faces unjust charges, becomes unhappy with service quality etc. In this phase, the customer usually shows different behaviour than the ‘good’ months. Also, it is crucial to identify high-churn-risk customers in this phase, since some corrective actions can be taken at this point (such as matching the competitor’s offer/improving the service quality etc.)
The churn phase: In this phase, the customer is said to have churned. You define churn based on this phase. Also, it is important to note that at the time of prediction (i.e. the action months), this data is not available to you for prediction. Thus, after tagging churn as 1/0 based on this phase, you discard all data corresponding to this phase.
In this case study, the dataset contains a 4-month window, the first two months are the good phase, the third month is the action phase, while the fourth month is the churn phase.
How to seggregate High-Value customers?
High-value customers are defined as follows: Those who have recharged with an amount more than or equal to X, where X is the 70th percentile of the average recharge amount in the first two months(the good phase).
How to Tag as churners for customers?
Tag the churned customers (churn=1, else 0) based on the fourth month as follows: Those who have not made any calls (either incoming or outgoing) AND have not used mobile internet even once in the churn phase. The attributes you need to use to tag churners are:
total_ic_mou_9
total_og_mou_9
vol_2g_mb_9
vol_3g_mb_9
After tagging churners, remove all the attributes corresponding to the churn phase (all attributes having ‘ _9’, etc. in their names).
Modelling Requirement
The predictive models need to serve two purposes:
It will be used to predict whether a high-value customer will churn or not, in near future (i.e. churn phase). By knowing this, the company can take action steps such as providing special plans, discounts on recharge etc.
It will be used to identify important variables that are strong predictors of churn. These variables may also indicate why customers choose to switch to other networks.
Why do we need multiple Models?:
Here, We have a large number of attributes, and thus we should try using a dimensionality reduction technique such as PCA and then build a predictive model for customer churning.
The model created by PCA is generally not easy to interpret. Hence we need another strong classification model to identify the significant factors that can impact the customer churning.
After PCA, we can use any classification model like the Logistict Regression or any Tree families.
Since the rate of churn is typically low (about 5-10%, this is called class-imbalance) - we need to apply techniques to handle class imbalance.
Approach for Predictive Model(i):
Preprocess data (convert columns to appropriate formats, handle missing values, etc.)
EDA to extract useful insights (whether directly useful for business or for eventual modelling/feature engineering).
Derive new features/Dummies.
Apply PCA for dimensionality reduction.
Train a variety of models, tune model hyperparameters, etc. (handle class imbalance using appropriate techniques).
Model evaluation using appropriate metrics.
