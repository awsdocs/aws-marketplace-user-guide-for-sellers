# Hourly metering with AWS Marketplace Metering Service<a name="container-metering-registerusage"></a>

If your container product uses per\-hour per\-task or per\-pod pricing instead of custom metered pricing dimensions, you don't have to define custom metering dimensions\.

The `RegisterUsage` API operation meters software use per Amazon Elastic Container Service \(Amazon ECS\) task or per Amazon Elastic Kubernetes Service \(Amazon EKS\) pod, per hour, with usage prorated to the second\. A minimum of 1 minute of usage applies to tasks or pods that are short lived\. Continuous metering for software use is automatically handled by the AWS Marketplace Metering Control Plane\. Your software isn't required to perform any metering specific actions except calling `RegisterUsage` once for metering of software use to commence\.

`RegisterUsage` must be called immediately at the time of launching a container\. If you don't register the container in the first 6 hours of the container launch, AWS Marketplace Metering Service doesn't provide any metering guarantees for previous months\. However, the metering will continue for the current month forward until the container ends\.

The AWS Marketplace Metering Control Plane continues to bill customers for running Amazon ECS tasks and Amazon EKS pods, regardless of the customer's subscription state\. This removes the need for your software to perform entitlement checks after the initial successful launch of the task or pod\. 

## Hourly metering prerequisites<a name="hourly-metering-prereqs"></a>

Before publishing the product, you must do the following:

1. Create a new container product in the AWS Marketplace Management Portal, and make a note of its product code\.

   For more information, see [Creating a container product](container-product-getting-started.md#create-container-product)\.

1. Fill out the product load form \(PLF\) with the necessary hourly price information, and return it to us for processing\.

   For more information, see [Creating or updating pricing details for container products](container-product-getting-started.md#container-product-load-form)\.

1. Use an AWS Identity and Access Management \(IAM\) role for the task or pod running your application with the IAM permissions necessary to call `RegisterUsage`\. The IAM managed policy `AWSMarketplaceMeteringRegisterUsage` has these permissions\. 

1. \(Optional\) If you want to see logging, we recommend that you enable AWS CloudTrail logging in the task or pod definition\.

1. Make a test call to the `RegisterUsage` API operation with a record for all of the pricing dimensions you define\.

## Product load form for hourly metering<a name="hourly-metering-product-load-form"></a>

When filling out the product load form for hourly metering, fill out the following fields for your product, in addition to the other required and optional fields that define your product:
+ **Hourly Price** – The price for your product, per hour\.
+ **Dimension Long Term Rate** – The total software price over a long\-term contract when buyers pay upfront\.
+ **Long Term Duration \(Days\)** – The duration, in days, for the long\-term contract\.

## Testing integration and preview mode for `RegisterUsage`<a name="hourly-metering-preview-mode"></a>

Use the `RegisterUsage` API operation to test your integration before submitting your image to AWS Marketplace for publishing\.

Preview mode operates identically to production mode, except preview mode does not verify entitlement to use your product\. To call `RegisterUsage` in preview mode, call `RegisterUsage` from the container image by running your product on Amazon ECS or Amazon EKS\. Use the AWS account that you're using to list the product on AWS Marketplace\. Your metering integration must dynamically set the AWS Region, rather than hardcoding it\. However, when testing, launch at least one Amazon ECS task or Amazon EKS pod containing your paid container in the US East \(N\. Virginia\) Region\. By doing this, the AWS Marketplace operations team can verify your work with the logs in that Region\.

**Note**  
If your product supports both Amazon ECS and Amazon EKS, you only need to launch in Amazon EKS for us to validate your integration\.

You can't fully test the integration until your product is published with all the required metadata and pricing information\. If requested, the AWS Marketplace catalog operations team can verify receipt of your metering records in preview mode\.

## Error handling for `RegisterUsage`<a name="hourly-metering-entitlement-error-handling"></a>

If your container image integrates with the AWS Marketplace Metering Service and receives an exception other than `ThrottlingException` at container startup, you should terminate the container to prevent unauthorized use\.

Exceptions other than `ThrottlingException` are thrown only on the initial call to the `RegisterUsage` API operation\. Subsequent calls from the same Amazon ECS task or Amazon EKS pod don't throw `CustomerNotSubscribedException` even if the customer unsubscribes while the task or pod is still running\. These customers are still charged for running containers after they unsubscribe, and their usage is tracked\.

The following table describes the errors that the `RegisterUsage` API operation might throw\. Each AWS SDK programming language has a set of error handling guidelines that you can refer to for additional information\. 


|  **Error**  |  **Description**  | 
| --- | --- | 
|  InternalServiceErrorException  |  RegisterUsage isn't available\.  | 
|  CustomerNotEntitiledException  |  The customer doesn't have a valid subscription for the product\.  | 
|  InvalidProductCodeException  |  The ProductCode value passed in as part of the request doesn't exist\.  | 
|  InvalidPublicKeyException  |  The PublicKeyVersion value passed in as part of the request doesn't exist\.  | 
|  PlatformNotSupportedException  |  AWS Marketplace doesn't support metering usage from the underlying platform\. Only Amazon ECS, Amazon EKS, and AWS Fargate are supported\.  | 
|  ThrottlingException  |  The calls to RegisterUsage are throttled\.  | 
|  InvalidRegionException  |  RegisterUsage must be called in the same AWS Region that the Amazon ECS task or Amazon EKS pod was launched in\. This prevents a container from choosing a Region \(for example, withRegion\(“us\-east\-1”\)\) when calling RegisterUsage\.  | 