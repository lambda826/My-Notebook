# Reference
[Designing a Web Crawler - Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview/NE5LpPrWrKv)
[web_crawler - system-design-primer](https://github.com/donnemartin/system-design-primer/tree/master/solutions/system_design/web_crawler)

# Introduction
A web crawler is a software program which browses the World Wide Web in a methodical and automated manner.
 - It collects documents by recursively fetching links from a set of starting pages.

## Key Words
URL Duplicates Handling - Timestamp
Document Duplicates Handling - Checksum
BFS vs. DFS
Path-Ascending Crawling
Robots.txt

# Requirements
## **Functional**
Given a set of URL seed, crawl and process the documents

## **Non-Functional**
Highly scalable


# Estimation
**Traffic**
* Assume 15B pages to fetch per month
* 15B / (30 * 24 * 60 * 60) = 15B / 2.5M = 6K page/s

 **Storage**
* Assume 1MB each page
* Total storage 15B * 1MB = 15PB without replication

# High Level Design
![crawler](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20Distributed%20System/01%20System%20Design/02%20System%20Design%20Demos/resource/Crawler.png)
[Draw IO source](https://app.diagrams.net/#G1OHJKoBAQphtncRhJpp6ddwQFIVCf93BZ)


# Follow-up
How do we distribute URLs from *URL Frontier Message Queue* to *Crawler Serivers*
 - Use *Consistent Hashing* algorithm
	 - Process URLs with Hash function to get the key, and then map the keys to the servers.

How do we avoid downloading duplicate documents
 - Caclulate checksum for each processed document and store it in the database.
 - Before processing a document, check whether it exists in the database.


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA2Njk0NTE4MywtMTA1MDk3ODA2Nl19
-->