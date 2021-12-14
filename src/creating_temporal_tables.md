# Creating temporal tables

When you create a system-versioned temporal table, you need to make sure the table definition has all the following elements:

* A primary key
* Two columns defined as DATETIME2
* A start column that should be marked with the option GENERATED ALWAYS AS ROW START
* An end column that should be marked with the option GENERATED ALWAYS AS ROW END
* A designation of the period columns with the option PERIOD FOR SYSTEM_TIME (<startcol>, <endcol>)
* The table option SYSTEM_VERSIONING, which should be set to ON
* A linked history table (which SQL Server can create for you) to hold the past states of modified rows

```sql
CREATE TABLE dbo.Employees
(
  empid      INT                         NOT NULL
    CONSTRAINT PK_Employees PRIMARY KEY NONCLUSTERED,
  empname    VARCHAR(25)                 NOT NULL,
  department VARCHAR(50)                 NOT NULL,
  salary     NUMERIC(10, 2)              NOT NULL,
  sysstart   DATETIME2(0)
    GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,
  sysend     DATETIME2(0)
    GENERATED ALWAYS AS ROW END   HIDDEN NOT NULL,
  PERIOD FOR SYSTEM_TIME (sysstart, sysend),
  INDEX ix_Employees CLUSTERED(empid, sysstart, sysend)
)
WITH (SYSTEM_VERSIONING = ON ( HISTORY_TABLE = dbo.EmployeesHistory ));
```

It is possible to enable temporal functionality for table by using:

```sql
ALTER TABLE dbo.Employees ADD
  sysstart DATETIME2(0) GENERATED ALWAYS AS ROW START HIDDEN NOT NULL
    CONSTRAINT DFT_Employees_sysstart DEFAULT('19000101'),
  sysend DATETIME2(0) GENERATED ALWAYS AS ROW END HIDDEN NOT NULL
    CONSTRAINT DFT_Employees_sysend DEFAULT('99991231 23:59:59'),
  PERIOD FOR SYSTEM_TIME (sysstart, sysend);

ALTER TABLE dbo.Employees
  SET ( SYSTEM_VERSIONING = ON ( HISTORY_TABLE = dbo.EmployeesHistory ) );
```

Modifying temporal tables is similar to modifying regular tables. You modify only the current table with INSERT, UPDATE, DELETE, and MERGE statements. 

```sql
INSERT INTO dbo.Employees(empid, empname, department, salary)
  VALUES(1, 'Sara', 'IT'       , 50000.00),
        (2, 'Don' , 'HR'       , 45000.00),
        (3, 'Judy', 'Sales'    , 55000.00),
        (4, 'Yael', 'Marketing', 55000.00),
        (5, 'Sven', 'IT'       , 45000.00),
        (6, 'Paul', 'Sales'    , 40000.00);
```

```sql
SELECT empid, empname, department, salary, sysstart, sysend
FROM dbo.Employees;

SELECT empid, empname, department, salary, sysstart, sysend
FROM dbo.EmployeesHistory;
```

