# Reference
[Designing a Web Crawler - Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview/NE5LpPrWrKv)

[web_crawler - system-design-primer](https://github.com/donnemartin/system-design-primer/tree/master/solutions/system_design/web_crawler)

# Introduction
A web crawler is a software program which browses the World Wide Web in a methodical and automated manner.
 - It collects documents by recursively fetching links from a set of starting pages.

## Key Words
URL Duplicates Handling
Document Duplicates Handling
BFS vs. DFS
Path-Ascending Crawling
Robots.txt

# Requirements
## **Functional**
Given a set of URL seed, crawl and process the documents

## **Non-Functional**
Highly scale


# Estimation
**Traffic**
* Assume 15B pages to fetch per month
* 15B / (30 * 24 * 60 * 60) = 15B / 2.5M = 6K page/s

 **Storage**
* Assume 1MB each page
* Total storage 15B * 1MB = 15PB without replication

# High Level Design
![crawler](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20System%20Design/02%20System%20Design%20Demos/resource/crawler.png)

[Draw IO source](https://app.diagrams.net/#G1OHJKoBAQphtncRhJpp6ddwQFIVCf93BZ)


# Follow-up
How do we distribute URLs from *URL Frontier Message Queue* to *Crawler Serivers*
 - Use *Consistent Hash
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzA2NTYxODI2LDcyNDE4MzEyOCwxNzU4Nj
A0NzYsNzIyNzYxODcwLC03NTE4MjY1MjksLTQ1NTE5NzI2Myw5
NzMzMTQwNDVdfQ==
-->