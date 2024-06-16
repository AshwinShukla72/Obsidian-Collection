```ad-important
Consistency - Availability - Partition Tolerance
``` 

- *Consistency*: Every read receives the most recent write or an error

- *Availability*: Every request receives a response which is not an error

- *Partition Tolerance*: The system continues to operate despite an arbitrary number of messages being dropped (or delayed) by the network between nodes


```ad-attention

- CAP theorem implies that in the presence of a network partition, one has to choose between consistency and availability
- CAP is frequently misunderstood as if one has to choose to abandon one of the three guarantees at all times. In fact, the choice is really between consistency and availability only when a network partition or failure happens; at all other times, no trade-off has to be made.

```

- [[ACID]] databases choose consistency over availability.
- [[BASE (basically Available Soft State Eventual Consistency)]] systems choose availability over consistency.

```ad-seealso
![[PACELC Theorem]]
```
