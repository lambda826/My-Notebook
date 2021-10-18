# Reference
[Grokking the Advanced System Design Interview - Vector Clocks](https://www.educative.io/courses/grokking-adv-system-design-intvw/xV575J9QE3q)

---

# Background
When a distributed system allows concurrent writes, it can result in multiple versions of an object. Different replicas of an object can end up with different versions of the data.
 - How can we reconcile and capture causality between different versions of the same object?

---

# Definition
Vector Clocks
 - Use Vector clocks to **keep track of value history and reconcile divergent histories** at read time.

---

# Solution
A vector clock is effectively a **(node, counter) pair**.
 - One vector clock is associated with every version of every object.
 - If the counters on the first object’s clock are less-than-or-equal to all of the nodes in the second clock, then the first is an ancestor of the second and can be forgotten.
 - Otherwise, the two changes are considered to be in conflict and require reconciliation.
 - Such conflicts are resolved at read-time, and if the system is not able to reconcile an object’s state from its vector clocks, it sends it to the client application for reconciliation.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMxNzg0NjM2N119
-->