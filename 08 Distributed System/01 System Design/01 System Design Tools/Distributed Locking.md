# Reference
[##### Chubby: How to Design a Distributed Locking Service? - # Grokking the Advanced System Design Interview](https://www.educative.io/courses/grokking-adv-system-design-intvw/YMzjoN4RzN9)

# Chubby: Introduction
## What is Chubby?
Chubby is a service that provides a distributed locking mechanism and also stores small files. Internally, it is implemented as a **key/value store** that also provides a locking mechanism on each object stored in it. It is extensively used in various systems inside Google to provide storage and coordination services for systems like **GFS** and **BigTable**. Apache **ZooKeeper** is the open-source alternative to Chubby.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY0OTcxOTAyN119
-->