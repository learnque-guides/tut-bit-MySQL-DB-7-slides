# Exercise 1

Execute code

```sql
DROP TABLE IF EXISTS CustomersWithOrders;

CREATE TABLE CustomersWithOrders
(
  custid      INT         NOT NULL PRIMARY KEY,
  companyname VARCHAR(40) NOT NULL,
  country     VARCHAR(15) NOT NULL,
  region      VARCHAR(15) NULL,
  city        VARCHAR(15) NOT NULL
);
```

Insert into the *CustomersWithOrders* table a row with the following information:

* custid: 100
* companyname: Coho Winery
* country: USA
* region: WA
* city: Redmond

Insert into the *CustomersWithOrders* table all customers who placed orders.

Tables involed: *Orders*, *Customers*, *CustomersWithOrders*
