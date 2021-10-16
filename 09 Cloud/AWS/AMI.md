# Introduction
Reference: [AWS Official Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)

An Amazon Machine Image (AMI) provides the information required to launch an instance.

An AMI includes the following:
* One or more Amazon Elastic Block Store (Amazon EBS) **snapshots**, or, for instance-store-backed AMIs, **a template for the root volume** of the instance (for example, an operating system, an application server, and applications).
* **Launch permissions** that control which AWS accounts can use the AMI to launch instances.
* A block device **mapping** that specifies the volumes to attach to the instance when it's launched.

# AMI Types
**AMI characteristics**
 - Region
 - OS
 - Architecture (32-bit or 64-bit)
 - Launch permission
	 - public
	 - explicit
	 - implicit
 - Storage for the root device
     - ![EBS vs. Instance
   store](https://img-blog.csdnimg.cn/2f8c9e9d7f454dc8b6f57ff731fc7092.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWXVueGlhbmdfSGU=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

# AMI Lifecycle
![AMI Lifecycle](https://img-blog.csdnimg.cn/7e52669650fd424ab51c6ec4e56cdea7.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWXVueGlhbmdfSGU=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
You can search for an AMI that meets the criteria for your instance.

## Create your own AMI
You can launch an instance from an existing AMI, customize the instance (for example, install software on the instance), and then save this updated configuration as a custom AMI

The root storage device of the instance determines the process you follow to create an AMI. 
 - Create an Amazon EBS-backed AMI
	 -  Root device for an instance launched from the AMI is an Amazon Elastic Block Store (Amazon EBS) volume created from an Amazon EBS snapshot.
 - Create an instance store-backed AMI
	 -  Root device for an instance launched from the AMI is an instance store volume created from a template stored in Amazon S3.

## Deregister your AMI
You can deregister an AMI when you have finished with it.




<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwOTAyNjMwMF19
-->