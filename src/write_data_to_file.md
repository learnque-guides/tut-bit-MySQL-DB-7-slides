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