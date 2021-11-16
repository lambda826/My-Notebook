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
- Nameing service (like DNS)
- Storage (small objects that rarely change)
	- ![]()


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY0NjE4ODc3MSwtMTY3MDE3NzAyOV19
-->