Dataset

An excerpt of a dataset released to the public by Crunchbase.

#Business Understanding

The holy grail of venture capital investment is to invest in companies that either get acquired or issue an IPO. We consider 
two types of outcomes as successful: the startup issued an IPO (ipo) or it got acquired (is_acquired). A startup would not be 
considered successful, if it closed (is_closed) or none of the previous outcomes (ipo, is_acquired, or is_closed) occur.

#Benefit of the model to an investor

(i) Enables investors to make more informed decisions by providing them with tools to identify viable investment opportunities among early-stage companies.

(ii) Helps investors to understand the associated risks and make more accurate risk assessments when considering investment opportunities.

(iii) Provide investors with alternative investment strategies.

#Why is the lack of outcome in crunchbase a sign of failure?

(i) Failure or closure generally happens without any official announcement or regulatory filing.

(ii) Successful companies are more likely to be added to the Crunchbase data.

(iii) Indicates the lack of progress or failure to attract further investment.

#Data understanding and preparation

![image](https://github.com/abibatoki/Classification-Model/assets/149620766/f511b3d4-83de-4fc9-ba7b-30ee84946eaf)

#Prompt Used

Show the age distribution in years.

Use the age range interval of 1-5, 6-10, ..., and 36-40.

Title the chart Age Distribution inYears, label the y-axis Frequency, and x-axis Age Range.

#Remove all companies from the dataset that are older than 7 years or younger than 3 years of age. How many companies are there in the remaining data?

![Companies](https://github.com/abibatoki/Classification-Model/assets/149620766/72e21bbc-66f2-4f79-93a9-bed7e501e026)

