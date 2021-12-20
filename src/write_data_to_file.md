# Exporting Data to Comma-Delimitted Files

You can export file to csv file as well:

```sql
SELECT emp_no, first_name, last_name, title, from_date
    FROM employees JOIN titles USING (emp_no)
    WHERE title = 'Manager' AND to_date = '9999-01-01'
    INTO OUTFILE '/var/lib/mysql-files/managers.csv'
    FIELDS TERMINATED BY ',';
```