# Sequence

In MySQL, a sequence is a list of integers generated in the ascending order i.e., 1, 2, 3...

To create a sequence in MySQL automatically, you set the AUTO_INCREMENT attribute for a column, which typically is a primary key column.

The following rules are applied when you use the AUTO_INCREMENT attribute:

* Each table has only one AUTO_INCREMENT column whose data type is typically the integer.
* The  AUTO_INCREMENT column must be indexed, which means it can be either PRIMARY KEY or UNIQUE index.
* The AUTO_INCREMENT column must have a NOT NULL constraint. When you set the AUTO_INCREMENT attribute to a column, MySQL automatically adds the NOT NULL  constraint to the column implicitly.

It is not possible to create a cusomt sequence like in MSSQL or Oracle or PostgreSQL:

```sql
CREATE SEQUENCE [dbo].[SeqMaxOrderId] AS INT
  MINVALUE 1,
  MAXVALUE 10
  CYCLE; -- Reset to min value after max value reached
```

We can use the LAST_INSERT_ID() function to get the last generated sequence number. However, we can also use the last insert ID for the subsequent statements that should be unique across sessions.
