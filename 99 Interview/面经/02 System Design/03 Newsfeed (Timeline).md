# Reference

[Instagram 系统设计题解 - acecodeinterview](https://acecodeinterview.com/instagram/)
[Design the Twitter timeline and search - system-design-primer](https://github.com/donnemartin/system-design-primer/blob/master/solutions/system_design/twitter/README.md)
[Designing Instagram - Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview/m2yDVZnQ8lG)
[Designing Twitter - Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview/m2G48X18NDO)
[Designing Facebook’s Newsfeed - Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview/gxpWJ3ZKYwl)

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
- Assume 5 Post per user per day
- Assume 10 read requests per user per day
- 

## **Storage**
- Assume 1MB per Post

# High Level Design
![](https://raw.githubusercontent.com/lambda826/My-Notebook/master/999%20Resource/News%20Feed.png)

![](https://raw.githubusercontent.com/lambda826/My-Notebook/master/999%20Resource/News%20Feed2.png)

[Draw IO source]()

---
# Follow-up
How to avoid querying full dataset from the database?
 - When making the `timeline` request, set a timestamp as a condition that only retrieve the createOn which is greater than this parameter.
 - Offline generation news feed (last timestamp)


<!--stackedit_data:
eyJoaXN0b3J5IjpbNzExMjk3NDA2LDIwODA1NDA0OTgsMTMxNT
g0OTY5MCwyMDQ2MjU3MzU4XX0=
-->