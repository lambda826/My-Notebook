# Reference
[Grokking the Advanced System Design Interview - Gossip Protocol](https://www.educative.io/courses/grokking-adv-system-design-intvw/7nzRqE43rG8)

---

# Background
In a large distributed environment where we do not have any central node that keeps track of all nodes to know if a node is down or not, how does a node know every other node’s current state?

---

# Definition
Gossip Protocol
 - Each node **keeps track of state information** about other nodes in the cluster and gossip (i.e., share) this information to one other random node every second.

---

# Solution
Gossip protocol is a peer-to-peer communication mechanism in which nodes periodically exchange state information about themselves and about other nodes they know about.
 - Each node initiates a gossip round every second to exchange state information about themselves and other nodes with one other random node.
	 - This means that any state change will eventually propagate through the system, and all nodes quickly learn about all other nodes in a cluster.

![在这里插入图片描述](https://img-blog.csdnimg.cn/77826d2a2cda431989e618cd2a597542.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWXVueGlhbmdfSGU=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MDMzMDczNF19
-->