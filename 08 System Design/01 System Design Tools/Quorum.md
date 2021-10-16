# Reference
[Grokking the Advanced System Design Interview - Quorum](https://www.educative.io/courses/grokking-adv-system-design-intvw/q2Oyw67Z8BG)
[分布式系统理论之Quorum机制](https://www.cnblogs.com/hapjin/p/5626889.html)

---

# Background
In Distributed Systems, data is replicated across multiple servers for fault tolerance and high availability.
How to make sure that all replicas are consistent?

---

# Definition
Quorum
* A **quorum** is the **minimum number** of servers on which a **distributed operation** needs to be performed successfully before declaring the operation’s overall success.

Example:
 - A database is replicated on 5 machines.
 - A **quorum** refers to the minimum number of machines that perform the **same action (commit or abort)** for a given transaction in order to decide the final operation for that transaction.

---

# Solution
**What value** should we choose for a quorum?
* **More than half** of the number of nodes in the cluster: (N/2 + 1)

**Quorum is achieved** when nodes follow the below protocol: **R + W > N**, where:
 - **N** = nodes in the quorum group
 - **W** = minimum write nodes
 - **R** = minimum read nodes
 - If a distributed system follows R + W > N rule, then **every read will see at least one copy of the latest value written**.


The following two things should be kept in mind before deciding read/write quorum:
* R=1 and W=N ⇒ full replication (write-all, read-one): undesirable when servers can be unavailable because writes are not guaranteed to complete.
* Best performance (throughput/availability) when 1 < r < w < n, because reads are more frequent than writes in most applications.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg3NjExMTM5OV19
-->