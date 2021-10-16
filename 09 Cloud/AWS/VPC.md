[AWS Official Docs](https://docs.aws.amazon.com/vpc/index.html)

# What is Amazon VPC
Amazon Virtual Private Cloud (Amazon VPC) enables you to launch AWS resources into a virtual network.

 - This virtual network closely resembles a traditional network that you'd operate in your own data center, with the benefits of using the scalable infrastructure of AWS.
 - It is logically isolated from other virtual networks in the AWS Cloud.
	 - You can launch your AWS resources into your VPC.
	 - You can specify an IP address range for the VPC, add subnets, associate security groups, and configure route tables.

## VPC Concepts

 - **Virtual Private Cloud (VPC)** — A virtual network dedicated to your AWS account.
 - **Subnet** — A range of IP addresses in your VPC.
 - **Route Table** — A set of rules, called routes, that are used to determine where network traffic is directed.
 - **Internet Gateway** — A gateway that you attach to your VPC to enable communication between resources in your VPC and the internet.
 - **Endpoint** — Enables you to privately connect your VPC to supported AWS services and VPC endpoint services powered by PrivateLink without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. 
	 - Instances in your VPC do not require public IP addresses to communicate with resources in the service.
	 - Traffic between your VPC and the other service does not leave the Amazon network.

## Access Amazon VPC

 - AWS Management Console
 - AWS Command Line Interface (AWS CLI)
 - AWS SDKs
 - Query API

---

# How Amazon VPC Works
## VPCs and Subnets
**Subnets**
A **subnet** is a range of IP addresses in your VPC. You can launch AWS resources into a specified subnet.   
 - Use a public subnet for resources that must be connected to the internet, and a private subnet for resources that won't be connected to the internet.
 - To protect the AWS resources in each subnet, you can use **multiple layers** of security, including **security groups** and **network access control lists (ACL)**.
 - You can optionally associate an **IPv6 CIDR block** with your VPC, and assign IPv6 addresses to the instances in your VPC.

## Default and Non-default VPCs
Default VPC
 - A default VPC has the benefits of the advanced features provided by EC2-VPC, and is ready for you to use.
 - If you have a default VPC and don't specify a subnet when you launch an instance, the instance is launched into your default VPC.
 - You can launch instances into your default VPC without needing to know anything about Amazon VPC.

Non-default VPC
 - Subnets that you create in your non-default VPC and additional subnets that you create in your default VPC

## Route Tables
A route table contains a set of rules, called routes, that are used to determine where network traffic from your VPC is directed.
 - You can explicitly associate a subnet with a particular route table. Otherwise, the subnet is implicitly associated with the main route table.
 - Each route in a route table specifies the range of IP addresses where you want the traffic to go (the destination) and the gateway, network interface, or connection through which to send the traffic (the target).

## Access the Internet

## Access a Corporate or Home Network

## Connect VPCs and Networks
**VPC peering**
 - You can create a VPC peering connection between two VPCs that enables you to route traffic between them privately.
 - Instances in either VPC can communicate with each other as if they are within the same network.

**Transit Gateway**
 - You can also create a transit gateway and use it to interconnect your VPCs and on-premises networks.
 - The transit gateway acts as a **Regional virtual router** for traffic flowing between its attachments, which can include VPCs, VPN connections, AWS Direct Connect gateways, and transit gateway peering connections.

## AWS Private Global Network Considerations
AWS Regions are connected to multiple Internet Service Providers (ISPs) as well as to a private global network backbone. The following considerations apply:
 - Traffic that is in an Availability Zone, or between Availability Zones in all Regions, routes over the AWS private global network.
 - Traffic that is between Regions always routes over the AWS private global network, except for China Regions.



<!--stackedit_data:
eyJoaXN0b3J5IjpbODg5MjE0NDI3XX0=
-->