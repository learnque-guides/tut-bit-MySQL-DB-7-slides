# Temporal tables

* When you modify data in tables, normally you lose any trace of the premodified state of the rows. You can access only the current state. What if you need to be able to access historical states of the data? 
* Perhaps you need these states for auditing, point-in-time analysis, comparing current states with older states, restoring an older state of rows because of accidental deletion or updating, and so on.