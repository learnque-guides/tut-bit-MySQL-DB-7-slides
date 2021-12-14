# The CREATE TABLE ... LIKE statement

Use CREATE TABLE ... LIKE to create an empty table based on the definition of another table, including any column attributes and indexes defined in the original table:

```sql
CREATE TABLE new_tbl LIKE orig_tbl;
```