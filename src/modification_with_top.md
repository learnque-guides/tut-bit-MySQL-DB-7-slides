# Modifications with LIMIT and OFFSET-FETCH

* SQL supports using the LIMIT option directly in INSERT, UPDATE, DELETE, and MERGE statements.
* The OFFSET-FETCH filter is not allowed directly in modifications because this filter requires an ORDER BY clause and modification statements don’t support one.

