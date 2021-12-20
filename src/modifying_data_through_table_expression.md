# Modifying data through join

Example:

```sql
UPDATE OrderDetails AS OD
  INNER JOIN Orders AS O
  ON OD.orderid = O.orderid
SET discount = discount + 0.05
WHERE O.custid = 1;
```