# Background
 - Horizontal Scalability.
 - Uniform Distribution.

# Implementation

## Creating the Hash Key Space - Hashing Ring
![Hasing Ring](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20System%20Design/01%20System%20Design%20Tools/resource/consistent%20hashing/01%20Hasing%20Ring.png)
Consider we have a hash function that generates integer hash values in the range [0, Integer.MAX_VALUE)
Representing the hashSpace as a Ring: Imagine that these integers generated above is placed on a ring such that the last value wraps around.

## Placing Nodes in Key Space (Hash Ring)
![Nodes Placement](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20System%20Design/01%20System%20Design%20Tools/resource/consistent%20hashing/02%20Key%20Placement.png)
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTM0MTM1MzU2XX0=
-->