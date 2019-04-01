# Best practices of SQL Server

* Don't forget to write proper comments in your stored procedures, triggers, and SQL query, whenever something is not very obvious. It will help the other developers to understand your code easily. Don’t worry about the lines of the comments in your query.

* Make sure that you are applying the Normalization rules. Your data must be of  at least the 3rd normal form. At the same time, please do not try to compromise with your query performance. A little bit of de-normalization in your query, helps the system perform faster.

* Choose a database naming convention, institutionalize it over your association, and be reliable in tailing it. It makes your code more lucid and justifiable.For more details of naming conventions with example, [click here](http://vyaskn.tripod.com/object_naming.htm).

* Once you write the "SELECT" command in SQL, don't use SELECT * in your queries. Always try to write the only needful column names after the SELECT statement. See the examples below. 

   ```sql
   Select * from tblName  --Wrong way    
  
   Select firstName,lastName from tblName -- correct way   
   ```
    This technique will reduce your hard disk's I/O performance.

* You need to avoid to use the server side cursors as much as possible in an SQL query. Continuously adhere to a 'set-based approach' rather than a 'procedural approach' for getting to a controlling information. Cursors can regularly be avoided, by utilizing SELECT statement.

* On the off chance that a cursor is unavoidable, utilize a WHILE loop. I have, by and by, tried and reasoned that a WHILE loop is constantly speedier than a cursor. Yet, for some time, loop to supplant a cursor, you require a section (Primary key or unique key) to recognize every column. I, for one, trust that each table must have a Primary or Unique key.

* Keep away from the creation of temp tables while preparing information, however, as much as could be expected, as making a temp table means more circle I/O. Consider utilizing advanced SQL, sees, SQL Server 2000 table variable, or derived tables, rather than temp tables.

* Try to use "Derived tables" wherever possible, as they perform better than others. You can use the following query to get the 2nd highest salary from the Emp table in sql.see example.

    ```sql
    SELECT MIN(Salary)     
    FROM Emp    
    WHERE EmpID IN    
    (    
    SELECT TOP 2 EmpID     
    FROM Emp    
    ORDER BY Salary Desc    
    )    
    As per the above same query, you can write using a derived table (Subquery), as given below, and it will perform twice as fast as the above given SQL query. see the example.
    SELECT MIN(Salary)     
    FROM     
    (    
    SELECT TOP 2 Salary     
    FROM Emp    
    ORDER BY Salary DESC    
    ) AS xyz  
    ```
    This is only a case, and your results may contrast in various situations relying upon the database design, indexing, volume of information, and so on. In this way, test all the conceivable ways a SQL query could be written, and run with the most proficient one. 

* Utilize the more discernable ANSI-Standard Join provisions rather than the old style Joins. With ANSI joins, the WHERE statement is utilized just to filter the information. Whereas with more seasoned style joins, the WHERE provision handles both the join condition and the separating information. The first of the accompanying two questions demonstrates the old style join, while the second one demonstrates the new ANSI join syntax.
    ```sql
    SELECT a.au_id, t1.title     
    FROM table1 t1, table2 a, table3 ta    
    WHERE     
    a.au_id = ta.au_id AND    
    ta.title_id = t1.title_id AND     
    t1.title LIKE ‘%Computer%’    
        
    SELECT a.au_id, t1.title    
    FROM table2 a     
    INNER JOIN    
    table3 ta     
    ON     
    a.au_id = ta.au_id    
    INNER JOIN    
    table1 t1    
    ON    
    ta.title_id = t1.title_id    
    WHERE t1.title LIKE ‘%xyz%’    
    Utilizing SET NOCOUNT ON towards the start of your SQL clusters, puts away systems, and triggers underway situations, as this stifles messages, like '(1 row(s) influenced)' in the wake of executing INSERT, UPDATE, DELETE and SELECT statement. This enhances the execution of put away techniques by lessening the system movement.
    USE DB_name;      
    GO      
    SET NOCOUNT OFF;      
    GO      
    --just you can show  count message.      
    SELECT TOP(5)Name      
    FROM xyz.xyz    
    WHERE NameLIKE 'A%';      
    GO      
    -- now you can  SET NOCOUNT to ON to no longer show the any message.      
    SET NOCOUNT ON;      
    GO      
    SELECT TOP(5) Name    
    FROM  xyz.xyz    
    WHERE name LIKE 'x%';      
    GO      
    -- now you can reset SET NOCOUNT to OFF       
    SET NOCOUNT OFF;      
    GO     
    ```

* Try not to give your front-end applications a chance to query/manipulate the information straightforwardly, utilizing SELECT or INSERT/UPDATE/DELETE statement. Rather, create a stored procedure and let your applications get to these put away systems. This keeps the information spotless and predictable over each of the modules of your application, and in the meantime, brings together the business rationale inside the database.

* You need to take care of these points once you execute the SELECT query.

    In this example, you can see that I have [ ] because SQL Server has some pre-defined keywords e.g User, Admin, Address. So, in that, if you are not using [ ], it may throw error. That's why I have used Table name and column name inside [ ].
    ```sql
    Select * from User ----Wrong way    

    Select [firstName],[lastname] from [User] --Correct way    
    ```
* _Constraint_
This one is very important, once you go to create or alter any constraint in SQL Server. I have seen that most of the developers create constraint without constraint name. In that case, SQL will create the default key name for constraint, e.g., default_2908xyz.

    ```sql
    Syntax
    --incorrect way  
    ALTER TABLE tblName    
    ADD clmnName INT NOT NULL DEFAULT 0    
        
    --Correct way    
    ALTER TABLE tblNmae     
    ADD ClmnName DataTypes {NULL|NOT NULL}     
    CONSTRAINT defult_xyz DEFAULT {DEFAULT_VALUE}    
    [WITH VALUES]   
    ```
    In this above syntax, you can see that I have written two queries. If you write the SQL query as the first one,you will face drop column and constraint in future from SQL table.

[Refernce](https://www.c-sharpcorner.com/article/best-practices-and-programming-guidelines-in-sql-server/)
