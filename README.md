# Practical_Assignment_3

PROBLEM STATEMENT:

The business objective of the task is to develop a model that can effectively predict whether a client will subscribe to a term deposit. The overarching goal is to optimize resource allocation, increase conversion rates, and improve overall marketing effectiveness. 

DATA UNDERSTANDING:
The first step was to understand the dataset and explore what information it contains, and how this could be used to inform better business understanding. The steps involved were:

1. Load Data
2. Preview Data
3. Assess the data
4. Check for null values
5. Exploratory Data Analysis (EDA)

The dataset comes from the UCI Machine Learning repository link. The data is from a Portugese banking institution and is a collection of the results of multiple marketing campaigns.This data represents 17 marketing campaigns occurring between May 2008 and November 2010. The  UCI Machine Learning repository page states that there are no missing values, so therefore we moved on exploratory analysis. Exploratory data analysis led us drop the "duration" feature becuase this feature is only helpful for benchmark purposes and is not ideal for a realistic predictive model.Data preprocessing for categorical columns and numerical columns are needed as well.

DATA ANALYSIS FINDINGS:

By developing a baseline model, we achieved a model accuracy of about 88.6%. To improve accuracy we built a simple logistic regression model.The logistic Regression Model produced a accuracy score of 89.68%, indicating better overall performance compared to the baseline model. In both cases, class 1 has low scores for all columns (precision, recall, f1-score). This is due to the fact that the dataset is imbalanced and the model is possibly prioritizing class 0. In other words, Class 1 is less frequent than class 0, which can lead to models being biased towards predicting class 0 more accurately (as we see in both models). Recall having a 21% is bad because recall measures how well the model identifies actual positives (clients who subscribe). Low preciision is also bad because precision measures how many of the predicted positives (clients predicted to subscribe) are actually correct. In this case, the model correctly predicts 64%. By intrigating class weighting, we were able to increase the recall from 0.21 to 0.63. However, both the precision, and model accuracy dropped. The precision for class 1 dropped from 0.64 to 0.32, while the model accuracy dropped down to about 81%.

The ideal model for the busniess object is a model which ia able to identify true positives for class 1 (identifying potential subscribers). However, the precision for class 1 is very low. This means that among all the instances predicted as class 1, only 28% are actually correct, leading to a higher number of false positives. High recall means that the model is effective at capturing most of the potential subscribers. This is particularly important if missing out on potential subscribers (false negatives) has significant consequences, such as losing potential revenue. High precision means that when the model predicts a client will subscribe, it is likely correct. This is important for avoiding wasted resources on clients who are unlikely to subscribe.

For the Business Objective: Higher Recall should be prioritized because the goal is to capture as many potential subscribers as possible, even if it means some of the predictions are incorrect (i.e lower precision). This minimizes the risk of missing out on potential customers. Higher Precision should be prioritized if the cost of pursuing false positives (clients predicted to subscribe but don’t) is high. This ensures that marketing resources are spent more effectively.

F1-Score: Balnce between precision and recall. A high F1-score means that the model performs well in both identifying subscribers and avoiding false positives.

If the business context values capturing as many subscribers as possible and the cost of false positives is manageable, then a model with higher recall (even at the expense of precision) might be preferable. Conversely, if resources are constrained and you need to focus on clients who are more likely to convert, prioritizing precision might be better. If the the bank wants to emphasize acquiring the maximum number of subscribers, and managing false positives is within budget, then a model with higher recall at the cost of precision could proove useful. On the other hand, if resources are limited and the focus is on clients with a higher likelihood of conversion, prioritizing precision may be the better option. 

COMPARING MODELS:

Comparing model training time: KNN is the fastest to train, taking about 0.006 seconds. Logistic Regression and Decision Tree was also relatively quick (0.05 and 0.11 seconds, respectively). SVM takes the longest, about 49.3 seconds, which is significantly more time-consuming compared to the other models.

Comparing model training accuracy: All models show high train accuracy. Decision Tree shows a near perfect score with 0.99% accuracy. Logistic regression has the lowest, albeit about 90% train accuracy.

Comparing model test accuracy: The test accuracy for logistic regression is very close to the training accuracy of about 90%,which probably indicates that the model generalizes well and isn't overfitting. The test accuracy for KNN is slightly lower than the training accuracy of about 0.91%. This might suggest that while the model performs well on training data, it might be overfitting to the training set just a bit. The test accuracy for SVM is very close to the training accuracy of 0.90%, indicating good generalization. This model seems to be balancing well between fitting the training data and maintaining good performance on any unseen data. On the other hand, the Decision Tree model shows a significant drop from the training accuracy of about 0.99%. This suggests that the decision tree model is overfitting a lot (possibly capturing noise in the training data that doesn't translate to good performance on test data).

Important Notes: 

1. KNN: Fastest training time.
2. Decision Tree: Very high training accuracy, but also decent test accuracy. Susceptible to overfitting. 
3. Logistic Regression: Moderate performance across metrics. It’s a good baseline model, but might be less complex compared to KNN and Decision Tree.
4. SVM: Longest training time and slightly higher performance compared to KNN and Decision Tree.

INDIVIDUAL STUDY:

For the individual study, we tried benchmarking the model (i.e. not dropping the "duration" feature). By doing this we increased overall precision, recall, and F1-score to 0.41%, 0.90%, and 0.56% respectfully. There was also an improvement in the model comparisons. Notably, SVM took far less time to train. 

Next steps and recommendations:

1. Handle data imbalance more effectively
2. More feature engineering
3. More parameter tuning
