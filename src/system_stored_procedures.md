# System stored procedures and functions

System stored procedures and functions internally query the system catalog and give you back more "digested" metadata information.

The sp_tables stored procedure returns a list of objects (such as tables and views) that can be queried in the current database.

```sql
EXEC sp_tables;
```

The sp_help procedure accepts an object name as input and returns multiple result sets with general information about the object, and also information about columns, indexes, constraints, and more.

```sql
EXEC sys.sp_help
  @objname = N'Sales.Orders';
```

The sp_columns procedure returns information about columns in an object. For example, the following code returns information about columns in the Orders table

```sql
EXEC sys.sp_columns
  @table_name = N'Orders',
  @table_owner = N'Sales';
```

The sp_helpconstraint procedure returns information about constraints in an object.

```sql
EXEC sys.sp_helpconstraint
  @objname = N'Sales.Orders';
```

More examples for getting information regarding MSSQL:

```sql
SELECT
  SERVERPROPERTY('ProductLevel');

SELECT
  DATABASEPROPERTYEX(N'TSQLV4', 'Collation');

SELECT
  OBJECTPROPERTY(OBJECT_ID(N'Sales.Orders'), 'TableHasPrimaryKey');

SELECT
  COLUMNPROPERTY(OBJECT_ID(N'Sales.Orders'), N'shipcountry', 'AllowsNull');
```

More info and examples:

[https://docs.microsoft.com/en-us/sql/relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq?view=sql-server-ver15#_FAQ31](https://docs.microsoft.com/en-us/sql/relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq?view=sql-server-ver15#_FAQ31)