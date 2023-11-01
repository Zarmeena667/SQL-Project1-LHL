# Final-Project-Transforming-and-Analyzing-Data-with-SQL


## Project/Goals

- Getting comfortable with large, unclean data sets. 
- Moving ahead from prescriptive defined questions to exploring data and drawing conclusions


## Process

![image](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/a70a9de8-0e49-49aa-b091-273b8f527482)

Steps followed: 

1. Data Exploration

- Identifying datatype to be assigned
- There must be a balance between allocating too much memory and too less e.g. name, page title etc.
- A high number of missing values e.g. revenue, transaction revenue etc. Must take into account when drawing any conclusions/drawinf insights.
- Identifying columns with inconsistent data format e.g. ProductSKU
- Columns with missing data

2. Data cleaning
- Used upper camel case for table columns could be assigned when querying
- Assessed which null values that can be replaced be existing values in another column e.g. country can replace city in the all_sessions table for missing cities depending on the nature of the analytics problem.
- Data cleaning is also defined by the business problem e.g. irrelevant data
- Data cleaning is iterative, it doesn’t stop at step 1 and I often found myself cleaning required data instead of cleaning the entire provided dataset.
- Creating clean tables from raw tables

3. Quality Assurance

- Validating/identifying potential Primary Keys by checking the column for duplicate or null values. 
- Checking if any of the existing columns are correlated? e.g. Is the product of units_sold and unit_price equal to the revenue?

4. Analysis

- Tried to maximize the use of different queries and techniques we’ve learned during the duration of the course



## Results
There were several queries run to identify trends and patterns which can be referred to in the project. However, I'd like to use this section to draw your attention to some interesting insights I found while working with data. 
1. Revenue was not equal to units sold and unit price. There were no other columns that would help me determine how this such data was evaluated.
2. What may potentially look like a primary key isn't necessarily one. For e.g. sku is not the primary key for the products table.


## Challenges 

1. No metadata or data dictionary provided therefore all results are based on assumptions about the data.
2. No business rules provided to be able to generate ERD with confidence
3. Data format inconsistency observed for ProductSKU and SKU columns
4. A huge chunk of missing data made me question the insights drawn from the data
5. Using upper camel case made it cumbersome to deal with some of the queries in Postgres such as window function where i didnot assign upper camel case aliases for column names. 



## Future Goals
- Due to time constraint I couldn't explore using stored procedures and views.
- I also wasn't able to showcase usage of user-defined functions for this project.
- I would also want to explore the data further and introduce constraints such as default and unique in order to streamline the data that can be inserted into a database.
- Need to focus on acquainting myself with Github. For the prepatory course I connected Github with AWS and wasn't able to use it for this assignment.
