# Anomaly-Detection-Models-for-Imbalanced-Datasets

# Business Problem

For banks, managing the credit risk of their clients has always been a fundamental part of their business. Credit card defaults obviously represent a significant financial risk for these institutions. To minimize this type of potential loss, banks need to accurately determine the likelihood that a particular credit card holder will pay them back. During the Great Recession, many credit card issuers were forced to deal with a surge in defaults. It turns out that card-issuing banks over-issued credit to unqualified applicants in an attempt to increase their market share. At the same time, cardholders, irrespective of their repayment ability, overused credit cards for consumption purposes, and accumulated heavy debts. This crisis caused a blow to consumer financial confidence and presented a big challenge for both banks and cardholders.

# Solution

Recent advances in machine learning have essentially collapsed the cost of predictions across virtually every domain that operates on certain algorithms and generates data (which is to say, every industry). For this specific business problem, I built an Anomaly Detection Model to identify which clients paid their credit card bill and which did not. After training and fine-tuning, I calculated the F1 score to assess the model's performance. I chose this as my evaluation metric because it accounts for both precision and recall.

# Data

The dataset contains credit information from more than 30000 clients with multiple attributes including marital status, education, age, and payment history, etc.

However, the distribution of paid vs unpaid observations in the dataset was far from equal. This is a problem since most predictive classification models assume that the distribution of target variables are equal. This imbalance is fairly common in real-world scenarios. For the two-class case, one assumes that the minority or rare class is the positive class, and the majority class is the negative class. Often the minority class is very infrequent, such as 1% of the dataset. If one applies most traditional classifiers on the dataset, they are likely to predict everything as negative (the majority class). This was often regarded as a problem in learning from highly imbalanced datasets.

To make my dataset balanced, I used the downsampling method. I have around 30000 samples and in this case by using downsampling method
I wont lose so many information. But when we have small dataset using downsamling method isn't recommended because of losing  information.



You can see the imbalance of the dataset with this plot :

![ana1](https://user-images.githubusercontent.com/33470542/81461380-47ce6380-9179-11ea-994e-3c7ecca1fc7a.png)


# Modeling

I compared four Unsupervised Anomaly Detection Models: Elliptic Envelope, Isolation Forest, OneClass SVM, and Local Outlier Factor. 
Our strategy employs two noteworthy approaches. First, I tried to train the models using just the majority class as inliers. Second, I used both classes to train the models.
Also, I used two methods for finding hyperparameters:  GridSearch and BayesianOptimization.
I have shown the result of classification report for Isolation Forest.

Classification report for Isolatin Forest training on one class using Grid Search: 

![IF1](https://user-images.githubusercontent.com/33470542/83418854-3b44d000-a3f2-11ea-95af-48b74e162701.png)

Classification report for Isolatin Forest training on one class using Bayesian Optimization:

![IFB1](https://user-images.githubusercontent.com/33470542/83418939-557eae00-a3f2-11ea-8bc9-d8ab1aec8c84.png)

Classification report for Isolatin Forest training on both classes using Grid Search:

![IF2](https://user-images.githubusercontent.com/33470542/83418983-63ccca00-a3f2-11ea-9a80-007d93fd2c11.png)

Classification report for Isolatin Forest training on both classes using Bayesian Optimization:

![IFB2](https://user-images.githubusercontent.com/33470542/83419044-72b37c80-a3f2-11ea-82ba-51bc833bae96.png)

# Result

I found that Elliptic Envelope performed better than Isolation Forest, OneClassSVM, and Local Outlier Factor on both methods. 
I got a higher f1 score when I trained the EllipticEnvelope model on just one class in comparison with training the model on both classes.
You can see the confusion matrix of both methods below:

The confusion matrix when I trained Elliptic Envelope model on just one class:

![ana3](https://user-images.githubusercontent.com/33470542/81461401-78160200-9179-11ea-997b-4343036fb09b.png)

The confusion matrix when I trained Elliptic Envelope model on both classes:

![ana2](https://user-images.githubusercontent.com/33470542/81461416-94b23a00-9179-11ea-95a0-607ab3aca2de.png)


Using BayesianOptimization gave me better results in comparison with GridSearch and I found the hyperparameters very quickly.
