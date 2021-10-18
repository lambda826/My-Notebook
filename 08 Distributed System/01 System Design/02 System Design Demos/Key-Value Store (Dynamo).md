# Reference
[educative - Dynamo](https://www.educative.io/courses/grokking-adv-system-design-intvw/xoEXr9614RB)
[AWS Official Docs](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html)

---

# Introduction
Dynamo is a highly available key-value store.
Dynamo is used at Amazon to manage services that have very high-reliability requirements and need tight control over the trade-offs between **availability**, **consistency**, **cost-effectiveness**, and **performance**.

---

## Key Words
Distributed Hash Table (DHT)
Consistent Hashing
Pptimistic Replication
Eventual Consistency
MD5 hashing algorithm
Sloppy Quorum
Gossip Protocol
Hinted Handoff
Vector Clock
Merkle Tree

---

# Requirements
## **Functional**
* **put(key, context, object)**
	* The **put** operation finds the nodes where the object associated with the given key should be stored and writes the given **object** to the disk.
	* The **context** is a value that is returned with a get operation and then sent back with the put operation. The **context** is always stored along with the **object** and is used like a cookie to verify the validity of the **object** supplied in the put request.
* **get(key)**
	* The **get** operation finds the nodes where the object associated with the given key is located and returns either a single **object** or a **list of objects** with *conflicting versions* along with a **context**.
	* The **context** contains encoded metadata about the **object** that is meaningless to the caller and includes information such as the version of the **object**.

## **Non-Functional**
* Highly available
* Highly scalable
* Completely decentralized
* Eventually consistent and low latency

---

# High Level Design
## Distributed Hash Table (DHT
Dynamo is a **[Distributed Hash Table (DHT)](https://www.educative.io/edpresso/what-is-a-distributed-hash-table)** that is replicated across the cluster for high availability and fault tolerance.

## Data Paritioning
### Chanllenges

 - How do we know on which node a particular piece of data will be stored?
 - When we add or remove nodes, how do we know what data will be moved from existing nodes to the new nodes?
 - Furthermore, how can we minimize data movement when nodes join or leave?

### Solution
 - Consistent Hashing
 - Optimistic Replication
 - Preference List
	 - The list of nodes responsible for storing a particular key.


## Strategies for Choosing the Coordinator Node
![How clients connect to Dynamo](https://img-blog.csdnimg.cn/ace4e00ed179407f8bb8b33bd0749bf5.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWXVueGlhbmdfSGU=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
Dynamo clients can use one of the two strategies to choose a node for their get() and put() requests:
 - Clients can route their requests through a generic load balancer.
	 - The client is unaware of the Dynamo ring, which helps scalability and makes Dynamo’s architecture loosely coupled.
	 - The load balancer can forward the request to any node in the ring, it is possible that the node it selects is not part of the preference list.
		 - This will result in an extra hop, as the request will then be forwarded to one of the nodes in the preference list by the intermediate node.
 - Clients can use a partition-aware client library that routes the requests to the appropriate coordinator nodes with lower latency.
 	- This strategy helps in achieving lower latency.
 	- The client maintains a copy of the ring and forwards the request to an appropriate node from the preference list.
 	- Dynamo does not have much control over the load distribution and request handling.

## Consistency protocol
Dynamo uses a consistency protocol similar to quorum systems.
If R/W is the minimum number of nodes that must participate in a successful read/write operation respectively:

 - Then R+W > N yields a quorum-like system
 - A Common (N, R, W) configuration used by Dynamo is (3, 2, 2).
	 - (3, 3, 1): fast WW, slow RR, not very durable
	 - (3, 1, 3): fast RR, slow WW, durable
 - In this model, the latency of a get() (or put()) operation depends upon the slowest of the replicas.
	 - For this reason, R and W are usually configured to be less than NN to provide better latency.
 - In general, low values of W and R increase the risk of inconsistency, as write requests are deemed successful and returned to the clients even if a majority of replicas have not processed them.
 	- This also introduces a vulnerability window for durability when a write request is successfully returned to the client even though it has been persisted at only a small number of nodes.
 - For both Read and Write operations, the requests are forwarded to the first ‘N’ healthy nodes.


**put() process:**

 1. The coordinator requests the data version from N−1 highest-ranked healthy nodes from the preference list.
 2. Waits until R−1 replies.
 3. Coordinator handles causal data versions through a vector clock.
 4. Returns all relevant data versions to the caller.

**get() process:**
 1. The coordinator generates a new data version and vector clock component.
 2. Saves new data locally.
 3. Sends the write request to N-1 highest-ranked healthy nodes from the preference list.
 4. The put() operation is considered successful after receiving W−1 confirmation.


## Request Handling through State Machine

---



# Follow-up
## Handle temporary failures
**Sloppy Quorum** & **Hinted Handoff**
- All read/write operations are performed on the first N healthy nodes from the preference list, which may not always be the first N nodes encountered while moving clockwise on the consistent hashing ring.
![在这里插入图片描述](https://img-blog.csdnimg.cn/89836bf41d31425a854b12949ad3ae98.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWXVueGlhbmdfSGU=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
	- Consider the example of Dynamo configuration given in the figure below with N=3.
	- In this example, if Server 1 is temporarily down or unreachable during a write operation, its data will now be stored on Server 4.
	- Thus, Dynamo transfers the replica stored on the failing node (i.e., Server 1) to the next node of the consistent hash ring that does not have the replica (i.e., Server 4).
	- This is done to avoid unavailability caused by a short-term machine or network failure and to maintain desired availability and durability guarantees.
	- The replica sent to Server 4 will have a hint in its metadata that suggests which node was the intended recipient of the replica (in this case, Server 1).
	- Nodes that receive hinted replicas will keep them in a separate local database that is scanned periodically.
	- Upon detecting that Server 1 has recovered, Server 4 will attempt to deliver the replica to Server 1.
	- Once the transfer succeeds, Server 4 may delete the object from its local store without decreasing the total number of replicas in the system.
- **Hinted handoff**
	- When a node is unreachable, another node can accept writes on its behalf.
	- The write is then kept in a local buffer and sent out once the destination node is reachable again.

## Handle conflicting data
Vector Clock with client-side resolution
![Vector Clock with client-side resolution](https://img-blog.csdnimg.cn/c73d1d167b774c2aa5f80e2827ae0e70.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWXVueGlhbmdfSGU=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

Conflict-free replicated data types (CRDTs)

 - To make use of CRDTs, we need to model our data in such a way that concurrent changes can be applied to the data in any order and will produce the same end result.

Last-write-wins (LWW)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgyMzIyMTc4MF19
-->