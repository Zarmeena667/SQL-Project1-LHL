Question 1: The site received the highest number of page views on which date? 

SQL Queries:
```sql 
SELECT DISTINCT (fullvisitorid), 
       pageviews as "PageViews", 
        to_date(date::text, 'YYYYMMDD') as "Date" from all_sessions 
Order by "PageViews" DESC
```


Answer: 



Question 2: 

SQL Queries:

Answer:



Question 3: 

SQL Queries:

Answer:



Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
