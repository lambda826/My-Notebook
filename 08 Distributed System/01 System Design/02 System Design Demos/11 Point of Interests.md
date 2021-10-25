# Reference

[# Designing Yelp or Nearby Friends - Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview/B8rpM8E16LQ)

# Introduction
Proximity servers are used to discover nearby attractions like places, events, etc.
https://www.youtube.com/watch?v=hykjbT5Z0oE&list=PLCfguwhZH5DnHl2yldI781yR6FAgky0Np&index=1
https://www.youtube.com/watch?v=Hr5UJnKxwyg&list=PLCfguwhZH5Dmi-N_EXR1h4bAt16EYpyc1&index=4
https://www.youtube.com/c/TheInterviewSage/videos

## Key Words
Read Heavy
QuadTree
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
- Assume 100K QPS

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
 - Assume we don’t want to have more than 500 places in a grid so that we can have a faster searching. So, whenever a grid reaches this limit, we break it down into four grids of equal size and distribute places among them.



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
eyJoaXN0b3J5IjpbLTE3Mjk4MDU2MjcsNjQ5MDA4NTE4LDIxMj
IxNTYwMjgsLTEzNzgzODM1MjksMTMyMjQ0ODUzMSwzMzg1OTA1
MzgsMTY2MDQxMzM0NSwtOTQ3ODgyNTcxLDEyOTEwOTQ5MjYsLT
EwNTk1NjU2MDcsLTE1MjM1NzY5OTMsLTg0ODIyMzUwMl19
-->