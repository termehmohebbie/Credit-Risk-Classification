# Credit-Risk-Classification
## Overview of the Analysis
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;In this repository we used a dataset of historical lending activity from a peer-to-peer lending services company and built two models to be able to predict the creditworthiness of future borrowers to help banks and lending companies to decide better and lower the risk of losing their income.
The dataset provided by the bank has more than 77000 entries with key indicators such as loan size,	interest rate of the loan,	borrower's income,	debt to income ratio,	number of the borrower's accounts,	derogatory marks on borrower's credit report, borrower's	total debt and	the status of the loan which shows if the loan was healthy or not.

  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;To do so, we used two Logistic Regression models that estimate the probability of an event occurring based on a given dataset of independent variables which in our case is the status of a loan. Feeding the training data into the machine, we can compare that to the test data to see how well the model predicts the event that we want.
After analyzing the original data and the Logistic Regression model, we can see that there are 75036 non-defaults and 2500 defaults, so the dataset is not balanced. Therefore, we decided to adjust our dataset using Oversampling method to create a model that better predicts those that might default on their loan. ("Oversampling" is when you notice that one of the classes doesn’t have enough instances in the training set and you choose more instances from that class for the training. This will help us to train the model to better understand what it needs to look for in case of a default.)

  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The target/label values that we used for training and prediction evaluation were one-hot encoded loan status values denoted as 0 for low risk loans and 1 for high risk loans. The original target/label values had a total count of 75036 low risk loan values and 2500 high risk loan values, for a total of 77536 values. Once the data was resampled, the value count was 56271 for both the high risk and low risk loan values, for a total of 112542 values.

  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The first step of the ML process was creating the classification model. In this challenge we were using the Logistic Regression model from scikit-learn. After creating the model we used the .fit method to fit the model using the training labels. After fitting the model with the training labels we generated predictions by feeding the test features to the model's predict method. After generating the predictions we compared the test predictions with the correct test labels using metrics such as Balanced Accuracy Score, Confusion Matrix and Classification Report.

## Results
To evaluate and be able to compare the models, we used three metrics, balanced accuracy, precision and recall scores.

**Accuracy Score** shows how often the model was correct. 

**Precision Score** measures how confident we are that the model correctly made the predictions.

**Recall Score** indicates the number of actual default transactions that the model correctly classified as default.

* Machine Learning Model 1 (Trained using the original data) :
  * Balanced Accuracy Score : 0.9520479254722232 which means this model is 95% accurate.
  * Precision Scores :
    * Healthy Loans : 1 (100% precise)
    * High Risk Loans : 0.85 (85% precise)
  * Recall Scores :
    * Healthy Loans : 0.99 (99% correct)
    * High Risk Loans : 0.91 (91% correct)
    
    
* Machine Learning Model 2 (Trained using the oversampled data) :
  * Balanced Accuracy Score : 0.9936781215845847 which means this model is 99% accurate.
  * Precision Scores :
    * Healthy Loans : 1 (100% precise)
    * High Risk Loans : 0.84 (84% precise)
  * Recall Scores :
    * Healthy Loans : 0.99 (99% correct)
    * High Risk Loans : 0.99 (99% correct)
    

 ## Summary
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;From the above analysis, we can conclude that Oversampling method allowed the model to better predict if a loan was going to default or not. It increased the Accuraccy and the Recall score significantly. We noticed a slight loss in precision, but that's normal. There's always a trade-off between the precision and the recall, so it depends on which of these factors are more important for each case which fully depends on what we are trying to achieve, if we are trying to minimize offering loans to those that might potentially default, then the second model appears to offer us a much better option. If we are just trying to lend out the money without worrying too much about defaults (as they are a low occurance at 3.33%), then we can still work with the first model. Overall, both models did a great job at having over 95% accuracy and above 90% Recall.
In this case we are attempting to reduce our defaults, so I would suggest that we use the "Oversampling Model" to reduce that possibility.It is important to understand which variable we are trying to predict. In this case, it is more important to predict the High Risk loan than the Healthy Loan. Therefore, the "False Negatives" measurement plays a significant role in the performance evaluation of the model.
