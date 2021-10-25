# Reference

[# Designing Yelp or Nearby Friends - Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview/B8rpM8E16LQ)

[Quadtree - wikipedia](https://en.wikipedia.org/wiki/Quadtree)

# Introduction
Proximity servers are used to discover nearby attractions like places, events, etc.
https://www.youtube.com/watch?v=hykjbT5Z0oE&list=PLCfguwhZH5DnHl2yldI781yR6FAgky0Np&index=1
https://www.youtube.com/watch?v=Hr5UJnKxwyg&list=PLCfguwhZH5Dmi-N_EXR1h4bAt16EYpyc1&index=4
https://www.youtube.com/c/TheInterviewSage/videos

## Key Words
Read Heavy
Quadtree
Geohash
Hilbert curve

https://blog.csdn.net/wdwyf999/article/details/89957490


# Requirements
## **Functional**
- Add/update/delete places with location
- Query nearby locations given a location

## **Non-Functional**
- Low latency with heavy search load

---
# Estimation
## **Traffic**
- Assume 10M DAU 
- Assume 10 Queries per user per day.
- QPS = (10M * 10) / (24 * 60 * 60) = 1K

## **Storage**
-

# High Level Design
## Architecture
![POI](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20Distributed%20System/01%20System%20Design/02%20System%20Design%20Demos/resource/POI.png)
[Draw IO source](https://app.diagrams.net/#G1HA21GylJ42Z1oZyYARWOKjJJ4f9iuiUc)

## Algorithm Model: How to Find NearBy?
### Option 1: SQL Solution
1. We store  `Latitude (X)` / `Longitute (Y)` for each entity 
2. Do a SQL query for `NearBy (D)` query: `([X + D, X - D], [Y + D, Y - D])`
3. Low performance: O(N)

### Option 2: Grid
![POI Grid](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20Distributed%20System/01%20System%20Design/02%20System%20Design%20Demos/resource/POI%20Grid.png)
1. Divide the whole map into grids.
2. Group locations into grids.
3. Based on given `Location` and `Radius`, find all neighbouring grids.
4. Aggregate all `Locations` in those grids.
5. We can cache the grids (`GridId`, `List<Location>`) in memory.

Problem
- Location is not uniformly distributed among grids.
- This problem can be solved if we can dynamically adjust our grid size such that whenever we have a grid with a lot of places we break it down to create smaller grids.

### Option 3: QuadTree (Dynamic Size Grids)
![QuadTree](https://raw.githubusercontent.com/lambda826/My-Notebook/master/999%20Resource/QuadTree.png)
- Assume we don’t want to have more than 500 places in a grid so that we can have a faster searching.
	- So, whenever a grid reaches this limit, we break it down into four grids of equal size and distribute places among them.
- **What data-structure can hold this information?**
	- A tree in which each node has four children.
		- All the leaf nodes will represent the grids that cannot be further broken down.
- **How will we build a QuadTree?**
	- Start with one node that will represent the whole world in one grid.
	- Break it down into four nodes and distribute locations among them.
	- Keep repeating this process with each child node until there are no nodes left with more than 500 locations.
- **How will we find the grid for a given location?**
	- Start with the root node and search downward to find our required node/grid.
	- At each step, see if the current node we are visiting has children.
		- If it has, we will move to the child node that contains our desired location and repeat this process.
		- If the node does not have any children, then that is our desired node.
- **How will we find neighboring grids of a given grid?**
	- Since only leaf nodes contain a list of locations, we can connect all leaf nodes with a doubly linked list.
		- This way we can iterate forward or backward among the neighboring leaf nodes to find out our desired locations.
		- Another approach for finding adjacent grids would be through parent nodes.
			- We can keep a pointer in each node to access its parent, and since each parent node has pointers to all of its children, we can easily find siblings of a node.
			- We can keep expanding our search for neighboring grids by going up through the parent pointers.

### Option 4: Hilbert Curve


# Follow-up
How can we paritition database?
 - Sharding based on regions
	 - Hotspot issue (read).
	 - Uniform distribution (write). 
 - Sharding based on `LocationID`
	 - Have to query all db instance and aggregate the results

How can we do a search and present the results on the map?
 - Build `inverted index` on top of the entities, whose `key` is the **key words** and `value` is the properties of the entities.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MTU3MzAwNTcsNTkzNjg4NzcsLTE1NT
YxMDk1MjIsNjQ5MDA4NTE4LDIxMjIxNTYwMjgsLTEzNzgzODM1
MjksMTMyMjQ0ODUzMSwzMzg1OTA1MzgsMTY2MDQxMzM0NSwtOT
Q3ODgyNTcxLDEyOTEwOTQ5MjYsLTEwNTk1NjU2MDcsLTE1MjM1
NzY5OTMsLTg0ODIyMzUwMl19
-->