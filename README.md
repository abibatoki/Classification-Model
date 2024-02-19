Dataset

An excerpt of a dataset released to the public by Crunchbase.

#Business Understanding

The holy grail of venture capital investment is to invest in companies that either get acquired or issue an IPO. We consider 
two types of outcomes as successful: the startup issued an IPO (IPO) or it got acquired (is_acquired). A startup would not be 
considered successful if it closed (is_closed) or none of the previous outcomes (IPO, is_acquired, or is_closed) occur.

#Benefit of the model to an investor

(i) Enables investors to make more informed decisions by providing them with tools to identify viable investment opportunities among early-stage companies.

(ii) Helps investors to understand the associated risks and make more accurate risk assessments when considering investment opportunities.

(iii) Provide investors with alternative investment strategies.

#Why is the lack of outcome in Crunchbase a sign of failure?

(i) Failure or closure generally happens without any official announcement or regulatory filing.

(ii) Successful companies are more likely to be added to the Crunchbase data.

(iii) Indicates the lack of progress or failure to attract further investment.

#Data understanding and preparation

![image](https://github.com/abibatoki/Classification-Model/assets/149620766/f511b3d4-83de-4fc9-ba7b-30ee84946eaf)

#Prompt Used

Show the age distribution in  years.

Use the age range interval of 1-5, 6-10, ..., and 36-40.

Title the chart Age Distribution in Years, label the y-axis Frequency, and x-axis Age Range.


#Remove all companies from the dataset that are older than 7 years or younger than 3 years of age. How many companies are there in the remaining data?

![Companies](https://github.com/abibatoki/Classification-Model/assets/149620766/72e21bbc-66f2-4f79-93a9-bed7e501e026)

#Create a new target variable (success) with two values: 1 for success and 0 for failure.

#Target variable: 'Success'

I created a new target variable ‘Success’ based on the assumption that companies that went for an IPO or got acquired during the period were successful.
It was encoded as a binary variable using the ‘ipo’ or ‘is_acquired’ column.

#Create the 'Success' variable (Success: 1, Failure: 0)

df['Outcome'] = ((df['ipo'] df['is_acquired']).astype(int)

![image](https://github.com/abibatoki/Classification-Model/assets/149620766/a471abbe-5c59-4c52-a977-ca7f58aaca04)

#Combine the features related to the education levels of the founders (mba_degree, phd_degree, ms_degree, other_degree) 
into a new feature for the total number of degrees obtained by the founders (number_degrees)

![Degrees](https://github.com/abibatoki/Classification-Model/assets/149620766/d8471595-5385-45fb-a895-5506829a81f0)

#Numerical features in the dataset

(i) Average_Funded: average funding per round

(ii) Average_Participants: average participants per round

(iii) Acquired_Companies: number of acquired companies

(iv) Age_in_years: age of the company

(v) Number_of_degrees: total number of degrees obtained by company founders

(vi) Offices: number of offices

(vii) Products_number: number of products

(viii) Total_rounds: total number of funding rounds

![Numerical](https://github.com/abibatoki/Classification-Model/assets/149620766/2e922bd9-684a-4797-a220-57fb27ae9cb7)

#Correlations of the numerical features with one another and the target in a heatmap.

![Final Heatmap](https://github.com/abibatoki/Classification-Model/assets/149620766/59ee52f3-ba5e-4fef-85a4-18aab1eba2b1)

#comment on the heatmap

The features are not highly correlated with one another. There may be a need for feature engineering, given the low correlation. To
improve the model's predictive capability, we may need to create new features, change existing ones, or collect additional data.

#Identify the categorical features in the dataset and explain what you need to do with the categorical features before you can use 
them in the model?

#Categorical features

(i) country_code
(ii) state_code
(iii) category_code

To use them in the model, they have to be encoded using one-hot encoding to create a new column for each value of the feature and
set the value to 1 if the feature has that value.

#Missing values count and missing value ratio

![Miss Ratio](https://github.com/abibatoki/Classification-Model/assets/149620766/3b382864-232b-4417-8317-9637e10603e6)

MODELING

#Training and test data

To split the dataset into training and test datasets, I used the train_test_split function from scikit-learn using the 80/20 ratio.

#Processed data

![Pre-processed data](https://github.com/abibatoki/Classification-Model/assets/149620766/93734c6e-9d3e-4e24-8735-76d5c503d04e)

#Logistics regression model

![image](https://github.com/abibatoki/Classification-Model/assets/149620766/5929f578-621b-4e19-b52b-b870cf3b5265)

#Random forest model

![image](https://github.com/abibatoki/Classification-Model/assets/149620766/d13f168d-a28f-468e-a1dc-16748dc43e57)

#Interpretation of result

While the Random Forest model was 100% accurate for the given dataset, there is a possibility that it might be overestimated.
The logistic regression model, with an accuracy of approximately 91.87%, seems to be more balanced and can be applied to new data more easily.
It's essential to consider how well these models will perform on new, unseen data (i.e., test them on a different dataset) to ensure they generalize well and
do not overfit.

Accuracy is high, but the precision and recall for the '1' class are very low, indicating that the model is not effective in identifying successful cases.
For an investor, the ability to make informed decisions depends on the precision and recall for the positive class. Therefore, this model's performance may not be satisfactory for investment decisions.

#Dealing with imbalanced data using a resampling technique

![image](https://github.com/abibatoki/Classification-Model/assets/149620766/6e5aab0e-62ad-4080-8f21-4e14a93f12c6)

#Using stratified k-fold cross-validation to evaluate the model

STRATIFIED K-FOLD (LOGISTIC REGRESSION)

Accuracy for Fold 1: 0.9160021265284424

Accuracy for Fold 2: 0.9160021265284424

Accuracy for Fold 3: 0.9164893617021277

Accuracy for Fold 4: 0.9159574468085107

Accuracy for Fold 5: 0.9159574468085107

Average Cross-Validation Accuracy: 0.916081701675206

STRATIFIED K-FOLD (RANDOM FOREST)

Accuracy for Fold 1: 1.0

Accuracy for Fold 2: 1.0

Accuracy for Fold 3: 1.0

Accuracy for Fold 4: 1.0

Accuracy for Fold 5: 1.0

Average Cross-Validation Accuracy: 1.0

#Evaluating the model against the test dataset

![image](https://github.com/abibatoki/Classification-Model/assets/149620766/aee73e2e-f724-4414-a79d-5f2983fa1dc5)

#Interpretation

The F1-score of 1.0 for the Random Forest model suggests that it achieved perfect precision and recall on the test set.
An F1-score of 0.880 for the Logistic Regression model indicates a harmonic mean of precision and recall that is less than perfect. The Logistic Regression model might be performing well, but not as well as the Random Forest model in terms of precision and recall on this specific test data.












