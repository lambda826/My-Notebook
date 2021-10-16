[AWS Official Docs](https://docs.aws.amazon.com/cdk/index.html)

# What is the AWS CDK?
A software development framework for **defining cloud infrastructure in code** and provisioning it through AWS CloudFormation.

---

![AWS CDK Application](https://img-blog.csdnimg.cn/175c0f32bc4d47bc9abfd0513c19dc01.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWXVueGlhbmdfSGU=,size_20,color_FFFFFF,t_70,g_se,x_16)

# Concepts
## Construct
A construct represents a "cloud component" and encapsulates everything AWS CloudFormation needs to create the component.


AWS Construct library
	• This library includes constructs that represent all the resources available on AWS.
	• Three different levels of constructs:
		○ L1 or CFN (CloudFormation) resources.
			§ CFN Resources are periodically generated from the AWS CloudFormation Resource Specification. They are named CfnXyz, where Xyz is name of the resource.
		○ L2, also represent AWS resources, but with a higher-level, intent-based API.
		○ Patterns
			§ These constructs are designed to help you complete common tasks in AWS, often involving multiple kinds of resources.

Composition
	• Composition is the key pattern for defining higher-level abstractions through constructs.
		○ A high-level construct can be composed from any number of lower-level constructs, and in turn, those could be composed from even lower-level constructs, which eventually are composed from AWS resources.
	• Composition lets you define reusable components and share them like any other code.

Initialization
	• Constructs are implemented in classes that extend the Construct base class.
		○ You define a construct by instantiating the class.
		○ All constructs take three parameters when they are initialized:
			§ Scope
			§ id
			§ Props

Apps and stacks
	• We call your CDK application an app, which is represented by the AWS CDK class App.
	• Since resources eventually need to be deployed as part of a AWS CloudFormation stack into an AWS environment, which covers a specific AWS account and AWS region.
		○ AWS constructs must be defined within the scope of a Stack.
	• Once you have defined a stack, you can populate it with resources by instantiating constructs

Using L1 constructs
Using L2 constructs
Configuration
	• Most constructs accept props as their third argument (or in Python, keyword arguments), a name/value collection that defines the construct's configuration. 

Interacting with constructs
	• Constructs are classes that extend the base Construct class

Writing your own constructs
	• To declare a new construct, create a class that extends the Construct base class, then follow the pattern for initializer arguments.

The construct tree



Apps
To define a stack within the scope of an application, use the App construct.
You can also define constructs within an App-derived class.


![在这里插入图片描述](https://img-blog.csdnimg.cn/49e84352f536453ba71f450ce917397f.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWXVueGlhbmdfSGU=,size_20,color_FFFFFF,t_70,g_se,x_16)
Cloud assemblies
	• The call to app.synth() is what tells the AWS CDK to synthesize a cloud assembly from an app.

Stack
The unit of deployment in the AWS CDK is called a stack.


Best Practices
Tips
	• CDK applications should be organized into logical units.
	• The logical units should be implemented as constructs.
	• Stacks define the deployment model of these logical units


Organization best practices
![在这里插入图片描述](https://img-blog.csdnimg.cn/d7d2dad7c8b4493fb6c7e636c21c79c3.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWXVueGlhbmdfSGU=,size_20,color_FFFFFF,t_70,g_se,x_16)


Coding best practices
![在这里插入图片描述](https://img-blog.csdnimg.cn/59409724af37467f910f124e12747d45.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWXVueGlhbmdfSGU=,size_20,color_FFFFFF,t_70,g_se,x_16)
	• Start simple and add complexity only when you need it.
	• Align with the AWS Well-Architected framework.
	• Every application starts with a single package in a single repository.
	• Move code into repositories based on code lifecycle or team ownership
Infrastructure and runtime code live in the same package


Construct best practices

Application best practices
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwMTcwNzM3MDBdfQ==
-->