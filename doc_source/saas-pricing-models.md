# SaaS product pricing<a name="saas-pricing-models"></a>

After a buyer purchases your software as a service \(SaaS\) product on AWS Marketplace, AWS Marketplace provides you with their billing identiﬁer\. You use the billing identifier to call the AWS Marketplace Entitlement Service and the AWS Marketplace Metering Service\. Then, customers access the product in your AWS environment or through a VPC endpoint connection you create\. AWS Marketplace offers the following pricing models for SaaS products:
+ **SaaS subscriptions** – A pay\-as\-you\-go model where we bill buyers for their hourly usage of your SaaS product\.

  For more information, see [Pricing for SaaS subscriptions](saas-subscriptions.md)\.
+ **SaaS contracts** – Buyers are either billed in advance for the use of your software, or you can offer them a flexible payment schedule\. Customers can also pay for additional usage above their contract\.

  For more information, see [Pricing for SaaS contracts](saas-contracts.md)\.
+ **SaaS contracts with pay\-as\-you\-go** – Buyers are either billed in advance for the use of your software, or you can offer them a flexible payment schedule\. Buyers will also be billed an additional metered rate for usage on top of the contract price\.

  For more information, see [Pricing for SaaS contracts](saas-contracts.md)\.

To make your SaaS product available on AWS Marketplace, decide whether you want to offer the [SaaS subscriptions pricing model](saas-subscriptions.md) or the [SaaS contracts pricing model](saas-contracts.md)\.

## Pricing your software with SaaS<a name="pricing-your-software-with-saas"></a>

 To set prices, you first define pricing dimensions that represent the units of value in your software and then assign a price to each dimension\. For example, dimensions can be protected hosts, users, or storage volumes\. You can define up to 24 dimensions\. Next, you select a category for those dimensions from one of our preset categories \(bandwidth, data, hosts, requests, tiers, and users\)\. If none of the presets fit your use case, you can choose the generic 'units' category and describe the units in the dimension description\. 

### Example: Provisioned bandwidth with nonlinear pricing<a name="example-provisioned-bandwidth-with-non-linear-pricing"></a>

 Imagine you offer network appliance software\. You choose to bill by provisioned bandwidth\. For your usage category, select **bandwidth**\. In addition to charging by bandwidth, you want to charge a different price as buyers scale up\. You can define multiple dimensions within the bandwidth category\. You can define a distinct price for 25 Mbps, 100 Mbps, and 1 Gbps\. 

### Example: Concurrent hosts with multiple dimensions<a name="example-concurrent-hosts-with-multiple-dimensions"></a>

 Imagine you offer software that monitors other Amazon Elastic Compute Cloud \(Amazon EC2\) instances\. You choose to bill by the number of hosts that are being monitored\. For your usage category, select **host**\. In addition to charging by host, you want to charge for the extra value for monitoring larger hosts\. You can use multiple dimensions within the host category\. You can define a distinct price for micro, small, medium, large, x\-large, 2XL, 4XL, and 8XL instances\. Your software is responsible for mapping each particular host to one of your defined dimensions\. Your software is responsible for sending a separate metering record for each dimension of your usage category if applicable\. 

### Listing your SaaS product on AWS Marketplace<a name="listing-your-saas-product-on-aws-marketplace"></a>

 To take advantage of the Metering Service, you must create a new product\. If your product is already on AWS Marketplace, you will need to decide whether the new AWS Marketplace Metering Service product will be made available in addition to your current one, or if it will replace it as the only version available to new users\. If you choose replacement, the existing product will be removed from the AWS Marketplace so that it is no longer available for new buyers\. Existing customers will continue to have access to their old product and instances, but they can migrate to the new product at their convenience\. The new product must meter usage to the AWS Marketplace Metering Service\. 

 After you have your AMI, follow the standard process to share and scan your AMI using the self\-service tool\. In addition, using the template available on the management portal, fill out the product load form and upload it to start the ingestion process\. 

 The following definitions will help you fill out the fields of the product load form for the AWS Marketplace Metering Service\. On the product load form, these fields are labeled as **Flexible Consumption Pricing \(FCP\)** to differentiate them from hourly and monthly priced products\. 
+ **Title** – If you already have a product, and you are adding the same product with the AWS Marketplace Metering Service, include the FCP category and dimension in parentheses to differentiate them\. For example, “PRODUCT TITLE \(Data\)”\. 
+ **Pricing Model** – From the dropdown list, choose **Usage**\.
+ **FCP Category** – The category in which customers will be charged for paid products with a **Usage** pricing component\. From the dropdown menu, choose **Users**, **Hosts**, **Data**, or **Bandwidth**\.
+ **FCP Unit** – The unit of measurement on which customers will be charged for paid products with a **Usage** pricing component\. Options will appear in the dropdown menu based on the FCP category that you chose\. 

  The following table lists the valid units for each category\.    
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-pricing-models.html)
+ **FCP Dimension Name** – The name used when sending metering records by calling the `MeterUsage` API operation\. It is visible in billing reports, but because it isn't external\-facing, the name doesn't need to be user\-friendly\. The name can be no more than 15 characters and can only include alphanumeric and underscore characters\. After you set the name, you can't change it\. Changing the name requires a new AMI\.
+ **FCP Dimension Description** – The customer\-facing statement that describes the dimension for the product\. The description can be no more than 70 characters and should be user\-friendly\. Examples of a description include Administrators per hour and Per Mbps bandwidth provisioned\. After the product is published, you can't change this description\.
+ **FCP Rate** – The software charge per unit for this product\. This field supports three decimal places\. 

**Note**  
 You don't need to fill out hourly and annual pricing fields\. 
 Free trial and annual pricing aren't compatible\. 
 Products that use the clusters and AWS Resources feature can't use the AWS Marketplace Metering Service\. 
 Price, instance type, or AWS Region change will follow the regular process as other AWS Marketplace products\. 
 Products with the AWS Marketplace Metering Service can't be converted to other pricing models such as hourly, monthly, or BYOL\. 
 We recommend adding AWS Identity and Access Management \(IAM\) policy information in your usage instructions or document\. 

 If you have questions, contact the [AWS Marketplace Managed Catalog Operations \(MCO\)](https://aws.amazon.com/marketplace/management/contact-us/)

### Modifying your SaaS software to use the Metering Service<a name="modifying-your-saas-software-to-use-the-metering-service"></a>

 You will need to modify your software to record customer usage, send hourly usage reports to the Metering Service, and handle new failure modes\. The software operates independently of pricing, but the software will need to know about the usage category, how it's consumed, and any dimensions\. 

#### Measuring consumption<a name="pricing-measuring-consumption"></a>

 Your software must determine how much of the selected usage category and which dimensions the customer has consumed\. This value will be sent, once each hour, to the AWS Marketplace Metering Service\. In all cases, it's assumed that your software has the ability to measure, record, and read consumption of resources for the purpose of sending it on an hourly basis to the Metering Service\. 

 For provisioned consumption, this will typically be read from the software configuration as a sampled value However, it might also be a maximum configured value, recorded each hour\. For concurrent consumption, this might be either a periodic sample or a maximum value recorded each hour\. For accumulated consumption, this will be a value that is accumulated each hour\. 

 For pricing on multiple dimensions, multiple values must be measured and sent to the Metering Service, one per dimension\. This requires your software to be programmed or configured with the known set of dimensions when providing the product AMI\. The set of dimensions can't change after a product has been created\. 

 For each pricing scenario, this table describes recommended ways for measuring consumption each hour\. 


|  Scenario  |  How to measure  | 
| --- | --- | 
|  Provisioned User  |   Current number of provisioned users \(sampled\)\.   \-OR\-   Maximum number of provisioned users \(seen that hour\)\.   | 
|  Concurrent User  |   Current number of concurrent users \(sampled\)\.   \-OR\-   Maximum number of concurrent users \(seen that hour\)\.   \-OR\-   Total number of distinct users \(seen that hour\)\.   | 
|  Provisioned Host  |   Current number of provisioned hosts \(sampled\)\.   \-OR\-   Maximum number of provisioned hosts \(seen that hour\)\.   | 
|  Concurrent Host  |   Current number of concurrent hosts \(sampled\)\.   \-OR\-   Maximum number of concurrent hosts \(seen that hour\)\.   \-OR\-   Total number of distinct hosts \(seen that hour\)\.   | 
|  Provisioned Bandwidth  |   Current provisioned bandwidth setting \(sampled\)\.   \-OR\-   Maximum provisioned bandwidth \(seen that hour\)\.   | 
|  Accumulated Data  |   Current GB of data stored \(sampled\)\.   \-OR\-   Maximum GB of data stored \(seen that hour\)\.   \-OR\-   Total GB of data added or processed that hour\.   \-OR\-   Total GB of data processed that hour\.   | 

#### Call AWS Marketplace Metering Service<a name="call-aws-marketplace-metering-service"></a>

 Your software must call the Metering Service hourly and record the consumption value for that hour\. 

 When your software starts, it should record the minute\-of\-the\-hour at which it started\. This will be referred to as the *start\-minute*\. Every hour on the start\-minute, your software must retrieve the consumption value for that hour and call the Metering Service\. 

 To wake up each hour at the start\-minute, your software will need to use one of three approaches: 
+ A thread within your software\. 
+ A daemon process that starts up with the instance or software\. 
+ A cron job that is configured during application startup\. 

Your software must call the AWS Marketplace Metering Service using the IAM role configured on the customer’s instance and specify the consumption dimension and amount\. 

 Your software can use the AWS SDK to call the AWS Marketplace Metering Service\. The following is a typical implementation: 

1. Use the instance profile to create a service client\. This requires the role configured for the Amazon EC2 instance\. The role credentials are refreshed by the SDK automatically\.   
**Example**  

   ```
   AmazonMeteringService meteringClient = new AmazonMeteringService(new InstanceProfileCredentialsProvider());
   ```

1. Each hour, read your software configuration and state to determine consumption values for that hour\. This might include collecting a value\-per\-dimension\. 

1. Call the `MeterUsage` action on the SDK client with the following parameters \(call additionally for each dimension that has usage\): 
   +  `Timestamp` – Timestamp of the hour being recorded \(use UTC\)\. 
   +  `ProductCode` – The product code assigned to the software\. 
   +  `UsageDimension` – The dimensions assigned to the software\.
   +  `UsageQuantity`– The consumption value for the hour\. 

In addition, your software must call an in\-Region AWS Marketplace Metering Service endpoint\. Your product must have a correct Regional endpoint set up, so US East \(N\. Virginia\) sends records to the US East \(N\. Virginia\) endpoint, and US West \(Oregon\) sends records to the US West \(Oregon\) endpoint\. Making in\-Region calls provides buyers with a more stable experience\. It prevents situations in which an unrelated Region’s availability could impact software running in another Region\. 

 When you send metering records to the service, you must connect to the AWS Marketplace Metering Service in your Region\. Use the `getCurrentRegion` action to determine the Region in which the Amazon EC2 instance is running\. Then, pass this Region information to the `MeteringServiceClient` constructor\. If you don't specify a Region in the SDK constructor, it defaults to the US East \(N\. Virginia\) Region\. If your application attempts to make cross\-Region calls to the service, it will be rejected\. 

### Failure handling<a name="important-information-about-failure-handling"></a>

 Your product must send metering records to the service, a public internet endpoint, so that usage can be captured and billed\. It's possible for a customer to modify network settings in a way that prevents your metering records from being delivered\. Your product should account for this possibility by choosing a failure mode\.

Typically, software can fail open \(provide a warning message but maintain full functionality\) or fail closed \(disable all functionality in the application until a connection has been reestablished\)\. You can choose to fail open, closed, or something specific to your application\. We recommend that you refrain from failing closed after less than two hours of metering failures\.

 As an example of failing partially open, you could continue to allow access to the software but not allow the buyer to modify the software settings\. Or, a buyer could still access the software but would not be able to create additional users\. Your software is responsible for defining and enforcing this failure mode\. Your software’s failure mode must be included when your AMI is submitted, and it can't be changed later\. 