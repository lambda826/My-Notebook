# Reference
[Designing Facebook Messenger - Grokking the System Design Interview ](https://www.educative.io/courses/grokking-the-system-design-interview/m2ygV4E81AR)
[8 Most Popular Instant Messaging & Chat Protocols](https://www.cometchat.com/blog/popular-chat-and-instant-messaging-protocols)
[Web Sockets vs. XMPP: Which Is Better For Chat Application?](https://medium.com/@thinkwik/web-sockets-vs-xmpp-which-is-better-for-chat-application-113e3520b327)
[XMPP vs. WebSockets: Comparing Instant Messaging Protocols
](https://www.cometchat.com/blog/xmpp-vs-websockets-instant-messaging-protocol-comparison)


# Introduction
## Key Words
1 : 1 Read-Write Ratio

# Requirements
## Functional
- Support one-on-one chat.
- Support group chat.
- Track online status.
- Persist chat history
- Notification

## Non-Functional
- Low latency
- High consistency
- High availability


# Estimation
## Traffic
- Assume 500M DAU
## Storage


# High Level Design
In a chat system, clients can be either mobile applications or web applications.
- Clients do not communicate directly with each other. Instead, each client connects to a chat service.

![Chat Service](https://raw.githubusercontent.com/lambda826/My-Notebook/master/999%20Resource/Chat%20Service.png)
The chat service must support the following functions:
- Receive messages from other clients.
- Find the right recipients for each message and relay the message to the recipients.
- If a recipient is not online, hold the messages for that recipient on the server until she is online.




[Draw IO source]()



# Follow-up


<!--stackedit_data:
eyJoaXN0b3J5IjpbODgyNTQ0Mjg2LDgxODAzNjk2NiwtNTUzMT
QyODUxLDEwNTcwNjcwMDMsLTE1OTY3NTg4ODcsLTcwNzQwMTE3
NV19
-->