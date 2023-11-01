What are your risk areas? Identify and describe them.

![image](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/8fe89ca1-a1d6-4da3-875f-7f82084f0b44)

Queries used:


IDENITIFYING PRIMARY KEYS
Query 1. 
```sql
SELECT * 
FROM all_sessions
```
This query retrieves a result set for about 15134 rows

Query 2.

``` sql
   SELECT * 
   FROM all_sessions 
   WHERE fullvisitorid IS NULL
```
This query retrieves no result meaning there are no fullvisitorid values that are null.

Query 3.

```sql
    SELECT distinct fullvisitorid
    FROM all_sessions
```
This query retrieves a result set of 14223 values. 


This test proves that there are duplicate values in the fullvisitorid column and therefore it cannot be the primary key to the sessions table. 

I conducted a similar test for analytics table which also contains the fullvisitorid column. There were about 4301122 rows of which only 120018 had unique values and there were no nulls. Thereby I concluded that this column cannot serve the primary key for analytics table. 

I didn’t add auto incrementing primary keys to the table as I didn’t feel the need and thought I’d be able to do that better if I have the business rule for database design. 

I didn’t add auto incrementing primary keys to the table as I didn’t feel the need and thought I’d be able to do that better if I have the business rule for database design.

A similar test was performed for products table, sales_by_sku and sales_report.





NULL VALUES

```sql
SELECT * 
FROM all_sessions
where totaltransactionrevenue is NULL
```

There are about 15053 of 15134 rows where totaltransactionrevenue is null. Any deductions made using this column should be considered with caution. The data is not enough to draw any tangible conclusions and/or insights. 

CONSTRAINTS

Looking at the data, I assumed that sku is the primary key in the products table that is being referenced as foreign key in the sales_by_sku and sales_report table. However, upon running the following queries I came to realize that is not the case.

```sql

SELECT * 
FROM products
WHERE sku = 'GGOEYAXR066128'

SELECT * 
FROM sales_by_sku
WHERE productsku = 'GGOEYAXR066128'

SELECT * 
FROM sales_report
WHERE productsku = 'GGOEYAXR066128'
```

The default constraint can be used to enforce a constraint on a particular column e.g. if we want to format SKU to contain dashes. 

RELATION BETWEEN EXISTING COLUMNS

```sql

SELECT
    revenue/100000 as "Revenue", 
    (cast((a.units_sold) * (a.unit_price/100000) as float)) as "ProductPrice"
FROM analytics a
Where revenue IS NOT NULL

```


