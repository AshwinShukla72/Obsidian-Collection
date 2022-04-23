#### Definition
> Isolation levels are levels created by the Database, in-order to combat the cases of Phantom, Dirty & Non-Repeatable Reads.
> Or can be understood as _**These are levels defined whether or not read data in certain situtations**_

- **Read Uncommitted**
	No isolation, any change from the outside is visible to the transaction.
- **Read Committed**
	Each Query in a transaction only sees committed stuff
- **Repeatable Read**
	Each query in a transaction only sees committed updates at the beginning of transaction.
- **Serializable**
	Transactions are serialized.

---
| **Isolation Levels** | Dirty Reads    | Non-Repeatable Read | Phantom Reads  | Lost Updates   |
| ---------------- | -------------- | ------------------- | -------------- | -------------- |
| **Read Uncommitted** | ==Can Happen== | ==Can Happen==      | ==Can Happen== | ==Can Happen== |
| **Read Committed**   | Doesn't Occur  | ==Can Happen==      | ==Can Happen== | ==Can Happen== |
| **Repeatable Read**  | Doesn't Occur  | Doesn't Occur       | Doesn't Occur  | ==Can Happen== |
| **Serializable**     | Doesn't Occur  | Doesn't Occur       | Doesn't Occur  | Doesn't Occur               |
