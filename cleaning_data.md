What issues will you address by cleaning the data?

DATA CLEANING

Data cleaning can be performed at two levels depending on the business rules defined: 
1.	Streamlining data when creating tables 
2.	Data cleaning/manipulation via queries

Cleaning strategies used

1. Columns with no data

Columns with no data can be removed
e.g., within all_sessions table the following columns have missing data
productRefundAmount
itemQuanity
itemRevenue
searchKeyword

One can parse data before importing CSV to the database which will also be required in order identify data type for each column within the table. These columns can be removed when creating table via CREATE TABLE query.

2. Missing data

Columns within tables have missing data e.g., timeonsite and revenue column within analytics table.
While querying data I also discovered that when the country column has (not set) data the product quantity is also null.
So I could confidently remove the not set countries when making queries with regards to product quantity


```sql
SELECT * 
FROM analytics 
WHERE timeonsite IS NULL
```



```sql
SELECT product quantity
FROM all_sessions
WHERE countries LIKE ‘(not set)’
```

3. Column names

The column names are not standardized to a single format. Camel case must be used to standardize column names. I prefer upper camel case when providing alias to table names. 

```sql
SELECT (type) as "Type", count(type) as "CountType"
FROM all_sessions
```

4. ProductSKU data type

The ProductSKU column does not have a consistent/uniform data type thereby creating data uniformity issues. 

```sql
SELECT ProductSKU 
FROM all_sessions;
```

5. Duplicate Values

There were duplicate values found in sales_by_sku table.

```sql
SELECT * 
FROM sales_by_sku
where productsku = 'GGOEYAXR066128'
```

6. Not set values that can be replaced

Replacing city with country where city data is not available in the all_sessions table

```sql
SELECT
       CASE WHEN city LIKE 'not available%' THEN country
            WHEN city LIKE '(not set)' THEN country
       Else city 
       END as "City", country as "Country", (transactionrevenue/100000) as "TransactionRevenue" 
FROM all_sessions
```




