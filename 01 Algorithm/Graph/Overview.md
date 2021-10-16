# Overview
# Representation
# Algorithms
## Breadth-First Search
## Depth-First Search
## Topological Sort
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
## Connectivity
### Properties
Strong connectivity in digraphs
* Two vertices v and w are strongly connected if they are **mutually reachable**.
* A digraph is strongly connected if **all** its vertices are strongly connected to one another.
* Two vertices are strongly connected if and only if there exists a general directed **cycle** that contains them both.

Strong components
* **Reflexive**: Every vertex v is strongly connected to itself.
* **Symmetric**: If v is strongly connected to w, then w is strongly connected to v.
* **Transitive**: If v is strongly connected to w and w is strongly connected to x, then v is also strongly connected to x.

### Kosaraju's Algorithm
> Process
>  1. Build graph G and revserse order of G G^R^
>  2. For each unvisisted node, do a DFS and add the node to the stack when finishing visiting (Topological order)
>  3. For each unvisited node, do a DFS and add the node to the Strong connected component set.
>  ---
> Proof'
> * 1
> * 2

```java
    private Map<Character, List<Character>> adjacentList = new HashMap<>();
    private Map<Character, List<Character>> transposeAdjacentList = new HashMap<>();
    private Set<Set<Character>> scc = new HashSet<>();
    private int[] visited = new int[26];

    public void kosaraju(char[][] edges) {
        for (char[] edge : edges) {
            // Build graph using Adjacent List with given edges
            List<Character> neighbour = adjacentList.getOrDefault(edge[0], new ArrayList<>());
            adjacentList.putIfAbsent(edge[0], neighbour);
            neighbour.add(edge[1]);

            // Build transpose graph using Adjacent List with given edges
            List<Character> _neighbour = transposeAdjacentList.getOrDefault(edge[1], new ArrayList<>());
            transposeAdjacentList.putIfAbsent(edge[1], _neighbour);
            _neighbour.add(edge[0]);
        }

        // Build Topological order
        Deque<Character> topological = new ArrayDeque<>();
        for (char node : adjacentList.keySet()) {
            dfs_Topological(topological, node);
        }

        // Build Strong Connected Components
        while (!topological.isEmpty()) {
            char node = topological.pollFirst();
            if (visited[node - 'a'] != 3) {
                scc.add(dfs_StrongConnectedComponent(node, new HashSet<>()));
            }
        }
        System.out.println(scc);
    }

    private void dfs_Topological(Deque<Character> topological, char node) {
        if (visited[node - 'a'] == 0) {
            visited[node - 'a'] = 1;
            for (char neighbour : adjacentList.get(node)) {
                dfs_Topological(topological, neighbour);
            }
            topological.offerFirst(node); // Add to the top of the stack when finish visiting
            visited[node - 'a'] = 2;
        }
    }

    private Set<Character> dfs_StrongConnectedComponent(char node, Set<Character> scc) {
        if (visited[node - 'a'] != 3) {
            visited[node - 'a'] = 3;
            scc.add(node);
            if (transposeAdjacentList.containsKey(node)) {
                for (char nei : transposeAdjacentList.get(node)) {
                    dfs_StrongConnectedComponent(nei, scc);
                }
            }
        }
        return scc;
    }
```

## Minimum Spanning Trees

## Shortest Path Problem
>
> **Variants**
> * Single-source shortest-paths problem
> 	* Given a graph G = (V, E), we want to find a shortest path from a given source vertex s ∈ V to each vertex v ∈ V.
> * Single-destination shortest-paths problem
> 	* Find a shortest path to a given destination vertex t from each vertex v.
> 	* By reversing the direction of each edge in the graph, we can reduce this problem to a single-source problem.
> * Single-pair shortest-path problem
> 	* Find a shortest path from u to v for given vertices u and v.
> * All-pairs shortest-paths problem
>---
> **Properties**
> * Subpaths of shortest paths are shortest paths.
> * If the graph contains a **negative-weight cycle** reachable from the source node, then shortest parth from source node doesn't exist. 
> * A shortest path can't contain a negative-weight cycle nor a positive-weight cycle.
>---
> **Shortest-paths tree**
> - rooted at s is a directed subgraph G' = (V', E') where V' ⊆  V and E' ⊆ E, such that
> 	- V' is the set of vertices reachable from s in G
> 	- G' forms a rooted tree with root s, and
> 	- For all v ∈ V', the unique simple path from s to v in G' is a shortest path from s to v in G
> - Shortest paths are not necessarily unique, and neither are shortest-paths trees
> ---
> **Relaxation**
> - For each vertex v ∈ V , we maintain an attribute v.d, which is an upper bound on the weight of a shortest path from source s to v
> - Initialize
> - The process of relaxing an edge (u, v) consists of testing whether we can improve the shortest path to v found so far by going through u and, if so, updating v.d and v.π
> - Dijkstra’s algorithm and the shortest-paths algorithm for directed acyclic graphs relax each edge exactly once
> - The Bellman-Ford algorithm relaxes each edge |V| - 1 times


Properties of shortest paths and relaxation
- Triangle inequality
	- For any edge (u, v) ∈ E, we have δ(s, v) ≤ δ(s, u) + w(u, v)
- Upper-bound property
	- We alwasy have v.d ≥ δ(s, v) for all vertices v ∈ V, and once v.d achieves the value δ(s, v), it never changes
- No-path property
	- If there is no path from s to v, then we always have v.d = δ(s, v) = ∞
- Convergence property
	- If s   u -> is a shortest path in G for some u,v ∈ V , and if u.d = δ(s, u) at any time prior to relaxing edge (u, v), then v.d = δ(s, v) at all times afterward
- Path-relaxation property
	- If p = <v0, v1, ..., vk> is a shortest path from s = v0 to vk, and we relax the edges of p in the order (v0, v1), (v1, v2), ..., (vk-1, vk) then vk.d = δ(s, vk)
		- This property holds regardless of any other relaxation steps that occur, even if they are intermixed with relaxations of the edges of p
- Predecessor-subgraph propert
	- Once v.d = δ(s, v) for all v ∈ V , the predecessor subgraph is a shortest-paths tree rooted at s

### Single-Source Shortest Paths




#### Properties
* Subpaths of shortest paths are shortest paths
* To print

#### Bellman-Ford
#### Dijkastra
### All-Pairs Shortest Paths

## Maximum Flow
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI5MzQ5NTA1NF19
-->