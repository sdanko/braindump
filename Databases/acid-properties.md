# ACID Properties

The acronym ACID stands for:
1. Atomicity
2. Consistency
3. Isolation
4. Durability

These describe the set of properties of database transactions that 
guarantee data integrity despite errors, system failures, power failures,
or other issues.

A database transaction is a sequence of operations on a database that satisfies the ACID properties.
Example of the transaction:

```
BEGIN TRANSACTION

INSERT INTO [dbo].[EmployeeRecords] (
	    [EmpID], [FirstName], [LastName], [Education], [Occupation], [YearlyIncome], [Sales])
     VALUES (5, 'SQL', 'Server', 'Education', 'Teaching', 10000, 200)

UPDATE [dbo].[EmployeeRecords]
	SET [Education] = 'Tutorials',
		[YearlyIncome] = 98000
	WHERE [EmpID] = 5
	   
COMMIT TRANSACTION
```

## Atomicity

Atomicity refers to the fact that a transaction succeeds or it fails.
It is an all-or-nothing operation. Despite being composed of multiple 
steps, those steps are treated as a single operation or a unit.

## Consistency

Consistency refers to the characteristic that requires data updated via 
transactions to respect the other constraints or rules within the database 
systems to keep data in a consistent state.

## Isolation

Modern DBMSs allow users to access data concurrently and in parallel. Isolation is 
the characteristic that allows concurrency control so modifications from one transaction
are not affecting operations in another transaction. Two parallel transactions are in reality 
isolated and seem to be performed sequentially.

## Durability

The last ACID property, durability, refers to the persistence of committed transactions. 
Transactions and database modifications are not kept in volatile memory but are saved to 
permanent storage, such as disks.

## Implementation 

The most common implementation of ACID transactions is done via locks. Data is locked 
(not accessible by another transaction) until a transaction completes or fails, to guarantee 
atomicity, isolation, and consistency.

To guarantee durability, databases often implement write-ahead logs. Transactions are
first stored into transaction logs, and only once they are saved to this separate repository, 
they are implemented in the actual database. In case of system failure mid-transaction, 
the transaction is either rolled back or continued from the transaction log left off.

## Downsides

ACID transactions also carry negative consequences that need to be weighed against the 
advantages. Database systems that rely on ACID transactions are usually slower at read
and write operations, because of the locking mechanism.

Distributed databases, such as NoSQL databases like Casandra or MongoDB, replicate data across 
several nodes or servers. Each node carries a copy of the overall data but does not necessarily 
update the data at the same time across all nodes. This design allows for faster data ingestion and reads.

In other words, has higher availability. But availability comes at the cost of consistency - data can 
be stale or inconsistent across nodes at any point in time. Distributed databases guarantee eventual 
consistency, aka data will be consistent, but not necessarily when you retrieve it from your closest node.