Anomaly-Detection-Models-for-Imbalanced-Datasets

# Business Problem

For banks, risk management and default detection have always been a crucial part in issuing credit cards. Defaults on credit card bill payment can result in a great financial loss. 
In order to reduce or even prevent loss of this kind, banks need to determine appropriately given credit for each specific client based on their information.
Back in the great recession, many credit card issuers faced a credit card debt crisis. 
Card-issuing banks over-issued credit cards to unqualified applicants in order to gain market shares.
At the same time, cardholders, irrespective of their repayment ability, overused credit cards for consumption purposes and accumulated heavy debts. 
This crisis caused a blow to consumer financial confidence and presented a big challenge for both banks and cardholders.

# Solution

I build an Anomaly Detection Model to identify which client has paid his credit card statement and which one not.

# Data

The dataset contains the credit information from more than 30000 clients with multiple attributes including marital status, education, age, and payment history, etc.
The classes were imbalanced.To overcome class imbalance,I used downsampling method

![ana1](https://user-images.githubusercontent.com/33470542/81461380-47ce6380-9179-11ea-994e-3c7ecca1fc7a.png)


# Modeling

I compare four unsupervised Anomaly Detection Models: EllipticEnvelope, IsolationForest, OneClassSVM and LocalOutlierFactor. 
Our strategy employs two noteworthy approaches. First, we try to train our model using just majority class as inliers. Second, we use both classes for train our models.
Also I used two methods for finding hyperparameters:GridSearch and BayesianOptimization.

# Result

I fould that EllipticEnvelope performed better than IsolationForest,OneClassSVM and LocalOutlierFactor on both methods, and in first method, f1 score is better for minority class in EllipticEnvelope model.

![ana3](https://user-images.githubusercontent.com/33470542/81461401-78160200-9179-11ea-997b-4343036fb09b.png)

![ana2](https://user-images.githubusercontent.com/33470542/81461416-94b23a00-9179-11ea-95a0-607ab3aca2de.png)


Using BayesianOptimization gave me better model in comparision with GridSearch despite of its speed. BayesianOptimization is not a time consuming method and we can find the hyperparameters very quickly
