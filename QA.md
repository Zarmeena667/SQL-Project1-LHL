What are your risk areas? Identify and describe them.

![image](https://github.com/Zarmeena667/SQL-Project1-LHL/assets/145514413/8fe89ca1-a1d6-4da3-875f-7f82084f0b44)

Queries used:

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


