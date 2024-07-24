

- What is the need for Scaling a messaging queue?
	- It becomes a bottleneck as a queue can only hold onto certain amount of data. 
	- Single machine queue on failure -> loss of data (becomes a Single Point of Failure)
	- <mark style="background: #FF5582A6; font-size:1.2em">How to prevent SPOF?</mark>
		- #### Master-Slave
			- Write will come to the master
			- Read will also be shared my replicas

Solution 1:
have different topics, separate topics for different activities making the topics independent of each other.
