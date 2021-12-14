# The INSERT INTO statement

* The INSERT INTO statement is a standard SQL statement that creates populates a target table with the result set of a query.

```sql
INSERT INTO tbl_temp2 (fld_id)
    SELECT tbl_temp1.fld_order_id
    FROM tbl_temp1 WHERE tbl_temp1.fld_order_id > 100;
```

Think about INSERT INTO like a `copy paste`

The target table’s structure and data must be based on the source table. The INSERT INTO statement copies from the source to the target.
