# The CREATE TABLE ... SELECT statement

You can create one table from another by adding a SELECT statement at the end of the CREATE TABLE statement:

```sql
CREATE TABLE new_tbl [AS] SELECT * FROM orig_tbl;
```