# Reference

[Instagram 系统设计题解 - acecodeinterview](https://acecodeinterview.com/instagram/)
[Designing Instagram - Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview/m2yDVZnQ8lG)
[Designing Twitter - Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview/m2G48X18NDO)
[Designing Facebook’s Newsfeed - Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview/gxpWJ3ZKYwl)



--- 
# Introduction
Application
 - Instagram
 - Facebook
 - Twitter

## Key Words
Read heavy
Ranking
Hotspot

# Requirements
## **Functional**
 - Post feed with or without images/videos
 - Following/follower
 - Timeline

## **Non-Functional**
 - High availability
 - Acceptable latency
 - Eventual consistency

# Estimation
## **Traffic**
- Assume 100M DAU
- Assume 2 Post per user per day
- 
- 

## **Storage**
- Assume 1MB per Post

# High Level Design
[Draw IO source]()

---
# Follow-up
How to avoid querying full dataset from the database?
 - When making the `timeline` request, set a timestamp as a condition that only retrieve the createOn


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NDk3Nzk1MDYsMTM5ODIwNTUyNywtNj
I3ODczNDMwLDE1MDY2NjQ3OTYsLTE3ODQ0OTY0MjcsMTU4NTQ3
NzAwOSwtMzY5MjMwMjI2LDE0MDU0NDM5ODQsLTE2NjQ4NTcxNz
ddfQ==
-->