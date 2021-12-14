# Exercise 2

```sql
DROP TABLE IF EXISTS Orders2014_2016;

CREATE TABLE Orders2014_2016
(
    orderid        int                         not null,
    custid         int                         null,
    empid          int                         not null,
    orderdate      date                        not null,
    requireddate   date                        not null,
    shippeddate    date                        null,
    shipperid      int                         not null,
    freight        decimal(10, 2) default 0.00 not null,
    shipname       varchar(40) charset utf8mb3 not null,
    shipaddress    varchar(60) charset utf8mb3 not null,
    shipcity       varchar(15) charset utf8mb3 not null,
    shipregion     varchar(15) charset utf8mb3 null,
    shippostalcode varchar(10) charset utf8mb3 null,
    shipcountry    varchar(15) charset utf8mb3 not null
);
```

Use a *INSERT INTO* statement to populate the *Orders2014_2016* table with orders from the *Orders* table that were placed in the years 2014 through 2016.
