**Redundancy**
 - The duplication of critical components or functions of a system with the intention of increasing the reliability of the system, usually in the form of a backup or fail-safe, or to improve actual system performance.

**Replication**
 - Means sharing information to ensure consistency between redundant resources, such as software or hardware components, to improve reliability, fault-tolerance, or accessibility.
 - Replication is widely used in many database management systems (DBMS), usually with a master-slave relationship between the original and the copies.
 - The master gets all the updates, which then ripple through to the slaves.
 - Each slave outputs a message stating that it has received the update successfully, thus allowing the sending of subsequent updates.

![Failover Primary Server Secondary Server —Data Replication—y Active Data Mirrored Data ](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20Distributed%20System/01%20System%20Design/01%20System%20Design%20Tools/resource/replication/replication.png)

Checksum

-   While moving data between components, it is possible that the data fetched from a node may arrive corrupted.
-   Calculate a checksum and store it with data.

-   To calculate a checksum, a cryptographic hash function like MD5, SHA-1, SHA-256, or SHA-512 is used.

-   The hash function takes the input data and produces a string (containing letters and numbers) of fixed length; this string is called the checksum.

-   When a system is storing some data, it computes a checksum of the data and stores the checksum with the data.

-   When a client retrieves data, it verifies that the data it received from the server matches the checksum stored.
-   If not, then the client can opt to retrieve that data from another replica.
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI4MzcwMTQyMiwtMTU1MjkyNTI4MV19
-->