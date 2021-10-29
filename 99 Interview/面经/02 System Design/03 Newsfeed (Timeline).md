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

1.  **"Pull" model or Fan-out-on-load:** This method involves keeping all the recent feed data in memory so that users can pull it from the server whenever they need it. Clients can pull the feed data on a regular basis or manually whenever they need it. Possible problems with this approach are a) New data might not be shown to the users until they issue a pull request, b) It’s hard to find the right pull cadence, as most of the time pull requests will result in an empty response if there is no new data, causing waste of resources.
    
2.  **"Push" model or Fan-out-on-write:**  For a push system, once a user has published a post, we can immediately push this post to all the followers. The advantage is that when fetching feed you don’t need to go through your friend’s list and get feeds for each of them. It significantly reduces read operations. To efficiently handle this, users have to maintain a [Long Poll](https://en.wikipedia.org/wiki/Push_technology#Long_polling) request with the server for receiving the updates. A possible problem with this approach is that when a user has millions of followers (a celebrity-user) the server has to push updates to a lot of people.

3.  **Hybrid:** An alternate method to handle feed data could be to use a hybrid approach, i.e., to do a combination of fan-out-on-write and fan-out-on-load. Specifically, we can stop pushing posts from users with a high number of followers (a celebrity user) and only push data for those users who have a few hundred (or thousand) followers. For celebrity users, we can let the followers pull the updates. Since the push operation can be extremely costly for users who have a lot of friends or followers, by disabling fanout for them, we can save a huge number of resources. Another alternate approach could be that, once a user publishes a post, we can limit the fanout to only her online friends. Also, to get benefits from both the approaches, a combination of ‘push to notify’ and ‘pull for serving’ end-users is a great way to go. Purely a push or pull model is less versatile.

[Draw IO source]()

---
# Follow-up
How to avoid querying full dataset from the database?
 - When making the `timeline` request, set a timestamp as a condition that only retrieve the createOn which is greater than this parameter.
 - Offline generation news feed (last timestamp)


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ1NDA1NzU1Miw3MTEyOTc0MDYsMjA4MD
U0MDQ5OCwxMzE1ODQ5NjkwLDIwNDYyNTczNThdfQ==
-->