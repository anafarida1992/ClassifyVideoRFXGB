**Project Tiktok aims to improve response time and efficiency through automating the initial claim process, predicting whether a TikTok video is a "claim" or an "opinion" based on a dataset of 19,382 rows by 12 columns:**\
A. A/B Test Comparing Verified vs. Unverified Accounts.\
B. Predicting Verified vs. Unverified Accounts.\
C. Classifying Claim vs. Opinion Videos.\
\
**A. A/B Test Comparing Verified vs. Unverified Accounts.**\
•	 Descriptive statistics compare average values of video_view_count for each group of verified_status, showing that videos from not_verified accounts have a higher number of views on average.\
•	To confirm the difference, a two-sample t-hypothesis test (independent t-test) with significance level 5% performed as part of the A/B test.\
•	It concludes that there is a statistically significant difference in the mean video view count between verified and unverified accounts on TikTok.\
\
**B. Predicting Verified vs. Unverified Accounts**\
•	Exploratory data analysis shows that verified users are more likely to post opinions. In order to explore into how video features relate to verified users, perform a logistic regression with verified status as the target. The results could help in improving the model for predicting whether a video is a claim or an opinion.\
•	Video_view_count and video_like_count are highly correlated (0.86). In order to meet the assumption of no strong multicollinearity between features, delete video_like_count and stay with video_view_count, video_share_count, video_download_count, and video_comment_count as features for the video metrics.\
•	Approximately 93.7% of the dataset represents videos posted by unverified accounts and 6.3% represents videos posted by verified accounts. So the outcome variable is imbalanced. Use resampling to create class balance in the outcome variable.\
•	The logistic regression model was able to achieve a precision of 61%, a recall of 84%, and an accuracy of 65%. These precision and recall values specifically pertain to the prediction of the "not verified" class, which is our target of interest. The "verified" class has different metrics, and the weighted average combines the results for both classes.\
•	Each additional second of the video_duration_sec is associated with 0.009 increase in the log-odds of the user having a verified status.\
•	Other video features have small estimated coefficients in the model, so their association with verified status seems to be small.\
\
**C. Classifying Claim vs. Opinion Videos.**\
•	The XGBoost model performed well but made more false negatives. Since identifying claims is the priority, the random forest model, with its better recall, is the better choice.\
•	Random forest model performed well on both validation and test holdout data. This model does not produce many false negatives. The model classified the claims and opinions very successfully.\
•	The model's most predictive features were all related to the user engagement levels associated with each video. It was classifying videos based on how many views, likes, shares, and downloads they received.
