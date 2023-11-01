Question 1: The site received the highest number of page views on which date? 

SQL Queries:
```sql 
SELECT DISTINCT (fullvisitorid), 
       pageviews as "PageViews", 
        to_date(date::text, 'YYYYMMDD') as "Date" from all_sessions 
ORDER BY "PageViews" DESC
LIMIT 1
```


Answer: 

![image](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/e76baf0c-001c-467b-b967-b424b48029a8)


Question 2: What is the average of ordered quantity with lowest sentiment score?

SQL Queries: 

```sql
SELECT name AS "Name" , AVG(orderedquantity) as "Average", sentimentscore as "SentimentScore"
FROM Products
GROUP BY name, sentimentscore
ORDER BY
```

Answer:


![image](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/2b136dbb-433a-4c65-8290-b6831e4e1f05)


Question 3: Top three channel groupings that have highest amount of sold units?

SQL Queries: ```sql
SELECT sum(units_sold) as "SumUnitsSold", channelgrouping as "ChannelGrouping"
FROM analytics A
WHERE units_sold IS NOT NULL
GROUP BY channelgrouping
ORDER BY "SumUnitsSold" DESC
```

Answer:


![image](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/d42d054b-fefd-4567-a57b-e6ea0b366772)



Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
