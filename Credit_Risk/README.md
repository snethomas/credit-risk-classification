# Module 12 Report Template

## Overview of the Analysis

Banks and other lenders use financial information of the borrower and of the loan itself, to predict if there is a risk of payment defaults.

--The objective here is to predict the health of a loan ie. high risk of deafulting vs healthy, based on factors like loan_size	,interest_rate	,borrower_income	,debt_to_income	,num_of_accounts	,derogatory_marks	and total_debt	
--This analyses provides 77K loan records that include these details for each loan and the corresponding loan status - ie healthy vs. high risk.
--The 77,536 loan records are flagged as 'healthy' vs 'high-risk' ie. 75,036 and 2,500 records each, respectively. 

-1- The first step of this supervised machine learning analyses is to divide the dataset into a 'train' [58,152=56,271(0)+1,881(1)] and 'test' dataset of [19,384=18,765(0)+619(1)] records
-2- Since the prediction is boolean ie. 1 or 0 - we used a Logistic Regression model.
-3- The model is first trained on the 'train' dataset and then applied to the 'test' dataset 
-4- The balanced accuracy score and confusion matrix was calculated to determine the quality of the model. 
-5- Since balanced accuracy was 95% - RandomOverSampler module from the imbalance-learn library was used to over sample the minority class in the data (in this case 1 or high-risk)
-6- The Logistic Regression model was then trained on the new training dataset - before being applied to the original test dataset

## Results

* Machine Learning Model 1: 

Training data had 58,152 records and test data had 19,384 records.

-1- Overall accuracy of the model in predicting loan status is very high at 99.2%. The balanced accuracy score (or average recall of each class) is 95%
-2- The precision of the 0 (healthy loan) predictions is 100%. The recall for 0 (healthy loan) predictions is also 100%. (These are rounded from 99.7% and 99.5% as calculated from the confusion matrix)
-3- However, for 1 (high risk loans) the precision is a little lower in comparison, at 85%. There is high recall at 91%.

So with this model there is lower probability of classifying a healthy loan as high-risk, than a high-risk loan as healthy.

* Machine Learning Model 2: 

RandomOverSampler was used to oversample the minority class in the data - thereby resulting in 77,036 records for both 0 and 1 in the training dataset

-1- The model with the new sample has similar accuracy of 99%. The balanced accuracy score (or average recall of each class) went up to 99% as well.
-2- The precision of 0 -healthy loan predictions stayed the same at 100% but recall went down to 99%.
-3- The precision of 1- high risk loans went down as well to 84%. However, there is an improvement in recall at 99%.

This model is very close in accuracy to the original model but it is able to classify 99% (recall) of the 1-high risk loans correctly. Making this a better model.

## Summary

* Which one seems to perform best? How do you know it performs best?

--Model 2 performs better than Model 1 even though the accuracy is similar at 99%. 
--This is clear from the balanced accuracy score which is higher at 99% for Model 2. 
--The recall rate for 1 or high-risk predictions increased from 91% to 99%, which is significant. This means that 99% of high-risk loans are predicted correctly in Model 2.

* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )

--In this analyses it is more important to predict the high-risk loans accurately. 
--Even if precision is low at 84% - which can lead to false positives/high-risk status prediction
--It is more important that recall is high at 99% - which means 99% of actual high risk loans were predicted correctly.

