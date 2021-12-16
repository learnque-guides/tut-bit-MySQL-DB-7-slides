# Exercise 5

By using CREATE TABLE ... SELECT statement create a copy of *Customers* table. Name it as *CustomersForUpdate*

Run the following query against *CustomersForUpdate*, and notice that some rows have a NULL in the region column:

```sql
SELECT * FROM CustomersForUpdate;
```

The output from this query is as follows:

```sql
custid      companyname      country         region     city
----------- ---------------- --------------- ---------- ---------------
1           Customer NRZBB   Germany         NULL       Berlin
2           Customer MLTDN   Mexico          NULL       México D.F.
3           Customer KBUDE   Mexico          NULL       México D.F.
4           Customer HFBZG   UK              NULL       London
5           Customer HGVLZ   Sweden          NULL       Luleå
6           Customer XHXJV   Germany         NULL       Mannheim
7           Customer QXVLA   France          NULL       Strasbourg
8           Customer QUHWH   Spain           NULL       Madrid
9           Customer RTXGC   France          NULL       Marseille
10          Customer EEALV   Canada          BC         Tsawassen
...

(90 row(s) affected)
```

Update the *CustomersForUpdate* table, and change all NULL region values to <None>.
