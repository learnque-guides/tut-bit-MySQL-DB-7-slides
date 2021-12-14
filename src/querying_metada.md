# Querying metadata

MySQL Server provides statements for getting information about the objects, such as information about tables in a database and columns in a table. Those tools include information schema views, and specific non standart sql statements.

## Non standart sql statements

```sql
SHOW DATABASES;
SHOW TABLES;
DESCRIBE table_name;
SHOW COLUMNS FROM table_name;
SHOW WARNINGS;
```

## information schema views

INFORMATION_SCHEMA is a database within each MySQL instance, the place that stores information about all the other databases that the MySQL server maintains.

```sql
SELECT table_name, table_type, engine
    FROM information_schema.tables
    WHERE table_schema = 'lessons'
    ORDER BY table_name;
```
