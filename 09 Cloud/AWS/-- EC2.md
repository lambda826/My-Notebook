
# [**Instance**](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Instances.html)
## [**Lifecycle**](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-lifecycle.html)
![Instance lifecycle](https://img-blog.csdnimg.cn/0766c4c0e9134d0d92fd9ec34c42939b.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWXVueGlhbmdfSGU=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
Can't stop and start an instance store-backed instance.

## Instance Lifecycle
### Launch
Launch methods:

 - [Amazon EC2 console] Use the **launch instance wizard** to specify the launch parameters.
 - [Amazon EC2 console] Create a **launch template** and launch the instance from the launch template.
 - [Amazon EC2 console] Use an **existing instance** as the base.
 - [Amazon EC2 console] Use an **AMI**.
 - [AWS CLI] Use an **AMI** that you select.
 - [AWS Tools for Windows PowerShell] Use an AMI that you select.
 - [AWS CLI] Use **EC2 Fleet** to provision capacity across different EC2 instance types and Availability Zones, and across On-Demand Instance, Reserved Instance, and Spot Instance purchase models.
 - [AWS CloudFormation] Use a AWS **CloudFormation template** to specify an instance.
 - [AWS SDK] Use a language-specific **AWS SDK** to launch an instance.	

When you launch your instance, you can launch your instance in a subnet that is associated with one of the following resources:

 - An Availability Zone
 - A Local Zone
 - A Wavelength Zone
 - An Outpost

After you launch your instance, you can connect to it and use it.

### Connect
#### Connect to your Linux instance
Connection Options

SSH client
EC2 Instance Connect

[**AWS Systems Manager Session Manager**](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html)
 - Session Manager is a fully managed AWS Systems Manager capability that lets you manage your Amazon EC2 instances through an interactive one-click browser-based shell or through the AWS CLI.
 - You can use Session Manager to start a session with an instance in your account.
 - After the session is started, you can run bash commands as you would through any other connection type.

# Fleet
You can use an EC2 Fleet or a Spot Fleet to launch a fleet of instances.
In a single API call, a fleet can launch multiple instance types across multiple Availability Zones, using the On-Demand Instance, Reserved Instance, and Spot Instance purchasing options together.

## [EC2 Fleet](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-fleet.html)
An EC2 Fleet contains the configuration information to launch a fleet—or group—of instances.
 - Define separate On-Demand and Spot capacity targets and the maximum amount you’re willing to pay per hour.
 - Specify the instance types that work best for your applications.
 - Specify how Amazon EC2 should distribute your fleet capacity within each purchasing option.
 - 

## Spot Fleet
## Monitor Fleet Events
# Monitor
# Networking
# Security
# Storage



---

# [EC2 Instance Connect](https://docs.aws.amazon.com/ec2-instance-connect/latest/APIReference/Welcome.html)
Amazon EC2 Instance Connect enables system administrators to publish one-time use SSH public keys to EC2, providing users a simple and secure way to connect to their instances.

 - Pushes an SSH public key to the specified EC2 instance. The key remains for 60 seconds, which gives you 60 seconds to establish a serial console connection to the instance using SSH.

**Request Syntax**
```java
{
   "InstanceId": "string",
   "SerialPort": number,
   "SSHPublicKey": "string"
}
```
[Other Common Parameters](https://docs.aws.amazon.com/ec2-instance-connect/latest/APIReference/CommonParameters.html)
 - Action
 - Version
 - X-Amz-Algorithm
 - X-Amz-Credential
 - X-Amz-Date
 - X-Amz-Security-Token
 - X-Amz-Signature
 - X-Amz-SignedHeaders



Response Syntax
```java
{
   "RequestId": "string",
   "Success": boolean
}
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYwODQ2ODcwXX0=
-->