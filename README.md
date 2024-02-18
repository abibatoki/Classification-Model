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

#Identifying the numerical features in the dataset

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

