# Reference
[Designing Twitter Search - Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview/xV9mMjj74gE)
[System Design Interview: Search Engine - medium](https://medium.com/double-pointer/system-design-interview-search-engine-edb66b64fd5e)


# Introduction
## Key Words
Inverted Index
 - https://blog.csdn.net/CrankZ/article/details/80615789
 - https://blog.csdn.net/LJJZJ/article/details/99955858

Stemming
Stop words
Spelling correction
Normalization
Conjunctive Search (and)
Disjunctive Search (or)


# Requirements
## **Functional**
Given search terms, return documents which contain the terms.

## **Non-Functional**
Highly available


# Estimation
**Traffic**
* Assume 500M searches per day
* QPS: 500M / (24 * 60 * 60) = ~60K search/s

 **Storage**
* Assume 500M new documents per day
* Assume 1KB per document
* Total storage increament per day: 500M * 1KB = 500 GB/day


# High Level Design

![search engine](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20System%20Design/02%20System%20Design%20Demos/resource/search%20engine.png)
[Draw IO source](https://app.diagrams.net/#G1nZpAJ1gY0EXcrLiRGmfU5tJI6XbDJo0V)


# Follow-up
How do we generated unique documentID?
 - UUID


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTczNzI2ODMwOSwtMTA5OTAyMTUwNiwtOT
cwNjQyMDcxLDQ2MzY3ODA4MywxMjQ0MjIzNjkyLC00NzQzODEw
NzgsLTEzOTY4NzgxMTgsNzMwOTk4MTE2XX0=
-->