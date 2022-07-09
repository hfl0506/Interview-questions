1. Define a Temp Table.

- In a nutshell, a temp table is a temporary storage structure. Basically, you can use a temp table to store data temporarily so you can manipulate and change it before it reaches its destination format.

2. What is a `VIEW` ?

- A view is simply a virtual table that is made up of elements of multiple physical or “real” tables. Views are most commonly used to join multiple tables together, or control access to any tables existing in background server processes.

3. What is `PRIMARY KEY` ?

- A `PRIMARY KEY` constraint is a unique identifier for a row within a database table.
- Every table should have a primary key constraint to uniquely identify each row and only one primary key constraint can be created for each table.
- The primary key constraints are used to enforce entity integrity.

4. What is Normalisation ?

- `Normalization` is basically to design a database schema such that `duplicate and redundant data is avoided`. If the same information is repeated in multiple places in the database, there is the risk that it is updated in one place but not the other, leading to data corruption.
- There is a number of normalization levels from 1. normal form through 5. normal form. Each normal form describes how to get rid of some specific problem.
- By having a database with normalization errors, you open the risk of getting invalid or corrupt data into the database. Since data "lives forever" it is very hard to get rid of corrupt data when first it has entered the database.

5. What is `DEFAULT` ?

- `Default` allows to add values to the column if the value of that column is not set.
- Default can be defined on number and datetime fields.
- They cannot be defined on timestamp and IDENTITY columns.

6. What is `FOREIGN KEY` ?

- `FOREIGN KEY` constraint prevents any actions that would destroy links between tables with the corresponding data values.
- A foreign key in one table points to a primary key in another table.
- Foreign keys prevent actions that would leave rows with foreign key values when there are no primary keys with that value.
- The foreign key constraints are used to `enforce referential integrity`.

7. What is the difference between `TRUNCATE` and `DELETE` ?

- `DELETE` is a Data Manipulation Language(DML) command. It can be used for deleting some specified rows from a table. `DELETE` command can be used with `WHERE` clause.
- `TRUNCATE` is a Data Definition Language(DDL) command. It deletes all the records of a particular table. `TRUNCATE` command is faster in comparison to `DELETE`. While `DELETE` command can be rolled back, `TRUNCATE` can not be rolled back in MySQL.

8. What is the difference between Data Definition Language (DDL) and Data Manipulation Language (DML) ?

- Data definition language (DDL) commands are the commands which are used to define the database. CREATE, ALTER, DROP and TRUNCATE are some common DDL commands.
- Data manipulation language (DML) commands are commands which are used for manipulation or modification of data. INSERT, UPDATE and DELETE are some common DML commands.

9. Define ACID Properties.

- `Atomicity`: by this, we mean that either the entire transaction takes place at once or doesn't happen at all. There is no midway i.e. transactions do not occur partially. Each transaction is considered as one unit and either runs to completion or is not executed at all. It involves the following two operations. 1. Abort: If a transaction aborts, changes made to the database are not visible. 2. Commit: If a transaction commits, changes made are visible.
  Atomicity is also known as the ‘All or nothing rule’.
  ![image info](./../images/sql-9-1.jpeg)
  If the transaction fails after completion of T1 but before completion of T2.( say, after write(X) but before write(Y)), then the amount has been deducted from X but not added to Y. This results in an inconsistent database state. Therefore, the transaction must be executed in its entirety in order to ensure the correctness of the database state.
- `Consistency`:This means that integrity constraints must be maintained so that the database is consistent before and after the transaction. It refers to the correctness of a database. Referring to the example above,
  The total amount before and after the transaction must be maintained.
  Total before T occurs = 500 + 200 = 700.
  Total after T occurs = 400 + 300 = 700.
  Therefore, the database is consistent. Inconsistency occurs in case T1 completes but T2 fails. As a result, T is incomplete.
- `Isolation`:This property ensures that multiple transactions can occur concurrently without leading to the inconsistency of the database state. Transactions occur independently without interference. Changes occurring in a particular transaction will not be visible to any other transaction until that particular change in that transaction is written to memory or has been committed. This property ensures that the execution of transactions concurrently will result in a state that is equivalent to a state achieved these were executed serially in some order.
  Let X= 500, Y = 500.
  Consider two transactions T and T”.
  ![image info](./../images/sql-9-2.jpeg)
  Suppose T has been executed till Read (Y) and then T’’ starts. As a result, interleaving of operations takes place due to which T’’ reads the correct value of X but the incorrect value of Y and sum computed by
  T’’: (X+Y = 50, 000+500=50, 500)
  is thus not consistent with the sum at end of the transaction:
  T: (X+Y = 50, 000 + 450 = 50, 450).
  This results in database inconsistency, due to a loss of 50 units. Hence, transactions must take place in isolation and changes should be visible only after they have been made to the main memory.
- `Durability`:
  This property ensures that once the transaction has completed execution, the updates and modifications to the database are stored in and written to disk and they persist even if a system failure occurs. These updates now become permanent and are stored in non-volatile memory. The effects of the transaction, thus, are never lost.

10. Discuss `INNER JOIN ON` vs `WHERE` clause (with multiple `FROM` tables).

- Yes. ON should be used to define the join condition and WHERE should be used to filter the data. I used the word should because this is not a hard rule. The splitting of these purposes with their respective clauses makes the query the most readable, it also prevents incorrect data being retrieved when using JOINs types other than INNER JOIN.

11. What is the difference between `INNER JOIN` and `OUTER JOIN` ?

- `Inner Join`:An inner join using either of the equivalent queries gives the intersection of the two tables, i.e. the two rows they have in common.

```sql
select * from a INNER JOIN b on a.a = b.b;
select a.*, b.*  from a,b where a.a = b.b;
a | b
--+--
3 | 3
4 | 4
```

- `Left outer join`:A left outer join will give all rows in A, plus any common rows in B.

```sql
select * from a LEFT OUTER JOIN b on a.a = b.b;
select a.*, b.*  from a,b where a.a = b.b(+);

a |  b
--+-----
1 | null
2 | null
3 |    3
4 |    4
```

- `Right outer join`: A right outer join will give all rows in B, plus any common rows in A.

```sql
select * from a RIGHT OUTER JOIN b on a.a = b.b;
select a.*, b.*  from a,b where a.a(+) = b.b;

a    |  b
-----+----
3    |  3
4    |  4
null |  5
null |  6
```

- `Full outer join`: A full outer join will give you the union of A and B, i.e. all the rows in A and all the rows in B. If something in A doesn't have a corresponding datum in B, then the B portion is null, and vice versa.

```sql
select * from a FULL OUTER JOIN b on a.a = b.b;

 a   |  b
-----+-----
   1 | null
   2 | null
   3 |    3
   4 |    4
null |    6
null |    5
```

12. What is the difference between `JOIN` and `UNION` ?

- `JOIN`:
  1. combines data from many tables based on a matched condition between them
  2. combines data into new columns.
  3. Number of columns selected from each table may not be same.
  4. Datatypes of corresponding columns selected from each table can be different.
  5. It may not return distinct columns.
- `UNION`:
  1. combines the result-set of two or more `SELECT` statements.
  2. combines data into new rows.
  3. Number of columns selected from each table should be same.
  4. Datatypes of corresponding columns selected from each table should be same.
  5. It returns distinct rows.

13. What is the difference between `UNION` and `UNION ALL` ?

- `Union`: means joining two or more data sets into a single set. In SQL Server, Union is used to combine two queries into a single result set using the select statements. Union extracts all the rows that are described in the query.
- `Union All`:A union is used for extracting rows using the conditions specified in the query while Union All is used for extracting all the rows from a set of two tables.
- The same conditions are applicable to Union All. The only difference between Union and Union All is that Union extracts the rows that are being specified in the query while Union All extracts all the rows including the duplicates (repeated values) from both the queries.

14. What is the difference between `INNER JOIN`, `OUTER JOIN`, `FULL OUTER JOIN` ?

- `INNER JOIN`:An inner join using either of the equivalent queries gives the intersection of the two tables, i.e. the two rows they have in common.
- `OUTER JOIN`: outer join includes left outer join and right outer join; A left outer join will give all rows in A, plus any common rows in B, A right outer join will give all rows in B, plus any common rows in A.
- `FULL OUTER JOIN`: A full outer join will give you the union of A and B, i.e. all the rows in A and all the rows in B. If something in A doesn't have a corresponding datum in B, then the B portion is null, and vice versa.

15. What is the difference between `WHERE` clause and `HAVING` clause ?

- `WHERE clause` is used to filter the records from the table or used while joining more than one table.Only those records will be extracted who are satisfying the specified condition in `WHERE clause`. It can be used with SELECT, UPDATE, DELETE statements.
- `HAVING Clause` is used to filter the records from the groups based on the given condition in the `HAVING Clause`. Those groups who will satisfy the given condition will appear in the final result. `HAVING Clause` can only be used
  with SELECT statement.

16. Describe the difference between truncate and delete.

- `DELETE` is a DML(Data Manipulation Language) command and is used when we specify the row(tuple) that we want to remove or delete from the table or relation. The `DELETE` command can contain a WHERE clause. If the WHERE clause is used with the `DELETE` command then it removes or deletes only those rows(tuple) that satisfy the condition otherwise by default it removes all the tuples(rows) from the table. Remember that `DELETE` logs the row deletions.

```sql
DELETE FROM TableName
WHERE condition;
```

- TRUNCATE is a DDL(Data Definition Language) command and is used to delete all the rows or tuples from a table. Unlike the DELETE command, the TRUNCATE command does not contain a WHERE clause. In the TRUNCATE command, the transaction log for each deleted data page is not recorded. Unlike the DELETE command, the TRUNCATE command is fast. We cannot roll back the data after using the TRUNCATE command.

```sql
TRUNCATE TABLE  TableName;The identity
```

17. What is Denormalization ?

- Denormalization is the process of adding precomputed redundant data to an otherwise normalized relational database to improve read performance of the database. Normalizing a database involves removing redundancy so only a single copy exists of each piece of information. Denormalizing a database requires data has first been normalized.
- With denormalization, the database administrator selectively adds back specific instances of redundant data after the data structure has been normalized. A denormalized database should not be confused with a database that has never been normalized.
- Using normalization in SQL, a database will store different but related types of data in separate logical tables, called relations. When a query combines data from multiple tables into a single result table, it is called a join. The performance of such a join in the face of complex queries is often the occasion for the administrator to explore the denormalization alternative.

18. What are the difference between Clustered and a Non-clustered index ?

- `Clustered Index` - Table is created with primary key constraints then database engine automatically create clustered index . In this data sort or store in the table or view based on their key and values.
- `Non-Clustered Index` - Table is created with UNIQUE constraints then database engine automatically create non-clustered index . A nonclustered index contains the nonclustered index key values and each key value entry has a pointer to the data row that contains the key value.

19. How does a Hash index work ?

- Hash indexes allow for quick lookups on data stored in tables. They work by creating an index key from the value and then locating it based on the resulting hash. It is useful when there is a lot of input with similar values or duplicates, as it only needs to compare keys instead of looking through all records.
- Hashing is taking a piece of information (a string) and turning it into an address or pointer for quick access later on.
- The idea with hashing is that data gets assigned a small number. When you’re looking up the data, you don’t have to actually sift through masses. Instead, just look up that one number. The simplest example is Ctrl+F-ing the word you’re looking for in a text instead of reading dozens of pages yourself.

20. How a database index can help performance ?

- the index causes the database to create a data structure. The data structure type is very likely a B-Tree. While the advantages of the B-Tree are numerous, the main advantage for our purposes is that it is sortable. When the data structure is sorted in order it makes our search more efficient for the obvious reasons we pointed out above.

When the index creates a data structure on a specific column it is important to note that no other column is stored in the data structure.

21. What's the difference between a Primary Key and a Unique Key ?

- primary key:
  1. used to ensure data in the specific column is unique.
  2. uniquely identifies a record in relational database table.
  3. only one primary key is allowed in a table.
  4. combination of unique and not null constraints.
  5. it cannot be deleted from the parent table.
  6. it constraint can be implicitly defined on the temporary tables.
- foreign key:
  1. can be a column or group of columns in a relational database table that provides a link between data in two tables.
  2. refers to the field in a table which is the primary key of another table.
  3. more than one foreign key are allowed in a table.
  4. can contain duplicate values and a table in a relational database.
  5. can contain NULL values.
  6. the value can be deleted from the child table.
  7. constraint cannot be defined on the local or global temporary tables.

22. What is Collation ?

- Collation specifies how data is sorted and compared in a database. Collation provides the sorting rules, case, and accent sensitivity properties for the data in the database.
- when you run a query using the ORDER BY clause, collation determines whether or not uppercase letters and lowercase letters are treated the same.
- Collation is also used to determine how accents are treated, as well as character width and Japanese kana characters. Collation can also be used to distinguish between various ideographic variation selectors in certain collations (such as the Japanese_Bushu_Kakusu_140 and Japanese_XJIS_140 collations that were introduced in SQL Server 2017).
- Different database management systems will provide different collation options. Depending on the DBMS, collation can be specified at the server level, the database level, the table level, and the column level. Collations can also be specified at the expression level (so you can specify which collation to use when you run a query), and at the identifier level.

23. How can `VIEW` be used to provide security layer for your app ?

- Use a view to limit the data that a user is allowed to see in a table. For example, if you have an employees table and wish to provide some users with access to the records of full-time employees, you can create a view that contains only those records. This is much easier than the alternative (creating and maintaining a shadow table) and ensures the integrity of the data.

24. What's the difference between Azure SQL database and Azure SQL Managed Instance ?

- Recovery model: Azure SQL Database is from automated backups only; SQL MI is from automated backups and from full backups placed on Azure Blob Storage.
- Active Geo-replication: Azure SQL Database support in all service tiers other than Hyperscale; SQL ML is not supported for that, but it has alternative solution from Auto-failover groups.
- Auto-failover groups: Azure SQL Database support in serverless model; SQL MI is not supported and have to reserve compute and storage.
- Automatic tuning \*indexes: Azure SQL database supported; SQL MI not supported.
- Elastic jobs: Azure SQL database supported; SQL MI not supported and could be use SQL Agent instead.
- Long-term backup retention(LTR): Azure SQL database supported and could be keep automatically backups up to 10 years; SQL MI not supported for that and it needs to backup manually.
- Hyperscale architecture: Azure SQL database is supported; SQL MI is not supported.
- SQL server profiler: Azure SQL database not supported; SQL MI is supported.
- Cross-database transactions: Azure SQL database not supported; SQL MI is supported;
- Database mail(DbMail): Azure SQL database not supported for that; SQL MI is supported.
- Linked servers: Azure SQL database not supported; SQL MI is supported.
- Service Broker: Azure SQL database not supported; SQL MI is supported;
- SQL Server Agent: Azure SQL database not supported; SQL MI is supported;
- SQL Server Auditing: Azure SQL database not supported; SQL MI is supported;

25. What is the cost of having a database index ?

- It will take up space, the larger your table, the larger your index.
- Another performance hit with indexes is the fact that whenever you add, delete, or update rows in the corresponding table, the same operations will have to be done to your index. Remember that an index needs to contain the same up to the minute data as whatever is in the table coulumns(s) that the index covers.
- An index should only be created on a table if the data in the indexed column will be queried frequently.

26. How does B-trees Index work ?

- B-tree is a data structure that provides sorted data and allows searches, sequential access, attachments, and removals in sorted order. The B-tree is highly capable of storage systems that write large blocks of data. The B-tree simplifies the binary search tree by allowing nodes with more than two children. We can represent the sample B-tree as follows.
- ![image info](./../images/sql-26-1.jpeg)
- B-tree stores data such that each node contains keys in ascending order. Each of these keys has two references to another two child nodes. Te left side child node keys are less than the current keys and the right side child node keys are more than the current keys. If a single node has “n” number of keys, then it can have maximum “n+1” child nodes.

27. Explain the difference between Exclusive Lock and Update Lock.

- When Exclusive Lock is on any processes no other lock can be placed on that row or table. Every other process have to wait till Exclusive Lock is complete its tasks.
- Update Lock is kind of Exclusive Lock except it can be placed on the row which already have Shared Lock on it. Update Lock reads the data of row which has Shared Lock, as soon as Update Lock is ready to change the data it converts itself to Exclusive Lock.

28. What is the difference among `UNION`, `MINUS` and `INTERSECT` ?

- `UNION`: The most commonly used command, `UNION` combines the two answer sets into a single answer set. It automatically removes duplicate rows from the results.
- `INTERSECT`: It gives you the rows that are found in both queries by eliminating rows that are only found in one or the other query.
- `MINUS`: It gives you the rows that are found in the first query and not in the second query by removing from the results all the rows that are found only in the second query.

29. What is fater, one big query or many small queries ?

- when your query is based on one condition, it is better to use one bigger query

```sql
SELECT product_id, product_name FROM products WHERE product_category IN (1,2,3);
```

rather than

```sql
SELECT product_id, product_name FROM products WHERE product_category = 1;
SELECT product_id, product_name FROM products WHERE product_category = 2;
SELECT product_id, product_name FROM products WHERE product_category = 3;
```

- using one query, which is reading the data from more tables with functions LEFT JOIN, RIGHT JOIN or INNER JOIN, instead of using multiple separated / nested queries, where each query is reading the data from only one table:

```sql
SELECT product_id, product_name FROM products AS p LEFT JOIN categories AS c ON p.product_category = c.category_id WHERE c.category_promotion = 1;
```

to benefit this case should have break down to multiple case

```sql
SELECT product_id, product_name FROM products WHERE product_price < 100;
SELECT * FROM products WHERE product_price < 100;
```

- In case of more complex operations, to speed up the processing, it can be good solution to create and use temporary tables with relevant data. Also the nested queries can be faster, than multiple separated queries:

```sql
INSERT INTO temporary_products (product_id, product_name, product_description, product_price, product_category, product_quantity, product_status) SELECT product_id, product_name, product_description, product_price, product_category, product_quantity, product_status FROM products WHERE product_category = 3;
```

30. What is Optimistic Locking and Pessimistic Locking ?

- Optimistic Locking:
  1. is a strategy where you read a record, take note of a version number (other methods to do this involve dates, timestamps or checksums/hashes) and check that the version hasn't changed before you write the record back. When you write the record back you filter the update on the version to make sure it's atomic. (i.e. hasn't been updated between when you check the version and write the record to the disk) and update the version in one hit.
  2. If the record is dirty (i.e. different version to yours) you abort the transaction and the user can re-start it.
  3. This strategy is most applicable to high-volume systems and three-tier architectures where you do not necessarily maintain a connection to the database for your session. In this situation the client cannot actually maintain database locks as the connections are taken from a pool and you may not be using the same connection from one access to the next.
- Pessimistic Locking:
  1. is when you lock the record for your exclusive use until you have finished with it. It has much better integrity than optimistic locking but requires you to be careful with your application design to avoid Deadlocks. To use pessimistic locking you need either a direct connection to the database (as would typically be the case in a two tier client server application) or an externally available transaction ID that can be used independently of the connection.
  2. In the latter case you open the transaction with the TxID and then reconnect using that ID. The DBMS maintains the locks and allows you to pick the session back up through the TxID. This is how distributed transactions using two-phase commit protocols (such as XA or COM+ Transactions) work.

31. What are some other types of Indexes (vs B-Trees) ?

- Forest of trees indexes: A forest of trees index is like a B-tree index, but it has multiple root nodes and potentially fewer levels. Multiple root nodes can alleviate root node contention, because more concurrent users can access the index. A forest of trees index can also improve the performance of a query by reducing the number of levels involved in buffer read operations.
- R-tree indexes: Informix uses an R-tree index for spatial data (such as two-dimensional or three-dimensional data).
- Indexes that DataBlade modules provide: DataBlade modules can contain user-defined data types. A DataBlade module can also provide a user-defined index for the new data type.

32. Name some disadvantages of a Hash index.

- Cannot avoid reading lines: Hash index only contains hash value and row pointer , Instead of storing field values , So you can't use the values in the index to avoid reading rows . however , Access to rows in memory is very fast , So in most cases, the impact on performance is not obvious .
- Can't be used to sort: Hash index data is not stored in the order of index values , So it can't be used for sorting .
- Cannot use partial index column matching to find: Hash index also does not support partial index column matching lookup , Because the hash index always uses the entire content of the index column to calculate the hash value . for example , In the data column （A,B） Create a hash index on , If the query has only columns of data A, The index cannot be used .
- Only equivalent search is supported: Hash index only supports equivalent comparison query , Include =、IN()、<=>（ Be careful <> and <=> It's a different operation ）. No scope queries are supported , for example WHERE price>100.
- There is Hash Conflict:
  1. Accessing hash index data is very fast , Unless there are many hash conflicts （ Different index column values have the same hash value ）. When there is a hash conflict , The storage engine must traverse all row pointers in the linked list , Compare line by line , Until you find all the right lines .
  2. meanwhile , When there are many hash conflicts , Some index maintenance operations are also expensive . for example , If at some point the selectivity is low （ There are a lot of hash conflicts ） Create a hash index on the column of , So when you delete a row from the table , The storage engine needs to traverse each row in the linked list corresponding to the hash value , Find and delete the reference to the corresponding line , The more conflicts , The more it costs .

33. What is difference between B-Tree, R-Tree and Hash indexing ?

- BTree (in fact B\*Tree) is an efficient ordered key-value map. Meaning:
  1. given the key, a BTree index can quickly find a record,
  2. a BTree can be scanned in order.
  3. it's also easy to fetch all the keys (and records) within a range.
- RTree is a spatial index which means that it can quickly identify close values in 2 or more dimensions. It's used in geographic databases for queries such as:
  1. all points within X meters from (x,y)
- Hash is an unordered key-value map. It's even more efficient than a BTree: O(1) instead of O(log n).
  1. But it doesn't have any concept of order so it can't be used for sort operations or to fetch ranges.
  2. As a side note, originally, MySQL only allowed Hash indexes on MEMORY tables; but I'm not sure if that has been changed over the years.

34. What is Index Cardinality and why does it matter ?

- Index cardinality refers to the uniqueness of values stored in a specified column within an index.
- The query optimizer uses the index cardinality to generate an optimal query plan for a given query. It also uses the index cardinality to decide whether to use the index or not in the join operations.
- If the query optimizer chooses the index with a low cardinality, it is may be more effective than scan rows without using the index.
- To view the index cardinality, you use the SHOW INDEXES command.
- For example, the following statement returns the index information of the orders table in the sample database with the cardinality (\*):

```sql
mysql> SHOW INDEXES FROM orders;
+--------+------------+----------------+--------------+----------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+
| Table  | Non_unique | Key_name       | Seq_in_index | Column_name    | Collation | Cardinality | Sub_part | Packed | Null | Index_type | Comment | Index_comment | Visible |
+--------+------------+----------------+--------------+----------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+
| orders |          0 | PRIMARY        |            1 | orderNumber    | A         |         326 |     NULL |   NULL |      | BTREE      |         |               | YES     |
| orders |          1 | customerNumber |            1 | customerNumber | A         |          98 |     NULL |   NULL |      | BTREE      |         |               | YES     |
+--------+------------+----------------+--------------+----------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+
2 rows in set (0.01 sec)
```
