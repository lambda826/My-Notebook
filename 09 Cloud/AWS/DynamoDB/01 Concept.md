# [What Is Amazon DynamoDB?](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html)
Amazon DynamoDB is a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability.
-	Can create database tables that can store and retrieve any amount of data and serve any level of request traffic.
-	On-demand backup capability.
	-	Point-in-time recovery.
-  Delete expired items from tables automatically.
-	High Availability and Durability.
	-	DynamoDB automatically spreads the data and traffic for your tables over a sufficient number of servers to handle your throughput and storage requirements, while maintaining consistent and fast performance.


# [Core Components of Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html)

## Tables
-  A _table_ is a collection of data.


## Items
-  An _item_ is a group of attributes that is uniquely identifiable among all of the other items.
-  Each item in the table has a unique identifier, or primary key, that distinguishes the item from all of the others in the table.
-  Other than the primary key, table is schemaless
	-  Neither the attributes nor their data types need to be defined beforehand. Each item can have its own distinct attributes.


## Attributes
An _attribute_ is a fundamental data element, something that does not need to be broken down any further.


## Primary Key
-  Uniquely identifies each item in the table, so that no two items can have the same key.
-  DynamoDB supports two different kinds of primary keys:
	- **Partition key**
	- **Partition key and sort key**


## Secondary Indexes
-  A _secondary index_ lets you query the data in the table using an alternate key, in addition to queries against the primary key.
-  DynamoDB supports two kinds of indexes:
	-  Global secondary index – An index with a partition key and sort key that can be different from those on the table.
	-  Local secondary index – An index that has the same partition key as the table, but a different sort key.


## DynamoDB Streams
DynamoDB Streams is an optional feature that captures data modification events in DynamoDB tables. The data about these events appear in the stream in near-real time, and in the order that the events occurred.

Each event is represented by a  _stream record_. If you enable a stream on a table, DynamoDB Streams writes a stream record whenever one of the following events occurs:
-  A new item is added to the table: The stream captures an image of the entire item, including all of its attributes.
-  An item is updated: The stream captures the "before" and "after" image of any attributes that were modified in the item.
-  An item is deleted from the table: The stream captures an image of the entire item before it was deleted.

Each stream record also contains the name of the table, the event timestamp, and other metadata. Stream records have a lifetime of 24 hours; after that, they are automatically removed from the stream.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNzQzNTI4NzEsLTg3NDg2NzU1OSwxMT
c1MDI0ODYxXX0=
-->