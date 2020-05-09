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
The classes were imbalanced.To make my dataset balanced,I used downsampling method.

You can see the imbalance of the dataset with this plot :

![ana1](https://user-images.githubusercontent.com/33470542/81461380-47ce6380-9179-11ea-994e-3c7ecca1fc7a.png)


# Modeling

I compared four Unsupervised Anomaly Detection Models: Elliptic Envelope, Isolation Forest, OneClass SVM and Local Outlier Factor. 
Our strategy employs two noteworthy approaches. First, I tried to train the models using just majority class as inliers. Second, I used both classes for train the models.
Also I used two methods for finding hyperparameters :  GridSearch and BayesianOptimization.

# Result

I fould that Elliptic Envelope performed better than Isolation Forest,OneClass SVM and Local Outlier Factor on both methods. 
I got higher f1 score, when I traind Elliptic Envelope model on just one class in comparission with trainnig the model on both classes.
You can see the confusion matrix of both methods below :

The confusion matrix when I trained Elliptic Envelope model on just one class :

![ana3](https://user-images.githubusercontent.com/33470542/81461401-78160200-9179-11ea-997b-4343036fb09b.png)

The confusion matrix when I trained Elliptic Envelope model on both classes :

![ana2](https://user-images.githubusercontent.com/33470542/81461416-94b23a00-9179-11ea-95a0-607ab3aca2de.png)


Using BayesianOptimization gave me better result in comparision with GridSearch and I found the hyperparameters very quickly.
