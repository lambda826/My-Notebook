# Reference
[Grokking the Advanced System Design Interview - Hinted Handoff](https://www.educative.io/courses/grokking-adv-system-design-intvw/3YxgPO2pm6p)

---

# Background
Depending upon the consistency level, a distributed system can still serve write requests even when nodes are down. 
 - Now, when the node which was down comes online again, how should we write data to it?

---

# Definition
Hinted Handoff

 - For nodes that are down, the system **keeps notes (or hints) of all the write requests they have missed**.
 - Once the failing nodes recover, the write requests are forwarded to them based on the hints stored.

---

# Solution
When a node is down or is not responding to a write request, the node which is coordinating the operation, writes a hint in a text file on the local disk.
 - This hint contains the data itself along with information about which node the data belongs to.
 - When the coordinating node discovers that a node for which it holds hints has recovered, it forwards the write requests for each hint to the target.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NzM1NzcyNDhdfQ==
-->