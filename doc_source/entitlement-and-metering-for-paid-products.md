# Entitlement and Metering for Paid Products<a name="entitlement-and-metering-for-paid-products"></a>

 Paid container software products sold through AWS Marketplace must integrate with the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) and call the `RegisterUsage` operation for software entitlement and metering\. Free and BYOL products aren't required to call `RegisterUsage`, but you might choose to do so if you want to receive usage data in your seller reports\. The following sections explain the behavior of `RegisterUsage`\.

**Note**  
You can call `RegisterUsage` from Amazon EKS [using a supported AWS SDK](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts-minimum-sdk.html)\.

## Entitlement<a name="seller-container-entitlement"></a>

 `RegisterUsage` allows you to verify that the customer running your paid software is subscribed to your product on AWS Marketplace, enabling you to guard against unauthorized use\. Your container image that integrates with `RegisterUsage` is only required to guard against unauthorized use at container startup\. As such, a `CustomerNotSubscribedException/PlatformNotSupportedException` is thrown only on the initial call to `RegisterUsage`\. Subsequent calls from the same Amazon ECS task instance or Amazon EKS pod \(for example, `task-id`\) does not throw `CustomerNotSubscribedException`, even if the customer unsubscribes while the Amazon ECS task or Amazon EKS pod is still running\. 

## Metering<a name="seller-container-metering"></a>

Infrastructure metering is handled by the Amazon ECS or Amazon EKS control plane based on the customer\-defined cluster configurations\. AWS Fargate automatically meters infrastructure usage based on the customer\-defined compute resources defined\. For more information about pricing, see [Amazon Elastic Container Service Pricing](https://aws.amazon.com/ecs/pricing) or [Amazon EKS Pricing](https://aws.amazon.com/eks/pricing)\.

 Software metering requires you to integrate your container software with `RegisterUsage`\. After you integrate your container with `RegisterUsage` customers are charged for each Amazon ECS task or Kubernetes pod that contains the container that has integrated with `RegisterUsage`\. `RegisterUsage` meters software use per Amazon ECS task or per Amazon EKS pod, per hour, with usage prorated to the second\. A minimum of 1 minute of usage applies to tasks or pods that are short lived\. For example, if a customer has a 10\-node Amazon ECS cluster or Amazon EKS cluster and creates a service configured as a daemon set, Amazon ECS or Amazon EKS launches a task or pod on all 10 cluster nodes, and the customer is charged \(10 \* hourly\_rate\)\. Continuous metering for software use is automatically handled by the AWS Marketplace Metering Control Plane\. Your software is not required to perform any metering specific actions except calling `RegisterUsage` once for metering of software use to commence\. The AWS Marketplace Metering Control Plane continues to bill customers for running Amazon ECS tasks and Amazon EKS pods, regardless of the customers subscription state, removing the need for your software to perform entitlement checks after the initial successful launch of the task or pod\. 

 `RegisterUsage` meters software use per Amazon ECS task or Amazon EKS pod, per hour, with usage prorated to the second\. A minimum of 1 minute of usage applies to tasks that are short lived\. For example, if a customer has a 10\-node Amazon ECS or Amazon EKS cluster and creates a service configured as a daemon set, Amazon ECS or Amazon EKS launches a task or pod on all 10 cluster nodes, and the customer is charged \(10 \* hourly\_rate\)\. Metering for software use is automatically handled by the AWS Marketplace Metering Control Plane\. Your software is not required to perform any metering specific actions except calling `RegisterUsage` once for metering of software use to commence\. The AWS Marketplace Metering Control Plane also continues to bill customers for running Amazon ECS tasks and Amazon EKS pods, regardless of the customers subscription state, removing the need for your software to perform entitlement checks at runtime\. 

 To get up and running quickly, use the steps in [Integrating Paid Container Software](integrating-your-paid-container-software.md) to integrate your paid container software with the AWS Marketplace Metering Service\. You don't have to fully onboard your paid container product with AWS Marketplace to perform this integration test\. 

## Error Handling<a name="error-handling"></a>

 If your container image integrates with `RegisterUsage` and receives an exception other than `ThrottlingException` at container startup you should kill the container image to prevent unauthorized use\. Your container image that integrates with `RegisterUsage` is only required to guard against unauthorized use at container startup, as such exceptions other than `ThrottlingException` are thrown only on the initial call to `RegisterUsage`\. Subsequent calls from the same Amazon ECS task instance or Amazon EKS pod call \(for example, `task-id`\) do not throw `CustomerNotSubscribedException` even if the customer unsubscribes while the task or pod is still running\. 

 The following table describes the errors that `RegisterUsage` might throw\. Each AWS SDK programming language has a set of error handling guidelines that you can refer to for additional information\. 


|  **Error**  |  **Description**  | 
| --- | --- | 
|  InternalServiceErrorException  |  RegisterUsage isn't available\.  | 
|  CustomerNotEntitiledException  |  The customer doesn't have a valid subscription for the product\.  | 
|  InvalidProductCodeException  |  The ProductCode value passed in as part of the request doesn't exist\.  | 
|  InvalidPublicKeyException  |  The PublicKeyVersion value passed in as part of the request doesn't exist\.  | 
|  PlatformNotSupportedException  |  AWS Marketplace doesn't support metering usage from the underlying platform\. Only Amazon ECS and Amazon EKS are supported\.  | 
|  ThrottlingException  |  The calls to RegisterUsage are throttled\.  | 
|  InvalidRegionException  |  RegisterUsage must be called in the same AWS Region that the Amazon ECS task or Amazon EKS pod was launched in\. This prevents a container from choosing a Region \(for example, withRegion\(“us\-east\-1”\)\) when calling RegisterUsage\.  | 