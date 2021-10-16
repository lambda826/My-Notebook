# Background
 - Horizontal Scalability.
 - Uniform Distribution.

# Implementation

## Creating the Hash Key Space - Hashing Ring
![Hasing Ring](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20System%20Design/01%20System%20Design%20Tools/resource/consistent%20hashing/01%20Hasing%20Ring.png)

 - Consider we have a hash function that generates integer hash values in the range [0, Integer.MAX_VALUE)
 - Representing the hashSpace as a Ring: Imagine that these integers generated above is placed on a ring such that the last value wraps around.


## Placing Nodes and Targeting Keys
![Nodes Placement](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20System%20Design/01%20System%20Design%20Tools/resource/consistent%20hashing/02%20Key%20Placement.png)
 - Placing Nodes in Key Space (Hash Ring)
    - Using the hash function, we map each node to a specific place on the ring.
 - Determining Placement of Keys on Nodes
	- To find which node an incoming key resides on we do the following:
		- Run the key through the same hash function we used to determine node placement on the ring.​
		- After hashing the key, we'll get an integer value which will be contained in the hash space, i.e., it can be mapped to some postion in the hash ring.
		- There can be two cases:
			- The hash value of the key maps directly onto the same hash vale of a node – in which case we place it on that node.
			- The hash value maps to a place on the ring which does not have a node.
				- In this case, we travel clockwise on the ring from the point where the key mapped to untill we find the first node.


# Scaling
## Scale Up
![Scale up](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20System%20Design/01%20System%20Design%20Tools/resource/consistent%20hashing/03%20Scale%20Up.png)
Adding a node to the Ring:
 - If we add another node to the hash Ring, server 4, we'll need to remap the keys.
 - However, ONLY the keys that reside between server 3 and server 0 needs to be remapped to server 4.
 - On an average , we'll need to remap only k/n keys , where k is the number of keys and n is the number of servers.
 - This is in sharp contrast to our modulo based placement approach where we needed to remap nearly all the keys.

## Scale Down
![Scale Down](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20System%20Design/01%20System%20Design%20Tools/resource/consistent%20hashing/04%20Scale%20Down.png)

Removing a nodefrom the ring
 - A server might go down in production and our consistent hashing scheme ensures that it has minimal effect on the number of keys and servers affected.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAzMTQ2MDYyOV19
-->