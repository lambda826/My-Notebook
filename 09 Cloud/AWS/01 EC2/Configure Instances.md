# Instance Metadata and User Data
**Instance metadata** is data about your instance that you can use to configure or manage the running instance.
You can also use instance metadata to access **user data** that you specified when launching your instance.



## Use IMDSv2
Two methods to access instance metadata:
 - Instance Metadata Service Version 1 (IMDSv1) – a **request/response** method
 - Instance Metadata Service Version 2 (IMDSv2) – a **session-oriented** method

The instance metadata service distinguishes between IMDSv1 and IMDSv2 requests based on whether, for any given request, either the `PUT` or `GET` headers, which are unique to IMDSv2, are present in that request.

### How Instance Metadata Service Version 2 Works
MDSv2 uses **session-oriented** requests.
 - With session-oriented requests, you create a session token that defines the session duration.

Use a  Linux  shell script and IMDSv2 to retrieve the top-level instance metadata items:
 - Creates a session token
	 - Stores the session token header in a variable named  `TOKEN`
 - Requests the top-level metadata items using the token
	 - The request must include the followings when Use IMDSv2 to request instance metadata:
		 - Use a  `PUT`  request to initiate a session to the instance metadata service.
			 - The  `PUT`  request returns a token that must be included in subsequent  `GET`  requests to the instance metadata service.
			 - The token is required to access metadata using IMDSv2.
		 - Include the token in all `GET` requests to the instance metadata service.
			 - The token is an instance-specific key.
			 - The `PUT` request must include a header that specifies the time to live (TTL) for the token in seconds.


### Transition to using Instance Metadata Service Version 2

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA4OTc1MDQ0NCwxNjg0MDI2MjYzLDQyOT
c5ODAzMSwtNjI2NDY4NzMzXX0=
-->