Reference
 - [CAP Theorem - Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview/RMkqx1Egxqz)

---

**CAP Theory**
![CAP Theory](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20System%20Design/resource/image/CAP%20Theory.png)

**Availability**
 - Availability in a distributed system ensures that the system remains operational 100% of the time.
 - Every request gets a (non-error) response regardless of the individual state of a node.

**Consistency**
 - All nodes see the same data at the same time.
   - Simply, if we perform a read operation on a consistent system, it should return the value of the most recent write operation.
     - This means that, the read should cause all nodes to return the same data, i.e., the value of the most recent write.

**Partition tolerance**
 - This condition states that the system does not fail, regardless of if messages are dropped or delayed between nodes in a system.
 - It is made possible by sufficiently replicating records across combinations of nodes and networks.
 - When dealing with modern distributed systems, Partition Tolerance is not an option. It’s a necessity.

---

**Note**
 - We cannot build a general data store that is continually available, sequentially consistent, and tolerant to any partition failures.
 - We can only build a system that has any two of these three properties.
 - Because, to be consistent, all nodes should see the same set of updates in the same order.
   - But if the network suffers a partition, updates in one partition might not make it to the other partitions before a client reads from the out-of-date partition after having read from the up-to-date one.
   - The only thing that can be done to cope with this possibility is to stop serving requests from the out-of-date partition, but then the service is no longer 100% available.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc5NzcyNzAyN119
-->