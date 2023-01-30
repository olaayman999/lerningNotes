## what are sql union operator conditions 
The UNION operator in SQL is used to combine the results of two or more SELECT statements into a single result set. The main condition for using the UNION operator is that the number of columns and their data types must be the same in each SELECT statement.

For example, consider two SELECT statements:
```sql
SELECT name, location FROM employees;
SELECT department, location FROM departments;
```
By using the UNION operator, you can combine the results of these two SELECT statements:
```sql
SELECT name, location FROM employees
UNION
SELECT department, location FROM departments;
```
The result of this combined SELECT statement will be a single result set that includes all of the rows from both SELECT statements. The UNION operator removes any duplicates and returns unique rows only.

UNION ALL operator is similar to UNION, but it does not remove duplicates, so all rows are returned in the result set, even if they are duplicates.

if the condition is violated you will get the error:
```error
Error message: "The number of columns in the two SELECT statements do not match."
```
The following SQL statement returns the cities (only distinct values) from both the "Customers" and the "Suppliers" table:

```sql
SELECT City FROM Customers
UNION
SELECT City FROM Suppliers
ORDER BY City;
```
The following SQL statement returns the cities (duplicate values also) from both the "Customers" and the "Suppliers" table:

```sql
SELECT City FROM Customers
UNION ALL
SELECT City FROM Suppliers
ORDER BY City;
```

The following SQL statement returns the German cities (only distinct values) from both the "Customers" and the "Suppliers" table:

```sql
SELECT City, Country FROM Customers
WHERE Country='Germany'
UNION
SELECT City, Country FROM Suppliers
WHERE Country='Germany'
ORDER BY City;
```
The following SQL statement lists all customers and suppliers:
```sql
SELECT 'Customer' AS Type, ContactName, City, Country
FROM Customers
UNION
SELECT 'Supplier', ContactName, City, Country
FROM Suppliers
```
![image](https://user-images.githubusercontent.com/72671239/215508514-656bec3a-7950-496f-82a4-3c94e90bb5e5.png)

to determine number of conumns use:
```sql
UNION seleect NULL, NULL, NULL--
```
till there is no error returned

if you want to return only 1 colimn you can run
```sql
SELECT CONCAT(FIRSTNAME, ' ', LASTNAME) AS 'CUSTOMER NAME' FROM customer;
```
