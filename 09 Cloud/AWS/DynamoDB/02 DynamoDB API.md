# [DynamoDB API](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.API.html)
## [Control Plane](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.API.html#HowItWorks.API.ControlPlane)
`CreateTable`
`DescribeTable`
- Returns information about a table, such as its primary key schema, throughput settings, and index information.
`ListTables`
`UpdateTable`
- Modifies the settings of a table or its indexes, creates or removes new indexes on a table, or modifies DynamoDB Streams settings for a table.
`DeleteTable`


## [Data Plane](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.API.html#HowItWorks.API.DataPlane)
### PartiQL - A SQL-Compatible Query Language
-  `ExecuteStatement`
	- Reads multiple items from a table. 
	- Write or update a single item from a table.
-  `BatchExecuteStatement`
	- Writes, updates or reads multiple items from a table.
	- This is more efficient than `ExecuteStatement` because your application only needs a single network round trip to write or read the items.

### Classic APIs
-  Creating Data
	-  `PutItem`
		- Writes a single item to a table.
	-  `BatchWriteItem`
		- Writes up to 25 items to a table.
		- You can also use `BatchWriteItem` for deleting multiple items from one or more tables.
-  Reading Data
	-  `GetItem`
		- Retrieves a single item from a table.
	-  `BatchGetItem`
		- Retrieves up to 100 items from one or more tables.
	-  `Query`
		- Retrieves all items that have a specific partition key.
		- Optionally, you can apply a condition to the sort key values so that you only retrieve a subset of the data that has the same partition key.
	-  `Scan`
		- Retrieves all items in the specified table or index.
		- Optionally, you can apply a filtering condition to return only the values that you are interested in and discard the rest.
-  Updating Data
	-  `UpdateItem`
-  Deleting Data
	-  `DeleteItem`
	-  `BatchWriteItem`


## [DynamoDB Streams](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.API.html#HowItWorks.API.Streams)
-  `ListStreams`
-  `DescribeStream`
-  `GetShardIterator`
-  `GetRecords`


## [Transactions](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.API.html#HowItWorks.API.Transactions)
### PartiQL - A SQL-Compatible Query Language
-  `ExecuteTransaction`

### Classic APIs
-  `TransactWriteItems`
-  `TransactGetItems`

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1OTQwNTE2NzcsMzk0ODM1MjM5LC0xOD
E3MDIwNDc1XX0=
-->