Strong Consistency (Immediate Consistency, Synchronous Replication)

-   This means that data viewed immediately after an update will be consistent for all observers of the entity.
-   To have strong consistency, system must compromise on the scalability and performance of their application.

-   Simply put, data has to be locked during the period of update or replication process to ensure that no other processes are updating the same data.

-   With synchronous replication, when a source commits a transaction, all replicas have also committed the transaction before the source returns to the session that performed the transaction.

-   Synchronous replication means failover from the source to any replica is possible at any time.
-   The drawback of fully synchronous replication is that there might be a lot of delay to complete a transaction.

-   ![Strong Consistency](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20System%20Design/01%20System%20Design%20Tools/resource/consistency%20model/Strong%20Consistency.png)

Eventual Consistency (Week Consistency, Asynchronous Replication)

-   容忍节点故障只是需要复制的一个原因。另两个原因是可扩展性和降低延迟。
-   单领导者的主从复制算法要求所有写入都由单个节点处理，但只读查询可以由任何节点处理。

-   对于 Read heavy 的场景，我们往往创建很多从库，并将读请求分散到所有的从库上去。

-   这样能减小主库的负载，并允许向最近的节点发送读请求。
-   当然这只适用于异步复制——如果尝试同步复制，则单个节点故障将使整个系统无法写入。

-   当用户从异步从库读取时，如果此异步从库落后，他可能会看到过时的信息。

-   这种不一致只是一个暂时的状态——如果等待一段时间，从库最终会赶上并与主库保持一致。这称为最终一致性。

-   ![Weak Consistency](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20System%20Design/01%20System%20Design%20Tools/resource/consistency%20model/Weak%20Consistency.png)

Semisynchronous Replication - [https://dev.mysql.com/doc/refman/8.0/en/replication-semisync.html](https://dev.mysql.com/doc/refman/8.0/en/replication-semisync.html)

-   The source waits until at least one replica has received and logged the events (the required number of replicas is configurable), and then commits the transaction.

-   The source does not wait for all replicas to acknowledge receipt, and it requires only an acknowledgement from the replicas, not that the events have been fully executed and committed on the replica side.
-   Semisynchronous replication therefore guarantees that if the source crashes, all the transactions that it has committed have been transmitted to at least one replica.

-   Compared to asynchronous replication, semisynchronous replication provides improved data integrity, because when a commit returns successfully, it is known that the data exists in at least two places. Until a semisynchronous source receives acknowledgment from the required number of replicas, the transaction is on hold and not committed.
-   Compared to fully synchronous replication, semisynchronous replication is faster, because it can be configured to balance your requirements for data integrity (the number of replicas acknowledging receipt of the transaction) with the speed of commits, which are slower due to the need to wait for replicas.

Read-after-Write Consistency - [https://avikdas.com/2020/04/13/scalability-concepts-read-after-write-consistency.html](https://avikdas.com/2020/04/13/scalability-concepts-read-after-write-consistency.html)

-   Read-after-write consistency is the ability to view changes (read data) right after making those changes (write data).

-   For example, if you have a user profile and you change your bio on the profile, you should see the updated bio if you refresh the page. There should be no delay during which the old bio shows up.

单调读

-   用户从某从库查询到了一条记录，再次刷新后发现此记录不见了，就像遇到时光倒流。如果用户从不同从库进行多次读取，就可能发生这种情况。
-   单调读可以保证这种异常不会发生。
-   单调读意味着如果一个用户进行多次读取时，绝对不会遇到时光倒流，即如果先前读取到较新的数据，后续读取不会得到更旧的数据。
-   单调读比强一致性更弱，比最终一致性更强。
-   实现单调读取的一种方式是确保每个用户总是从同一个节点进行读取（不同的用户可以从不同的节点读取），比如可以基于用户ID的哈希值来选择节点，而不是随机选择节点。

Sequential Consistency

Causal Consistency

-   在本文中阐述因果一致性可能并不是一个很好的时机，因为它往往发生在分区（也称为分片）的分布式数据库中。
-   分区后，每个节点并不包含全部数据。不同的节点独立运行，因此不存在全局写入顺序。如果用户A提交一个问题，用户B提交了回答。问题写入了节点A，回答写入了节点B。因为同步延迟，发起查询的用户可能会先看到回答，再看到问题。
-   为了防止这种异常，需要另一种类型的保证：因果一致性。 即如果一系列写入按某个逻辑顺序发生，那么任何人读取这些写入时，会看见它们以正确的逻辑顺序出现。
-   这是一个听起来简单，实际却很难解决的问题。一种方案是应用保证将问题和对应的回答写入相同的分区。但并不是所有的数据都能如此轻易地判断因果依赖关系。如果有兴趣可以搜索向量时钟深入此问题。
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMDgwODk2MjMsNDA0MjkyOTY5XX0=
-->