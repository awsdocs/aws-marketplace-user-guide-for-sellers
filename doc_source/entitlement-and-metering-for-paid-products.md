# Entitlement and Metering for Paid Products<a name="entitlement-and-metering-for-paid-products"></a>

 Paid container software products sold through AWS Marketplace must integrate with the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) and call the `RegisterUsage` operation for software entitlement and metering\. Calling `RegisterUsage` from containers running outside of Amazon ECS is not currently supported\. Free and BYOL products for Amazon ECS aren't required to call `RegisterUsage`, but you may choose to do so if you want to receive usage data in your seller reports\. The following sections explain the behavior of `RegisterUsage`\. 

## Entitlement<a name="seller-container-entitlement"></a>

 `RegisterUsage` allows you to verify that the customer running your paid software is subscribed to your product on AWS Marketplace, enabling you to guard against unauthorized use\. Your container image that integrates with `RegisterUsage` is only required to guard against unauthorized use at container startup\. As such, a `CustomerNotSubscribedException/PlatformNotSupportedException` will only be thrown on the initial call to `RegisterUsage`\. Subsequent calls from the same Amazon ECS task instance \(for example, task\-id\) will not throw `CustomerNotSubscribedException`, even if the customer unsubscribes while the Amazon ECS task is still running\. 

## Metering<a name="seller-container-metering"></a>

 `RegisterUsage` only performs software metering, infrastructure metering is handled by the Amazon EC2 control plane when customers launch Amazon ECS tasks on Amazon ECS, and are charged for Amazon EC2 instance use regardless of if they are running Amazon ECS task\. Customers who choose to run tasks on Amazon Fargate are charged for infrastructure use based on the Amazon ECS task compute configuration and duration of the Amazon ECS task execution\. 

 `RegisterUsage` meters software use per Amazon ECS task, per hour, with usage prorated to the second\. A minimum of 1 minute of usage applies to tasks that are short lived\. For example, if a customer has a 10\-node Amazon ECS cluster and creates an Amazon ECS service configured as a daemon set, Amazon ECS will launch a task on all 10 cluster nodes, and the customer will be charged \(10 \* hourly\_rate\)\. Metering for software use is automatically handled by the AWS Marketplace Metering Control Plane\. Your software is not required to perform any metering specific actions except calling `RegisterUsage` once for metering of software use to commence\. The AWS Marketplace Metering Control Plane will also continue to bill customers for running Amazon ECS tasks, regardless of the customers subscription state, removing the need for your software to perform entitlement checks at runtime\. 

 To get up and running quickly, use the steps in [Integrating Paid Container Software](integrating-your-paid-container-software.md) to integrate your paid container software with the AWS Marketplace Metering Service\. You don't have to fully onboard your paid container product with AWS Marketplace to perform this integration test\. 

## Error Handling<a name="error-handling"></a>

 If your container image integrates with `RegisterUsage` and receives an exception other than `ThrottlingException` at container startup you should kill the container image to prevent unauthorized use\. Your container image that integrates with `RegisterUsage` is only required to guard against unauthorized use at container startup, as such exceptions other than `ThrottlingException` will only be thrown on the initial call to `RegisterUsage`\. Subsequent calls from the same Amazon ECS task instance \(for example, `task-id`\) will not throw `CustomerNotSubscribedException` even if the customer unsubscribes while the Amazon ECS task is still running\. 

 The following table describes the errors that `RegisterUsage` might throw\. Each AWS SDK programming language has a set of error handling guidelines that you can refer to for additional information\. 


|  **Error**  |  **Description**  | 
| --- | --- | 
|  InternalServiceErrorException  |  RegisterUsage isn't available\.  | 
|  CustomerNotEntitiledException  |  The customer doesn't have a valid subscription for the product\.  | 
|  InvalidProductCodeException  |  The ProductCode value passed in as part of the request doesn't exist\.  | 
|  InvalidPublicKeyException  |  The PublicKeyVersion value passed in as part of the request doesn't exist\.  | 
|  PlatformNotSupportedException  |  AWS Marketplace doesn't support metering usage from the underlying platform\. Currently, only Amazon ECS is supported\.  | 
|  ThrottlingException  |  The calls to RegisterUsage are throttled\.  | 
|  InvalidRegionException  |  RegisterUsage must be called in the same AWS Region that the Amazon ECS task was launched in\. This prevents a container from hardcoding a Region \(for example, withRegion\(“us\-east\-1”\)\) when calling RegisterUsage\.  | 