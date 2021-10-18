# Instance Metadata and User Data
**Instance metadata** is data about your instance that you can use to configure or manage the running instance.
You can also use instance metadata to access **user data** that you specified when launching your instance.



## Use IMDSv2
Two methods to access instance metadata:
 - Instance Metadata Service Version 1 (IMDSv1) – a **request/response** method
 - Instance Metadata Service Version 2 (IMDSv2) – a **session-oriented** method

The instance metadata service distinguishes between IMDSv1 and IMDSv2 requests based on whether, for any given request, either the `PUT` or `GET` headers, which are unique to IMDSv2, are present in that request.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTk2NzYwNzksLTYyNjQ2ODczM119
-->