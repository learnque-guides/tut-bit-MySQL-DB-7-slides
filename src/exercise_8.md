# Exercise 7

* Create a system-versioned temporal table called Departments with an associated history table called DepartmentsHistory.
* The table should have the following columns: 
  * deptid INT NOT NULL, 
  * deptname VARCHAR(25) NOT NULL, 
  *  mgrid INT NOT NULL.
* Also include columns called validfrom and validto that define the validity period of the row. Define those with precision zero (1 second), and make them hidden.
