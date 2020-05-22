# Hourly metering<a name="container-metering-registerusage"></a>

If your container product uses per\-hour task/pod pricing instead of custom metered pricing dimensions, you don't have to define custom metering dimensions\.

`RegisterUsage` meters software use per Amazon ECS task or per Amazon EKS pod, per hour, with usage prorated to the second\. A minimum of 1 minute of usage applies to tasks or pods that are short lived\. Continuous metering for software use is automatically handled by the AWS Marketplace Metering Control Plane\. Your software is not required to perform any metering specific actions except calling `RegisterUsage` once for metering of software use to commence\.

The AWS Marketplace Metering Control Plane continues to bill customers for running Amazon ECS tasks and Amazon EKS pods, regardless of the customers subscription state, removing the need for your software to perform entitlement checks after the initial successful launch of the task or pod\. 

## Hourly metering prerequisites<a name="hourly-metering-prereqs"></a>

Before publishing the product, you must do the following:

1. Create a new container product in the AWS Marketplace Management Portal, and make a note of its product code\.

1. Fill out the product load form with the necessary hourly price information and return it to us for processing\.

1. Use an IAM role for the task or pod running your application with the IAM permissions necessary to call `RegisterUsage`\. The IAM managed policy `AWSMarketplaceMeteringRegisterUsage` has these permissions\. 

1. \(Optional\) We recommend that you enable CloudTrail logging in the task or pod definition if you want to see logging\.

1. Make a test call to the `RegisterUsage` action with a record for all of the pricing dimensions you define\.

## Product load form for hourly metering<a name="hourly-metering-product-load-form"></a>

When filling out the product load form for hourly metering, fill out the following fields for your product, in addition to the other required and optional fields that define your product\.
+ `Hourly Price` This is the price for your product, per hour\.
+ `Dimension Long Term Rate` – The software price per unit for this product when buyers pay upfront for a long term contract\.
+ `Long Term Duration (Days)` – The duration, in days, for the long term contract\.

## Testing integration and preview mode for RegisterUsage<a name="hourly-metering-preview-mode"></a>

Use the `RegisterUsage` action to test your integration before submitting your image to AWS Marketplace for publishing\.

Preview mode operates identically to production mode, except preview mode does not verify entitlement to use your product\. To call `RegisterUsage` in preview mode, call `RegisterUsage` from the container image\(s\) by running your product on Amazon ECS or Amazon EKS with the AWS account you are using to list the product on AWS Marketplace\. When testing, launch at least one Amazon ECS task or Amazon EKS pod containing your paid container in the `us-east-1` AWS Region\.

**Note**  
If your product supports both Amazon ECS and Amazon EKS, you only need to launch in Amazon EKS for us to validate your integration\.

You can't fully test the integration until your product is published with all the required metadata and pricing information\. If requested, the AWS Marketplace catalog operations team can verify receipt of your metering records in preview mode\.

## Error handling for RegisterUsage<a name="hourly-metering-entitlement-error-handling"></a>

If your container image integrates with the AWS Marketplace Metering service and receives an exception other than `ThrottlingException` at container startup, you should terminate the container to prevent unauthorized use\.

Exceptions other than `ThrottlingException` are thrown only on the initial call to `RegisterUsage`\. Subsequent calls from the same Amazon ECS task or Amazon EKS pod do not throw `CustomerNotSubscribedException` even if the customer unsubscribes while the task or pod is still running\. These customers are still charged for running containers after they unsubscribe and their usage is tracked\.

The following table describes the errors that `RegisterUsage` might throw\. Each AWS SDK programming language has a set of error handling guidelines that you can refer to for additional information\. 


|  **Error**  |  **Description**  | 
| --- | --- | 
|  InternalServiceErrorException  |  RegisterUsage isn't available\.  | 
|  CustomerNotEntitiledException  |  The customer doesn't have a valid subscription for the product\.  | 
|  InvalidProductCodeException  |  The ProductCode value passed in as part of the request doesn't exist\.  | 
|  InvalidPublicKeyException  |  The PublicKeyVersion value passed in as part of the request doesn't exist\.  | 
|  PlatformNotSupportedException  |  AWS Marketplace doesn't support metering usage from the underlying platform\. Only Amazon ECS, Amazon EKS, and Fargate are supported\.  | 
|  ThrottlingException  |  The calls to RegisterUsage are throttled\.  | 
|  InvalidRegionException  |  RegisterUsage must be called in the same AWS Region that the Amazon ECS task or Amazon EKS pod was launched in\. This prevents a container from choosing a Region \(for example, withRegion\(“us\-east\-1”\)\) when calling RegisterUsage\.  | 