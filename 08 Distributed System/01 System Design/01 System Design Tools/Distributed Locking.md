# Reference
[Chubby: How to Design a Distributed Locking Service? - # Grokking the Advanced System Design Interview](https://www.educative.io/courses/grokking-adv-system-design-intvw/YMzjoN4RzN9)

# Chubby: Introduction
## What is Chubby?
- Chubby is a service that provides a distributed locking mechanism and also stores small files.
	- Internally, it is implemented as a **key/value store** that also provides a locking mechanism on each object stored in it.

## Chubby Use Casees
- Distributed locking mechanism
	- ![Chubby Distributed Locking Service.png](https://raw.githubusercontent.com/lambda826/My-Notebook/master/999%20Resource/Chubby%20Distributed%20Locking%20Service.png)
- Leader/master election
	- ![Chubby Leader Election.png](https://raw.githubusercontent.com/lambda826/My-Notebook/master/999%20Resource/Chubby%20Leader%20Election.png)
- Nameing service (like DNS)
	- ![Chubby DNS.png](https://raw.githubusercontent.com/lambda826/My-Notebook/master/999%20Resource/Chubby%20DNS.png)
- Storage (small objects that rarely change)
	- ![Chubby Storage Service for Small Objects.png](https://raw.githubusercontent.com/lambda826/My-Notebook/master/999%20Resource/Chubby%20Storage%20Service%20for%20Small%20Objects.png)

## When not to use Chubby
-   Bulk storage is needed.
-   Data update rate is high.
-   Locks are acquired/released frequently.
-   Usage is more like a publish/subscribe model.


## Terms
Cell
Server
Client Library
APIs


<!--stackedit_data:
eyJoaXN0b3J5IjpbNjcxMzI0NDQyLDE2NTI4OTk3ODMsNzIxOT
I0NDAxLDEwMDI1MDk3NTUsLTE2NzAxNzcwMjldfQ==
-->