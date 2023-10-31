Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:

![Screenshot 2023-10-31 135655](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/94c922a6-1e92-4fb1-bc18-7a063cd6b4e3)


Answer: 






**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:

```sql
SELECT country, city, AVG(productQuantity) AS avg_product
FROM all_sessions
WHERE country NOT LIKE '(not set)' AND productQuantity IS NOT NULL
GROUP BY country, city
ORDER BY avg_product DESC







**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:

Answer: 





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







