# Reference
[Grokking the Advanced System Design Interview - Merkle Trees](https://www.educative.io/courses/grokking-adv-system-design-intvw/q27QYqZDJNk)

---

# Background
When a replica falls significantly behind others, it might take a very long time to resolve conflicts.

- In a distributed environment, how can we quickly compare two copies of a range of data residing on two different replicas and figure out exactly which parts are different?
- Naively splitting up the entire range to calculate checksums for comparison, is not very feasible; there is simply too much data to be transferred. Instead, we can **use Merkle trees to compare replicas of a range**.

---

# Definition
Merkle Trees
- **A Merkle tree** is **a binary tree of hashes**, where each internal node is the hash of its two children, and each leaf node is a hash of a portion of the original data.

---

# Solution
![Merkle Trees](https://img-blog.csdnimg.cn/c49ff70368ec40bf9113252c6658675e.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWXVueGlhbmdfSGU=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
Comparing Merkle trees is conceptually simple:

- Compare the root hashes of both trees.
- If they are equal, stop.
- Recurse on the left and right children.

Ultimately, this means that replicas know exactly which parts of the range are different, but the amount of data exchanged is minimized.

---

Pros
- Each branch of the tree can be checked independently without requiring nodes to download the entire tree or the entire data set. Hence, Merkle trees minimize the amount of data that needs to be transferred for synchronization and reduce the number of disk reads.

Cons

- The disadvantage of using Merkle trees is that many key ranges can change when a node joins or leaves, at which point the trees need to be recalculated.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyNjczMTY4OThdfQ==
-->