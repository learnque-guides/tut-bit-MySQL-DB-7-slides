# Merge / replace data?

For data merging we can use *INSERT ... ON DUPLICATE KEY* or *REPLACE ... ON DUPLICATE KEY*.

```sql
REPLACE table_name (col1, col2, col3)
    VALUES (2, 'val1', 'val2'),
    (3, 'val3', 'val4');

INSERT INTO table_name (col1, col2, col3)
    VALUES (1, 'val1', 'val2')
    ON DUPLICATE KEY UPDATE first_name = 'val1', last_name = 'val2';
```