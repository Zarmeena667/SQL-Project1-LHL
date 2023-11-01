Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries: 
```sql 
SELECT
       CASE WHEN city LIKE 'not available%' THEN country
            WHEN city LIKE '(not set)' THEN country
       Else city 
       END as "City", country as "Country", (transactionrevenue/100000) as "TransactionRevenue" 
FROM all_sessions
WHERE transactionrevenue IS NOT NULL
ORDER BY "TransactionRevenue" DESC
```



Answer: 

![image](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/7f59621a-be81-45b7-9c5b-aa11b011ae4d)



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

```sql
---------- #4 Top-selling product from each country---------
SELECT * 
FROM (
SELECT
distinct(s.v2productname),
s.country, 
sr.total_ordered, 
(rank() over (partition by s.country order by sr.total_ordered desc)) as rank_orders
FROM all_sessions s
JOIN sales_report sr
ON s.productsku = sr.productsku) x
WHERE x.rank_orders = 1 and country != '(not set)'
ORDER BY country ASC
```


Answer:

![image](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/a048cb3c-95bb-4573-947e-9ce7676e4e4b)




**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:

```sql
SELECT
    s. country, 
    SUM(cast((a.units_sold) * (a.unit_price/100000) as float)) as revenue_impact
FROM analytics a
JOIN all_sessions s
ON s.fullvisitorid = a.fullvisitorid
WHERE units_sold IS NOT NULL
GROUP BY country
ORDER BY revenue_impact DESC
limit 10
```

Answer:

![image](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/2ba10e09-8a5d-4fe2-8d12-549aab4e47ce)








