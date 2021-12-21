# Loading Data from Comma-Delimited Files

You use the *LOAD DATA INFILE* statement to insert into an existing table data originating from a file. 

```sql
LOAD DATA INFILE 'cars.csv' INTO TABLE some_table
FIELDS TERMINATED BY ',' LINES TERMINATED BY ';';
```

* Create a simple Car table with type column as varchar, number column as varchar
* Create file cars.csv with conext like:

```
skoda,rlt11;
toyouta,mnt233;
honda,mrt123;
```
* Upload data to your created table


Note: By default, MySQL doesn’t let you load any data using the LOAD DATA INFILE command. The behavior is controlled by the secure_file_priv system variable. 

You need to put this file in:

```sql
SELECT @@secure_file_priv;
```

If you do not have this variable specified then you need to use such sql:

```sql
LOAD DATA LOCAL INFILE 'cars.csv' INTO TABLE some_table
FIELDS TERMINATED BY ',' LINES TERMINATED BY ';';
```