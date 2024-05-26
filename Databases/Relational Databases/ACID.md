#### Definition
> In the context of transaction processing, ACID refers to 4 key properties of a transaction → Atomicity, Isolation, Consistency & Durability

- ##### What is a #transaction?
	- A _**transaction**_ is a very small unit of a program and it may contain several low level tasks.
	- The _**transaction**_ is used to transform the database from one consistent state to another consistent state. 
	- A collection of queries. 

	```SQL
	SELECT Balance FROM Account WHERE id = 1 
	// Check for balance 
	UPDATE Account SET Balance = Balance - 100 WHERE id = 1 
	UPDATE Account SET Balance = Balance + 100 WHERE id = 2 
	// COMMIT TRANSACTION
	```

- ![[Atomicity]]
- ![[Isolation]]
- ![[Consistency]]
- ![[Durabilty]]
