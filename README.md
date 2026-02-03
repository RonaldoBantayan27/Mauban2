# Mauban2
Practical Application 3

Read Me File

Bank_Subscription_Prediction.ipynb

Business Understanding

The exercise is to compare the performance of the classifiers, namely KNearest Neighbor, Logistic Regression, Decision Tree Classifier, and Support Vector Classifier (SVC). 
A dataset related to marketing bank products over the telephone is utilized. The classification goal is to predict if a client will subscribe to a bank term deposit and determine the machine learning model that will best achieve this goal.
The predictions will help the marketing team to formulate a business strategy and a marketing campaign to increase bank clients subscription to term deposits.

Data Understanding

The dataset comes from the UCI Machine Learning repository. The data is from a Portugese banking institution and is a collection of the results of multiple marketing campaigns. Seventeen (17) marketing campaigns represent the data. 
The larger dataset has 41,188 rows while the smaller dataset has 4,119 rows. SVC uses the smaller dataset (a representative subset of the larger dataset) in order to conserve computational resources.

Data Preparation

The target variable 'y' is transformed to a numeric type "0" and "1". 
There are no missing values. 
The column 'duration' is dropped because the data do not help in the prediction. 
Duplicate rows are removed. 
Data that say ‘unknown’ are removed. 
Outliers are removed from numeric features. 
The columns ‘euribor3m’ and ‘nr.employed’ are strongly correlated with ‘emp.var.rate’. In order to reduce redundancy and multicollinearity, ‘emp.var.rate’ is dropped. This preserves underlying information while improving model stability and interpretability. 
'rare' months are grouped to address the data imbalance in the column 'month'. 
Categorical features are encoded.

Modeling

Before building the models, a baseline performance is established. A baseline model is built to benchmark the predictive ability of the four classifier models that are built. It is determined that the baseline Receiver Operating Curve AUC is 0.50. 
AUC (Area Under Curve) is the ability to distinguish between the positive (subscription) and negative (no subscription) classes across the model thresholds. AUC = 0.5 is random guessing while AUC = 1.0 is perfect separation of the classes. This means that the closer the model is to 1.0 the better it is in identifying the positive class. 
In order to address the imbalanced data, the class_weight parameter and SMOTE are used. 
Initially, simple models are built to compare train time, train and test accuracy. These models are then optimized and their thresholds adjusted to arrive at the final model version. 
A representative smaller dataset is used for SVC in order to conserve computational resources. 
The objective of modeling is to find the optimal mix of precision and recall. In achieving the objective of predicting the clients who will subscribe to a bank term deposit so that they can be pursued by the marketing department, the best classifier that can identify the clients the most is determined. 
Grid search functions are used to optimize the model parameters. 
Since the potential gains are valued more than the cost of subscription, recall is maximized at the expense of precision and accuracy. A suitable mix of precision and recall that is aligned with the business strategy is proposed. Given the lifetime value and the cost of subscription, precision and recall combinations are iterated to determine the threshold that maximizes profit. 
The metrics of accuracy, recall, precision, F2 score, AUC and profit/loss are determined to evaluate the different models.
The formula for the F-score is F_β= (1+β^2 )(PR)/ 〖(β〗^2 P + R) where P is precision and R is recall.
It is a common metric used to find the best balance between catching as many positive cases as possible (Recall) and being accurate when you do (Precision).
F2 score is where β=2 and it is considered that Recall is twice as important as Precision.

Evaluation

Based on the comparison using the metrics of accuracy, precision, recall, F2 score, AUC and Profit/Loss, the Support Vector Classifier (SVC) is the clear winner being ahead in almost all of the metrics especially on AUC. Decision Tree is ahead in recall (99%) but SVC is right behind it (98%). Otherwise, SVC is ahead in all the other metrics. 
With regard to feature importance, the four models generally are in agreement that macroeconomics (e.g., euribor rate, consumer confidence index, consumer price index, timing of campaign) rather than demographics (e.g., age, marital status, job, education) influence subscription the most.

Deployment

Samples were taken from the test data to demonstrate how to use the different classifiers in predicting subscription of clients. 
Next steps and recommendations: 
- continue model development to include identification of clients who are likely to subscribe to a term deposit
- deploy the model for use by marketing teams for sales campaigns and by the leadership for strategic planning and forecasting
- calculate realistic assumptions on the cost of subscription and potential gains for budget purposes and for tuning the profit/loss analysis
- tune the threshold according to the relative cost of subscription and potential gains
- continue model development to validate the features relative importance to guide management on which features need to be given particular attention in order to optimize subscription
