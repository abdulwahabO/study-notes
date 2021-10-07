## SQL

SQL is a declarative language used to manage data stored in a relational database system. It consists of a
Data Definition Language, a Data Manipulation Language and a Data Control Language.

## Query, Sort & Filter

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

This query returns only 10 rows starting with the fifth row in the result set. `LIMIT` can be used without an offset clause in which case the result set starts at the very first row.

The `LIMIT` clause is not an SQL standard even though many databases support it. The SQL standard introduced a `FETCH` clause which performs the same function as `LIMIT OFFSET`.


##### The `WHERE` appears immediately after the `FROM` clause and specifies conditions that must be true for a row to be included in the result set.

The `WHERE` clause can be used with comparison operators like `=`, `>`, `!=`, and logical operators like `EXISTS`, `AND` and `BETWEEN`. E.g

```sql
SELECT * FROM invoice WHERE create_date BETWEEN '2016-1-1' AND '2017-11-11'
```

The Above includes only rows in the specified range for `create_date`

##### SQL defines a few logical operators for testing if a condition is true:

* `AND` and `OR` - These operators allow multiple conditions to be comibed in a `WHERE` clause.
```sql
SELECT * FROM invoices WHERE create_date > '2020-12-1' AND customer_id = 'cus_21221';
SELECT * FROM invoices WHERE customer_name = 'Adeshina' OR customer_name = 'Ogunmodede';
```

* `IS NULL` - As the name implies, this is a check for null values. 
```sql
SELECT * FROM invoices WHERE phone_number IS NULL;
```

* `IN` - This operator allows for specifying multiple values in a `WHERE` clause. This is a shorthand for using `OR`. The SQL statement below will return all rows where 'customer_name' is 'Adeshina' or 'Bilikisu'
```sql
SELECT * FROM invoices WHERE customer_name IN ('Adeshina','Bilikisu');
```

* `LIKE` - This operator is used in a `WHERE` clause to search for patterns in a column.
Two wildcards often used with this operator are '%' and '_', which match zero or multiple characters and a single character respectively. The SQL statement below returns all rows where customer name contains 'Ade'.
```sql
SELECT * FROM invoices WHERE customer_name LIKE '%Ade%'
```

## Joins.

* An `Inner Join` can be thought of as an intersection. An inner join links two or more tables using a relationship between two columns. The join condition is specified using the `ON` keyword. E.g
```sql
SELECT invoices.create_date, customers.location FROM invoices INNER JOIN customers ON invoice.customer_id = customers.id WHERE invoices.create BETWEEN '2021-11-11' AND '2020-11-11';
```
Inner Join can join two or more tables as long as there are relationships between them e.g foreign keys.

* A `LEFT JOIN` returns all the records from the left table and matching records from the right table.
If no records from the left table match, then the result set consists of the records from the left table.

* A `FULL JOIN` returns all records where there is a match in either table.

## Aggregate Functions.

* Aggregate functions operate on a set of values and are often used with the `GROUP BY` clause.
The most common aggregate functions are `AVG(..)` which returns the average value of numeric column, `COUNT(..)` which returns the number of rows in a resut set, `SUM(..)` which returns the sum of all the values in a column, `MIN(..)`, `MAX(..)`.

## Grouping Data

* The `GROUP BY` clause is used in `SELECT` statements to group rows based on a column. An aggregate function is then applied to return a row for each group.
```sql
SELECT AVG(price) as price_avg, product_name FROM products GROUP BY product_name;
```

_TODO: Practice grouping and applying aggregate functions on a real DB._

_TODO: Learn about stored procedures, triggers, EXPLAIN and views._

## SQL Practice: Prognoreport DB query problems.

1. Show how many sales each company has made in Naira.
2. Show every sale whose total amount is higher than the average total amount.
3. Show the average amount spent by each company on sales.
4. Show the payment_fact(s) whose currency is cash.
5. Get the top 10 sales above 5k naira.
6. Find the top 10 payment_facts (in terms of amount) below 1000.0 created between 2018 and 2019
7. Find all products whose description includes `od`.
8. _DO some practice with GROUP BY and aggregate functions_


