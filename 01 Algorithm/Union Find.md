# Dynamic Connectivity Problem
-  The input is a sequence of pairs of integers
	-  Where each integer represents an object of some type and we are to interpret the pair p q as meaning "p is connected to q".
	-  We assume that “is connected to” is an equivalence relation, which means that it is
		-  Reflexive
		-  Symmetric
		-  Transitive


# Applications
-  Networks
-  Variable-name equivalence
-  Mathematical sets


# Implementations
![Union Find](https://raw.githubusercontent.com/lambda826/My-Notebook/master/999%20Resource/Union%20Find.png)
-  **Weighted quick-union**
	-  Rather than arbitrarily connecting the second tree to the first for union()
-  **We keep track of the size of each tree and always connect the smaller tree to the larger**
-  **Optimal algorithms (path compression)**
	-  Ideally, we would like every node to link directly to the root of its tree, but we do not want to pay the price of changing a large number of links, as we did in the quick-find algorithm
		-  To implement path compression, **we just add another loop to find() that sets the id[] entry corresponding to each node encountered along the way to link directly to the root**
			-  The net result is to flatten the trees almost completely, approximating the ideal achieved by the quick-find algorithm


## Data Structure
-  int[] root (index is subtree, value is root)
-  int[] size
-  Map<Integer, Integer> root
-  Map<Integer, Integer> size


## Operations
-  Find(index)
	- Returns an integer component identifier for a given site.
-  Union(index1, index2)
	- Merges two components if the two sites are in different components.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkyMzUzNTMxOSwtMTA4NDYzMjE2MiwtNz
A5OTgxNzE5LDk0MTA3OTYxMywxOTg0MDY3Nzc4XX0=
-->