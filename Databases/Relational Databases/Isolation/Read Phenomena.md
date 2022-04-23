#### Definition
> Situations where data is read by a query in a transaction where you may not want it to be read. They can cause issues with working with data in a transaction
1. **Dirty Reads**
	- When changes occurs to the database, when data is read and updated without commit, Basically an incomplete transaction.
2. **Non-Repeatable Reads**
	- one in which data read twice inside the same transaction cannot be guaranteed to contain the same value.
3. **Phantom Reads**
	- occurs when, in the course of a transaction, new rows are added or removed by another transaction to the records being read.
4. **Lost Updates**
	- Committed changes to the database are lost, resulting in bad data.
