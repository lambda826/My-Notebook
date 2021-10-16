# Background
 - Horizontal Scalability.
 - Uniform Distribution.

# Implementation

## Creating the Hash Key Space - Hashing Ring
![Hasing Ring](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20System%20Design/01%20System%20Design%20Tools/resource/consistent%20hashing/01%20Hasing%20Ring.png)

 - Consider we have a hash function that generates integer hash values in the range [0, Integer.MAX_VALUE)
 - Representing the hashSpace as a Ring: Imagine that these integers generated above is placed on a ring such that the last value wraps around.


## Node Placement and Key Targeting
![Nodes Placement](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20System%20Design/01%20System%20Design%20Tools/resource/consistent%20hashing/02%20Key%20Placement.png)
 - Placing Nodes in Key Space (Hash Ring)
    - Using the hash function, we map each node to a specific place on the ring.
 - Determining Placement of Keys on Nodes
	- To find which database server an incoming key resides on (either to insert it or query for it ), we do the following:
		- Run the key through the same hash function we used to determine db server placement on the ring.​
		- After hashing the key, we'll get an integer value which will be contained in the hash space, i.e., it can be mapped to some postion in the hash ring.
		- There can be two cases:
			- -   The hash value of the key maps directly onto the same hash vale of a db server – in which case we place it on that server.
-   The hash value maps to a place on the ring which does not have a db server.

-   In this case, we travel clockwise on the ring from the point where the key mapped to untill we find the first db server.
-   Once we find the first db server travelling clockwise on the ring, we insert the key there.
-   The same logic would apply while trying to find a key in the ring.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTczMzczNzAzN119
-->