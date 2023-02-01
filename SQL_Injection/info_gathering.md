## database information gathering
This includes the type and version of the database software, and the contents of the database in terms of which tables and columns it contains.
## Database version
You can query the database to determine its type and version. This information is useful when formulating more complicated attacks.

```sql
Oracle	    SELECT banner FROM v$version
            SELECT version FROM v$instance
            
Microsoft   SELECT @@version
PostgreSQL  SELECT version()
MySQL       SELECT @@version
```

## Listing the contents of the database
Most database types (with the notable exception of Oracle) have a set of views called the information schema which provide information about the database.

You can query information_schema.tables to list the tables in the database:
```sql
SELECT * FROM information_schema.tables
```
```text
TABLE_CATALOG  TABLE_SCHEMA  TABLE_NAME  TABLE_TYPE
=====================================================
MyDatabase     dbo           Products    BASE TABLE
MyDatabase     dbo           Users       BASE TABLE
MyDatabase     dbo           Feedback    BASE TABLE
```

You can then query information_schema.columns to list the columns in individual tables:
```sql
SELECT * FROM information_schema.columns WHERE table_name = 'Users'
```

```text
TABLE_CATALOG  TABLE_SCHEMA  TABLE_NAME  COLUMN_NAME  DATA_TYPE
=================================================================
MyDatabase     dbo           Users       UserId       int
MyDatabase     dbo           Users       Username     varchar
MyDatabase     dbo           Users       Password     varchar
```

## Database contents
You can list the tables that exist in the database, and the columns that those tables contain.
```sql
Oracle        SELECT * FROM all_tables
              SELECT * FROM all_tab_columns WHERE table_name = 'TABLE-NAME-HERE'
              
others        SELECT * FROM information_schema.tables
              SELECT * FROM information_schema.columns WHERE table_name = 'TABLE-NAME-HERE'
```
