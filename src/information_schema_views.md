# Information schema views

An information schema view is a set of views that resides in a schema called INFORMATION_SCHEMA and provides metadata information in a standard manner.

```sql
SELECT TABLE_SCHEMA, TABLE_NAME
FROM INFORMATION_SCHEMA.TABLES
WHERE TABLE_TYPE = N'BASE TABLE';
```

```sql
SELECT
  COLUMN_NAME, DATA_TYPE, CHARACTER_MAXIMUM_LENGTH,
  COLLATION_NAME, IS_NULLABLE
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_SCHEMA = N'Sales'
  AND TABLE_NAME = N'Orders';
```