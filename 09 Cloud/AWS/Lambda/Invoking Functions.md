# [Invoking AWS Lambda functions](https://docs.aws.amazon.com/lambda/latest/dg/lambda-invocation.html)

Types
 - You can invoke Lambda functions **directly** with the Lambda console, the Lambda API, the AWS SDK, the AWS CLI, and AWS toolkits.
 - You can also configure **other AWS services** to invoke your function
 - You can configure Lambda to read from a stream or queue and invoke your function.

Styles
 - Synchronous
 - Asynchronous


# [Synchronous Invocation](https://docs.aws.amazon.com/lambda/latest/dg/invocation-sync.html)
![Clients invoke a function synchronously and wait for a response.](https://docs.aws.amazon.com/lambda/latest/dg/images/invocation-sync.png)
 - The `payload` is a string that contains an event in JSON format.
 - 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4MzczMzU0MTksMTY3NzY2MjgzNF19
-->