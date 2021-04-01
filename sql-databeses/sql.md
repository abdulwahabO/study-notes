### SQL

SQL is a declarative language used to manage data stored in a relational database system. It consists of a
Data Definition Language, a Data Manipulation Language and a Data Control Language.

### Query, Sort & Filter

##### The `SELECT` statement is used to query data from a table. It supports selecting columns, grouping data, joining tables and performing simple calculations. The `ORDER BY` clause is used to specify the order in which the result set should be sorted.

```sql
SELECT * FROM customers ORDER BY age DESC, first_name ASC;
```

* The above statement retrieves all the columns of the customer table and first orders them such that for any two rows the one with a higher value for age is placed at the top, and if they have the same age then they are sorted using the characters of the first name field in ascending alphabetical order.

##### The `DISTINCT` clause will ensure only rows with unique values for the specified columns are returned.

```sql
SELECT DISTINCT last_name, salary, age FROM staff ORDER BY age DESC; 
```

* The above statement ensures that no row has non-unique values for the listed columns.

##### The `LIMIT OFFSET` clause specifies the max number of rows a query should return and the row at which to start from. 

```sql
SELECT * FROM customers LIMIT 10 OFFSET 4;
```

* This query returns only 10 rows starting with the fifth row in the result set. `LIMIT` can be used without an offset clause in which case the result set starts at the very first row.

* The `LIMIT` clause is not an SQL standard even though many databases support it. The SQL standard introduced a `FETCH` clause which performs the same function as `LIMIT OFFSET`.



### Aggregate Functions



### Joins


### Grouping Data


### Update





### Stored Procedures. Functions and Views.





## SQL Practice: Prognoreport DB query problems.

1. Show how many sales each company has made in Naira.
2. Show every sale whose total amount is higher than the average total amount.
3. Show the average amount spent by each company on sales.
4. Show the payment_fact(s) whose currency is cash.
5. Get the top 10 sales above 5k naira.
6. 



