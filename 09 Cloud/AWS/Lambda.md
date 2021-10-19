# Introduction
## References
[AWS official document](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)
[API reference](https://docs.aws.amazon.com/lambda/latest/dg/API_Reference.html)

# [What is AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)
Lambda is a compute service that lets you run code without provisioning or managing servers.

Lambda runs your code on a high-availability compute infrastructure and performs all of the administration of the compute resources, including server and operating system maintenance, capacity provisioning and automatic scaling, code monitoring and logging.

## When should I use Lambda?

## Features

## Accessing Lambda


# Foundations
## Concepts
**Function**
A function is a resource that you can invoke to run your code in Lambda. A function has code to process the events that you pass into the function or that other AWS services send to the function.

**Trigger**
A trigger is a resource or configuration that invokes a Lambda function.
Triggers include AWS services that you can configure to invoke a function and event source mappings.
An event source mapping is a resource in Lambda that reads items from a stream or queue and invokes a function.

**Event**
 An event is a JSON-formatted document that contains data for a Lambda function to process.

**Execution environment**
An execution environment provides a secure and isolated runtime environment for your Lambda function.

**Instruction set architecture**
The instruction set architecture determines the type of computer processor that Lambda uses to run the function.

**Deployment package**
You deploy your Lambda function code using a deployment package.

**Runtime**
The runtime provides a language-specific environment that runs in an execution environment.
The runtime relays invocation events, context information, and responses between Lambda and the function.

**Layer**
A Lambda layer is a .zip file archive that can contain additional code or other content. A layer can contain libraries, a custom runtime, data, or configuration files.
Layers provide a convenient way to package libraries and other dependencies that you can use with your Lambda functions.


**Extension**
Lambda extensions enable you to augment your functions.

**Concurrency**
Concurrency is the number of requests that your function is serving at any given time.

**Qualifier**
When you invoke or view a function, you can include a qualifier to specify a version or alias.

**Destination**
A destination is an AWS resource where Lambda can send events from an asynchronous invocation

## Features
## Programming model
## Architectures
## Function scaling
## Deployment packages
## Lambda console
## Lambda CLI
# Permissions
# Configuring functions
# Managing functions
# Invoking functions
# Lambda runtimes
# Container images
# Working with Java
# Monitoring
# Security
# Troubleshooting
# Lambda applications
# Orchestrating functions
# Best practices
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MTEwMjEwMTAsLTE2NDk1NTI2NzJdfQ
==
-->