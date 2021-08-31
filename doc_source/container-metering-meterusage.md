# Custom metering<a name="container-metering-meterusage"></a>

AWS Marketplace container products can have custom metering on up to 24 different pricing dimensions per product\. Each dimension can have a long\-term contract price associated with it\. Custom metering is enabled by integrating your container product with the AWS Marketplace Metering Service\. If you want to define your own pricing units and custom metering for that usage to us for billing, integrate with [https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_MeterUsage.html](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_MeterUsage.html)\.

Price dimensions are defined in two locations, once in the product load form and once through the `MeterUsage` operation\. This two\-factor method ensures that the subsequent offers are working as intended before they're made available to the public\.

To set up custom metering, you'll need to choose the usage category, the unit type, and pricing dimensions: 
+ **Usage category** – The usage category helps buyers understand what your product is and how to use it\. 
+ **Unit type** – The unit type defines the unit of measure for billing\. For example, bandwidth measured in GBps or MBps, the number of hosts, or data measured in MB, GB, or TB\.
+ **Pricing dimensions** – The pricing dimensions represents a feature or service that you've set a per\-unit price for \(for example, users, scans, vCPUs, or deployed agents\)\. Pricing dimensions are public; however, you can still define private and Bring Your Own License \(BYOL\) offers for public products\. Don't send pricing in the metering records\. You meter the quantity of units, and we use that along with the prices you defined when creating your product to compute the buyer's bill\. 

  If your product pricing doesn't fit with any of the predefined categories or unit types, you can choose the generic **units** category and use the dimension description to describe what the unit is\.

Optionally, you may distribute the usage into allocations by properties that you track\. The allocations are represented as tags to the buyer\. These tags allow the buyer to view their costs split into usage by tag values\. For example, if you charge by the user, and users have a "Department" property, you could create usage allocations with tags that have a key of "Department", and one allocation per value\. This does not change the price, dimensions, or the total usage that you report, but allows your customer to view their costs by categories appropriate to your product\.

We recommend that you send a metering record every hour; however, you can aggregate usage over daily or monthly periods as well\. If you experience an outage you can aggregate buyer software use and send it in the following hours metering\. You can't send more than one record per hour\.

**Important**  
Free trial and prepaid entitlement are tracked on an hourly level\. As a result, sending these records in separately might lead to the buyer being overcharged\.

## Custom metering prerequisites<a name="custom-metering-prereqs"></a>

Before publishing the product, you must do the following:

1. Create a new container product in the AWS Marketplace Management Portal, and make a note of its product code\.

1. Fill out the product load form with the necessary dimension information, and return it to us for processing\.

1. Use an AWS Identity and Access Management \(IAM\) role for the task or pod running your application with the IAM permissions necessary to call `MeterUsage`\. The IAM managed policy `AWSMarketplaceMeteringRegisterUsage` has these permissions\.

1. \(Optional\) We recommend that you enable CloudTrail logging in the task or pod definition if you want to see logging\.

1. Make a test call to the `MeterUsage` operation with a record for all of the pricing dimensions you define\.

## Product load form for custom metering<a name="custom-metering-product-load-form"></a>

When filling out the product load form for custom metering, each product can have up to 24 dimensions\. The dimensions are defined in the following fields:
+ **Dimension Name** – The name used when your container application is sending metering records to the AWS Marketplace Metering Service\. This name indicates which dimension your buyer will use\. This name is visible in billing reports\. After you set the name, you can't change it\.
+ **Dimension Description** – The buyer\-facing description for the dimension\. The description can't exceed 70 characters\. After the product is published publicly to buyers, this field can't be changed\.
+ **Dimension Rate** –The software price per unit for this product when buyers pay as they go\. This ﬁeld supports three decimal places\.
+ **Dimension Long Term Rate** – The total software price over a long\-term contract when buyers pay upfront\.
+ **Long Term Duration \(Days\)** – The duration, in days, for the long\-term contract\.

## Testing MeterUsage integration and preview mode<a name="custom-metering-preview-mode"></a>

Use the `MeterUsage` operation to test your integration before submitting your image to AWS Marketplace for publishing\.

Preview mode operates identically to production mode, except preview mode does not verify entitlement to use your product\. To call `MeterUsage` in preview mode, call `MeterUsage` from the container image\(s\) by running your product on Amazon Elastic Container Service \(Amazon ECS\) or Amazon Elastic Kubernetes Service \(Amazon EKS\) with the AWS account you are using to list the product on AWS Marketplace\. Your metering integration must dynamically set the AWS Region, rather than hard coding it, but when testing, launch at least one Amazon ECS task or Amazon EKS pod containing your paid container in the US East \(N\. Virginia\) AWS Region so that the AWS Marketplace operations team can verify your work with the logs in that Region\.

**Note**  
If your product supports both Amazon ECS and Amazon EKS, you only need to launch in Amazon EKS for us to validate your integration\.

You can't fully test the integration until your product is published with all the required metadata and pricing information\. If requested, the AWS Marketplace catalog operations team can verify receipt of your metering records in preview mode\.

## Error handling for MeterUsage<a name="custom-metering-entitlement-error-handling"></a>

If your container image integrates with the `MeterUsage` operation and receives an exception other than `ThrottlingException` at container startup, you should terminate the container to prevent unauthorized use\.

Exceptions other than `ThrottlingException` are thrown only on the initial call to `MeterUsage`\. Subsequent calls from the same Amazon ECS task or Amazon EKS pod do not throw `CustomerNotSubscribedException` even if the customer unsubscribes while the task or pod is still running\. These customers are still charged for running containers after they unsubscribe and their usage is tracked\.

The following table describes the errors that `MeterUsage` might throw\. Each AWS SDK programming language has a set of error handling guidelines that you can refer to for additional information\. 


|  **Error**  |  **Description**  | 
| --- | --- | 
| DuplicateRequestException |  A metering record has already been emitted for the given \{usageDimension, timestamp\} with a different usageQuantity\.  | 
| InvalidUsageDimensionException |  The usage dimension does not match one of the UsageDimensions associated with the product\.  | 
| TimestampOutOfBoundsException  |  The timestamp value passed in the MeterUsage is out of allowed range\.  | 
|  InternalServiceErrorException  |  MeterUsage isn't available\. | 
|  CustomerNotEntitledException  |  The customer doesn't have a valid subscription for the product\.  | 
|  InvalidProductCodeException  |  The ProductCode value passed in as part of the request doesn't exist\.  | 
|  PlatformNotSupportedException  |  AWS Marketplace doesn't support metering usage from the underlying platform\. Only Amazon ECS, Amazon EKS, and AWS Fargate are supported\.  | 
|  ThrottlingException  |  The calls to MeterUsage are throttled\. | 
|  InvalidEndpointRegionException  |  MeterUsage must be called in the same AWS Region that the Amazon ECS task or Amazon EKS pod was launched in\. This prevents a container from choosing a Region \(for example, withRegion\(“us\-east\-1”\)\) when calling MeterUsage\.  | 
|  InvalidTagException  | The tags in the UsageAllocations object must have unique keys within each UsageAllocation, have no key\-value pairs the same across UsageAllocation objects, and the number of tags must be 5 or less per UsageAllocation\.  | 
|  InvalidUsageAllocationsException  | The UsageAllocation object allocations do not add up to the UsageQuantity value\. | 