# The OUTPUT clause

The OUTPUT clause usefull for debugging when we do INSERT, UPDATE, DELETE and MERGE.

The OUTPUT clause is designed similarly to the SELECT clause, only you need to prefix the attributes with either the inserted or deleted keyword. 
* In an INSERT statement, you refer to inserted; 
* In a DELETE statement, you refer to deleted; 
* And in an UPDATE statement, you refer to deleted for the old state of the row and inserted for the new state.

