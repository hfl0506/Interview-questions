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
