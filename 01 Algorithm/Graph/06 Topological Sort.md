# Topological Sort
Implementation
* DFS
  * Iterate every node in the Graph
  * For each node, if it's not visited, mark it as visited, recursively DFS visit every neighbour of current node
  * After the visiting each neighbour, add current node to head of the order list.
* BFS
  * Additional data structure to store the indegree of each node
  * Enqueue all nodes which have zero indegree
  * Dequeue the current node and add it into the orderList
  * Update indegree of the neighbours of the current node
    * Enqueue if the beighbour node has zero indegree
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkwNDc3ODQzXX0=
-->