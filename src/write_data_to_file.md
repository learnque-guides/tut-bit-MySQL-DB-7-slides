# Exporting Data to Comma-Delimitted Files

You can export file to csv file as well:

```sql
SELECT *
    FROM Employees JOIN Orders O on Employees.empid = O.empid
    INTO OUTFILE 'employees.csv'
    FIELDS TERMINATED BY ',';
```

It is better to use commandline utils

```bash
mysql -uroot -padmin -e'USE lessons; SELECT * FROM Orders;' > test.csv
```

If you want to export / backup all database you can use:

```bash
mysqldump -uroot -padmin lessons
```

[https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
