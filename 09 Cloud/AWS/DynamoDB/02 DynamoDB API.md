# [DynamoDB API](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.API.html)
## [Control Plane](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.API.html#HowItWorks.API.ControlPlane)
`CreateTable`
`DescribeTable`
`ListTables`
`UpdateTable`
`DeleteTable`


## [Data Plane](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.API.html#HowItWorks.API.DataPlane)
### PartiQL - A SQL-Compatible Query Language
-  `ExecuteStatement`
	-  Reads multiple items from a table. You can also write or update a single item from a table.
-  `BatchExecuteStatement`

### Classic APIs
-  Creating Data
	-  `PutItem`
		- Writes a single item to a table.
	-  `BatchWriteItem`
		- Writes up to 25 items to a table.
		- You can also use `BatchWriteItem` for deleting multiple items from one or more tables.
-  Reading Data
	-  `GetItem`
		- Retrieves a single item from a table. You must specify the primary key for the item that you want.
	-  `BatchGetItem`
		- Retrieves up to 100 items from one or more tables.
	-  `Query`
		- Retrieves all items that have a specific partition key. You must specify the partition key value.
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
eyJoaXN0b3J5IjpbLTE4MTcwMjA0NzVdfQ==
-->