## SQL injection examples

There are a wide variety of SQL injection vulnerabilities, attacks, and techniques, which arise in different situations. Some common SQL injection examples include:

 1. Retrieving hidden data, where you can modify an SQL query to return additional results.
 ``` sql
 SELECT * FROM products WHERE category = 'Gifts' OR 1=1--' AND released = 1
 ```
 
 2. Subverting application logic, where you can change a query to interfere with the application's logic.
 
 ```sql
 SELECT * FROM users WHERE username = 'administrator'--' AND password = ''
 ```
 
 3. UNION attacks, where you can retrieve data from different database tables.
 ```sql
 SELECT name, description FROM products WHERE category = '' UNION SELECT username, password FROM users--
 ```
 
 4. Examining the database, where you can extract information about the version and structure of the database.

 5. Blind SQL injection, where the results of a query you control are not returned in the application's responses.
 
 ##how to know if a login page is vulnerable to sql injection
There are several ways to check if a login page is vulnerable to SQL injection:

1. Manual testing - by manually entering SQL injection payloads in the login form fields

2. Using automated tools - such as sqlmap, which can automatically detect and exploit SQL injection vulnerabilities.

3. Code Review - reviewing the source code of the application looking for any signs of SQL injection vulnerabilities, such as the use of unsanitized user input in SQL queries.

4. Testing with a web vulnerability scanner - like Nessus, Acunetix or Burp Suite.

It's important to note that an absence of vulnerability does not guarantee the security of the application against SQL injection, so regular penetration testing and security reviews are recommended.

##what are database types used in businesses 
There are several different types of databases that are commonly used in businesses, including:

1. Relational databases: The most widely used database system, relational databases store data in tables with rows and columns. Examples include MySQL, Oracle, and Microsoft SQL Server.

2. NoSQL databases: These databases do not use the traditional table-based relational model, instead they use a variety of data models such as key-value, document, columnar and graph. Examples include MongoDB, Cassandra, and Redis.

3. Graph databases: They store data in nodes and edges, and are particularly good for handling complex relationships between data. Examples include Neo4j, Amazon Neptune, and ArangoDB.

4. Time-series databases: They are optimized for handling time-stamped data, and are commonly used for monitoring, logging, and IoT applications. Examples include InfluxDB and OpenTSDB

5. In-memory databases: These databases store data in RAM, which allows for very fast data access. Examples include SAP HANA and Oracle TimesTen.

These databases are not mutually exclusive and some businesses use more than one type of database depending on the use case.

The choice of database type depends on the specific needs of the business and the application being developed. Some databases are better suited for handling large amounts of data, while others are better for handling complex relationships between data.

## Examining the DB

The SQL statement 
```sql 
SELECT * FROM information_schema.tables
```
is used to retrieve information about tables in a database. The "information_schema" is a database in its own right within the SQL database management system, and it contains information about all the other databases, tables, views, columns, and other metadata in the system.

The "tables" table within the "information_schema" database contains information about all the tables within the database, such as their names, schemas, types, etc.

So, when you run the query "SELECT * FROM information_schema.tables", you will get a list of all the tables in the database, along with information about each table, such as its name, schema, type, etc. This information can be useful for troubleshooting, database administration, and for gaining a better understanding of the database structure.
