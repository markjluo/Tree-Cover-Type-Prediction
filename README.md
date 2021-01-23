# Tree-Cover-Type-Prediction

Case Study - Cover Type Prediction
Jiatuan (Mark) Luo
11/03/2019

Exploratory Data Analysis (EDA)
1.	Describe the dataset and any interesting variables (feel free to include response). (Hint: It may be useful to provide a high-level summary (i.e. descriptive statistics) on the variables)
-	The data set consists of 55 columns and  581012 observations. There are 14 quantitative variables and 2 qualitative variables. The qualitative variables Soil_Type and Wilderness_Type are in the form of binary columns (0, 1), each area (observation) is classified into a soil type and wilderness type.
-	It is very interesting to see the patterns of how different cover types are distributed across areas of different soil and wilderness types.
-	From the boxplots, we can see that cover types 1, 2 and 7 have very high variance in horizontal distance from roadways comparing to other cover types and further away from roadways. This could indicate that they grow in wide range further away from the roads, while other species grow more closely around roadways.
-	Cover types 1,2,5 have many outliers in horizontal distance to firepoints while others don’t.

2.	Provide up to 5 key insights that you learned from this dataset. (Hint: Do not focus on statistical summaries. Consider focusing on groups and clusters and describing them)
1.	Many soil types are dominated by some cover types and many cover types grow exclusively on some soil types, for instance: 
o	Cover types 1 and 2 dominate many soil types, such as 22, 23, 24, 29, 32 etc.
o	Cover type 3 dominates soil types 4 and 6.
2.	Nearly all of cover type 7 are found in soil type 38, 39, and 40. Also type 7 grows exclusively in areas with very high elevation, which implies that soil types 38-40 appear frequently in high elevation areas.
3.	Cover type 4 tends to grow at very low elevation areas.
4.	Cover types 1 and 2 almost grow exclusively in wilderness areas 1 and 3.
5.	There is no pronounced difference between the means of vertical distance to hydrology and hillshade indices across 7 response categories.

3.	Highlight challenges in the dataset and the plans to mitigate those challenges (Hint: If there are missing data, how would you address this?)
-	The response variable is very unbalanced, some categories appear very few times comparing to other categories. Over representation of some categories might cause problems during classification. This is a limitation of the sample. Sampling a training set with approximately same number of response categories could potentially alleviate this problem.
-	There is high difference in the ranges of some quantitative variables. We would need to normalize the predictors if we want to use KNN model.


Modeling Strategy
1.	 What model(s) are you using and why?
-	Since we are classifying response into multiple categories,  random forest, KNN, and Naïve Bayes would be some appropriate models we could choose from.
-	I decided to go with random forest because it is intrinsically suited for multiclass classification, and it works well with a mixture of numerical and categorical features without the need of normalization.

2.	Describe (in detail) how each model was developed
I used random forest to construct the classification model, here are the steps I took.
-	Clean data.
-	Split data into training and testing sets.
-	Train the model.
-	Tuned the model and perform cross validation to search for optimal hyperparameters.
-	Score the resulting model with test set.
-	Analyze result with confusion matrix and feature importance chart.

Results
1.	Describe your model results. (Hint: It may be helpful to include tables or graphs)
-	The model with handpicked parameter scored a accuracy of 95.5 percent, while the cross-validated tuned model scored an accuracy of 80 percent. 
-	Looking at the confusion matrix, we can see that the model is not good at distinguishing cover types A and B. 
-	The feature importance chart shows that elevation is the most important in the process of classification, followed by distance to roadways.

2.	If more time were provided, what other strategies would you pursue? Why?
1.	I would try to construct different models and compare their performance.
2.	Try different sampling techniques when partitioning data into training and test set.
3.	When tuning the model, I couldn’t test more combinations of parameters due to constrains in time and computing power. I believe there are other parameters that could give better accuracies.
