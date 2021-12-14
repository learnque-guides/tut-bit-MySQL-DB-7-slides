# Catalog views

Catalog views provide detailed information about objects in the database, including information that is specific to SQL Server. 

```sql
SELECT SCHEMA_NAME(schema_id) AS table_schema_name, name AS table_name
FROM sys.tables;
```

To get information about columns in a table, you can query the sys.columns table.

```sql
SELECT
  name AS column_name,
  TYPE_NAME(system_type_id) AS column_type,
  max_length,
  collation_name,
  is_nullable
FROM sys.columns
WHERE object_id = OBJECT_ID(N'Sales.Orders');
```
