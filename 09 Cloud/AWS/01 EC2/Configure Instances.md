# [Instance Metadata and User Data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html)
**Instance metadata** is data about your instance that you can use to configure or manage the running instance.
You can also use instance metadata to access **user data** that you specified when launch your instance.


## [Use IMDSv2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/configuring-instance-metadata-service.html)
Two methods to access instance metadata:
 - Instance Metadata Service Version 1 (IMDSv1) – a **request/response** method
 - Instance Metadata Service Version 2 (IMDSv2) – a **session-oriented** method

The instance metadata service distinguishes between IMDSv1 and IMDSv2 requests based on whether, for any given request, either the `PUT` or `GET` headers, which are unique to IMDSv2.

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
**Tools for helping with the transition to IMDSv2**
 - If your software uses IMDSv1, use the following tools to help reconfigure your software to use IMDSv2.
	 - AWS software
		 - AWS SDKs and CLIs
	 - CloudWatch
		 - `MetadataNoToken`
	 - Updates to EC2 APIs and CLIs
		 - For existing instances, you can use the [modify-instance-metadata-options](https://docs.aws.amazon.com/cli/latest/reference/ec2/modify-instance-metadata-options.html) CLI command (or the [ModifyInstanceMetadataOptions](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_ModifyInstanceMetadataOptions.html) API) to require the use of IMDSv2.
		 - For new instances, you can use the [run-instances](https://docs.aws.amazon.com/cli/latest/reference/ec2/run-instances.html) CLI command (or the [RunInstances](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_RunInstances.html) API) and the `metadata-options` parameter to launch new instances that require the use of IMDSv2.
	 - IAM policies and SCPs

**Recommended path to requiring IMDSv2 access**
 - Step 1: At the start
	 - Update the SDKs, CLIs, and your software that use Role credentials on their EC2 instances to IMDSv2-compatible versions.
 - Step 2: During the transition
	 - Track your transition progress by using the CloudWatch metric `MetadataNoToken`.
 - Step 3: When everything is ready on all instances
   - For existing instances: You can require IMDSv2 use through the  [modify-instance-metadata-options](https://docs.aws.amazon.com/cli/latest/reference/ec2/modify-instance-metadata-options.html)  command. You can make these changes on running instances; you do not need to restart your instances.
    
	- For new instances: When launching a new instance, you can do one of the following:
	    - In the Amazon EC2 console launch instance wizard, set  **Metadata accessible**  to  **Enabled**  and  **Metadata version**  to  **V2**. For more information, see  [Step 3: Configure Instance Details](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/launching-instance.html#configure_instance_details_step).
	    - Use the  [run-instances](https://docs.aws.amazon.com/cli/latest/reference/ec2/run-instances.html)  command to specify that only IMDSv2 is to be used.
 - Step 4: When all of your instances are transitioned to IMDSv2
	 - The `ec2:MetadataHttpTokens`, `ec2:MetadataHttpPutResponseHopLimit`, and `ec2:MetadataHttpEndpoint` IAM condition keys can be used to control the use of the [RunInstances](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_RunInstances.html) and the [ModifyInstanceMetadataOptions](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_ModifyInstanceMetadataOptions.html) API and corresponding CLI.


## [Configure the instance metadata options](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/configuring-instance-metadata-options.html)


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5ODQ4NjkwNTIsLTY4NTA5NjQ4MCwxNj
c0NDY3Mjc4LDEyMDM0MDY5OTgsMTU1ODgyNDg5NSw5NTIzMzk3
NTEsMjAyNTkxODI5OCwxMjM2MzY0MjYxLDE2ODQwMjYyNjMsND
I5Nzk4MDMxLC02MjY0Njg3MzNdfQ==
-->