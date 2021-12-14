# Window functions

A window function is a function that, for each row, computes a scalar result value based on a calculation against a subset of the rows from the underlying query.

MySQL supports window functions that, for each row from a query, perform a calculation using rows related to that row.

More detailed describtion:

[https://dev.mysql.com/doc/refman/8.0/en/window-function-descriptions.html](https://dev.mysql.com/doc/refman/8.0/en/window-function-descriptions.html)

Let's look at MySQL examples:

[https://dev.mysql.com/doc/refman/8.0/en/window-functions-usage.html](https://dev.mysql.com/doc/refman/8.0/en/window-functions-usage.html)

```sql
SELECT empid, ordermonth, val,
  SUM(val) OVER(PARTITION BY empid
                ORDER BY ordermonth) AS runval
FROM EmpOrders;
```

```sql
SELECT empid, ordermonth, val, SUM(val), AVG(val)
FROM EmpOrders
GROUP BY empid, ordermonth, val
ORDER BY ordermonth;
```

One of the great advantages of window functions is that they don’t hide the detail. This means you can write expressions that mix detail and aggregates. The next example demonstrates this:

```sql
SELECT orderid, custid, val,
  100 * val / SUM(val) OVER() AS pctall,
  100 * val / SUM(val) OVER(PARTITION BY custid) AS pctcust
FROM OrderValues;
```

Other example:

```sql
SELECT
         orderdate,
            freight,
         ROW_NUMBER()   OVER(PARTITION BY YEAR(orderdate)) AS 'row_number',
         SUM(freight)   OVER(PARTITION BY YEAR(orderdate)) AS 'total_freight_for_order_year'
       FROM Orders
ORDER BY orderdate;
```