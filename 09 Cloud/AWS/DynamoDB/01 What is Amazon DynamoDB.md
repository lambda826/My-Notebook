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
	- 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzEzMTY0NjYxXX0=
-->