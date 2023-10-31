Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:



Answer: 






**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:


```sql
---#1: Average productQuantity by country and city------
SELECT country, city, AVG(productQuantity) AS avg_product
FROM all_sessions
WHERE country NOT LIKE '(not set)' AND productQuantity IS NOT NULL
GROUP BY country, city
ORDER BY avg_product DESC

---#2: Average productQuantity by country ------
SELECT country, city, AVG(productQuantity) AS avg_product
FROM all_sessions
WHERE country NOT LIKE '(not set)' AND productQuantity IS NOT NULL
GROUP BY country, city
ORDER BY avg_product DESC
```
Answer: 


-------------------# Result 1-------------------



![image](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/16267d5a-8570-409c-a5b1-ec1fc9b9b899)



-------------------# Result 2-------------------


![image](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/ba8c1411-ca64-473f-a8d6-d9f4256f1b38)


**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:  

```sql
---------------#1 count by type-----------
SELECT (type) as "Type", count(type) as "CountType"
FROM all_sessions
WHERE country NOT LIKE '(not set)'
Group by type

-------------#2 Top 5 orders placed for PAGE type product by country------
SELECT country as "Country", type as "Type", count(type) as "CountType"
FROM all_sessions
WHERE country NOT LIKE '(not set)' AND type = 'PAGE'
Group by country,type
ORDER BY count(type) DESC
limit 5 
-----------#3 Top 5 orders placed for Event type product by country------
SELECT country as "Country", type as "Type", count(type) as "CountType"
FROM all_sessions
WHERE country NOT LIKE '(not set)' AND type = 'EVENT'
Group by country,type
ORDER BY count(type) DESC
limit 5
```

Answer: 

---------- Result 1-----------------

![image](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/fd68ad7b-b788-4232-aaa0-e854636cdb3f)


--------Result 2 ------------------

![image](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/a0ea6cad-3f62-4871-9af8-d92d002957da)


---------Result 3------------------

![image](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/793987d9-ecab-474e-bffd-5512424c9b2c)









**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







