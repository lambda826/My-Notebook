[BigTable: How to Design a Wide-column Storage System? - Grokking the System Design Interview ](https://www.educative.io/courses/grokking-adv-system-design-intvw/mEG04BK3M79)

# Introduction
## What is BigTable
BigTable is a **distributed** and **massively scalable** wide-column store. It is designed to store huge sets of structured data.
 -	In terms of the CAP theorem, BigTable is a CP system, i.e., **it has strictly consistent reads and writes**.
 -	BigTable can be used as an input source or output destination for [MapReduce](https://hadoop.apache.org/docs/r1.2.1/mapred_tutorial.html) jobs.

## BigTable Use Cases
 - Store large amounts of data and perform thousands of queries per second on that data.
 -	BigTable is suitable to store large datasets that are greater than one TB where each row is less than 10MB. Since BigTable does not provide ACID (atomicity, consistency, isolation, durability) properties or transaction support, Online Transaction Processing ([OLTP](https://en.wikipedia.org/wiki/Online_transaction_processing)) applications with transaction processes should not use BigTable.
 -	For BigTable, data should be structured in the form of key-value pairs or rows-columns. Non-structured data like images or movies should not be stored in BigTable.

**BigTable can be used to store the following types of data:**
 -  Time series data: As the data is naturally ordered
 -  Internet of Things (IoT) data: Constant streams of writes
 -  Financial Data: Often represented as time-series data

# BigTable Data Model
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjIxMjYyODI5LC0xNjcxMjg5MDI3LC0yMD
g4NzQ2NjEyXX0=
-->