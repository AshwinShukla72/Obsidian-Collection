
```ad-seealso
PACELC Theorem
![[Pasted image 20240614171849.png]]
```

- The PACELC theorem is an extension of the CAP theorem and provides a more comprehensive framework for understanding trade-offs in distributed systems. Here’s a breakdown of the PACELC theorem:

- **P** stands for **Partition Tolerance**: It indicates that the system continues to operate despite physical network partitions that prevent communication between groups of nodes in the system.
- **A** stands for **Availability**: It refers to the system’s ability to always process queries and not have any downtime.
- **C** stands for **Consistency**: It means that all nodes see the same data at the same time.

The PACELC theorem states that in the event of a network partition (**P**), a distributed system must choose between **Availability** (**A**) and **Consistency** (**C**). This is similar to the CAP theorem. However, the PACELC theorem goes further by stating that **else** (**E**), even when the system is running normally in the absence of partitions, one must choose between **Latency** (**L**) and **Consistency** (**C**).

In essence, the #PACELC theorem suggests that outside of partitions, there is still a trade-off to be made between the latency of operations and the consistency of data. This helps designers and architects of distributed systems to make more informed decisions about their system’s behavior in both normal and partitioned states.

To summarize, the PACELC theorem provides a more detailed perspective on the trade-offs between consistency, availability, and latency in distributed systems, extending beyond the scenarios covered by the CAP theorem.