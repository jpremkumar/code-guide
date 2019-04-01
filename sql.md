# SQL Code Check

* Use table aliases and refer to column names using that alias
* Use WITH (NOLOCK) for selecting or deleting rows from a table
* Use WITH (NOLOCK) in JOIN conditions
* Use WITH (HOLDLOCK TABLOCKX) with UPDATE statements
* Use SET NOCOUNT ON
* Do not use DATA_COMPRESSION = PAGE flag for INDEXES on temp tables
* Do not use LOCKS on Temporary Tables/Views
* Follow Pascal case for variable/table/views/stored procedure names
* Spaces are not allowed in TABLE/VIEW/PROCEDURE/Constraint names
* Follow 'IXCU_ColumnName' convention for UNIQUE CLUSTERED INDEX
* Follow 'IXC_ColumnName' convention for CLUSTERED INDEX
* Follow 'IXU_ColumnName' convention for UNIQUE NONCLUSTERED INDEX
* Follow 'IX_ColumnName' convention for NONCLUSTERED INDEX
* Follow 'IXCS_ColumnName' for COLUMNSTORE INDEX
* Follow 'PK_TableName_ColumnName' convention for PRIMARY KEY
* Create Table/Primary Key/Clustered, Non-Clustered Index/ only on DATA File Group
* Either DATA_COMPRESSION = PAGE flag is missing, or you have used flags other than DATA_COMPRESSION = PAGE for Indexes
* Multiple calls of GETDATE() found. Store GETDATE() value in a variable and use this variable
* Avoid use of subqueries in JOIN statements
* Avoid use of subqueries in WHERE clause
* Check headers for SQL file, like Mention Author, Created Date, Description and Test Scripts as comments at the beginning of a stored procedure
* Use CONVERT() instead of CAST()

> [Basics of T-SQL Coding Practise](https://www.red-gate.com/simple-talk/sql/t-sql-programming/basics-good-t-sql-coding-style/)
