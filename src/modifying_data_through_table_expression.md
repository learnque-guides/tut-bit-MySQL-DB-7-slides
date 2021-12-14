# Modifying data through join and table expressions


Examples:

```sql
UPDATE OD
  SET discount += 0.05
FROM dbo.OrderDetails AS OD
  INNER JOIN dbo.Orders AS O
    ON OD.orderid = O.orderid
WHERE O.custid = 1;
```

```sql
WITH C AS
(
  SELECT custid, OD.orderid,
    productid, discount, discount + 0.05 AS newdiscount
  FROM dbo.OrderDetails AS OD
    INNER JOIN dbo.Orders AS O
      ON OD.orderid = O.orderid
  WHERE O.custid = 1
)
UPDATE C
  SET discount = newdiscount;
```

```sql
UPDATE D
  SET discount = newdiscount
FROM (SELECT custid, OD.orderid,
        productid, discount, discount + 0.05 AS newdiscount
        FROM dbo.OrderDetails AS OD
        INNER JOIN dbo.Orders AS O
           ON OD.orderid = O.orderid
        WHERE O.custid = 1 ) AS D;
```