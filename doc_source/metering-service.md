# Metering service<a name="metering-service"></a>

 The AWS Marketplace Metering Service is a pricing and metering feature that sellers can use to directly charge for their software by one of four usage categories: users, data, bandwidth, or hosts\. You can use the Metering Service with AMI\-based, container\-based, and SaaS\-based products\. For more information, see the [https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html)\.

All AMI\-based software that uses the Metering Service must meet the following requirements: 
+ Your software must be launched from AWS Marketplace through an Amazon Machine Image \(AMI\)\. 
+ If you have an existing product in AWS Marketplace, you must submit a new AMI and create a new product to enable this feature\. 
+ All software must be provisioned with an AWS Identity and Access Management \(IAM\) role\. The end customer must add an IAM role to the Amazon EC2 instance the user is provisioning with the software\. Currently, the use of an IAM role is optional when you deploy software through AWS Marketplace\. It is required when you deploy AWS Marketplace Metering Service software\. 
+ Your software must be able to determine consumption in some way\. 

Products that use the Metering Service must charge customers along a single usage category, but you can define up to 24 dimensions of a single category\. Depending on the category, software can be priced by provisioned resources, concurrent resources, or accumulated resource consumption\. All charges are still incurred hourly by the customer\. All usage is calculated and billed monthly using the same mechanism as existing AWS Marketplace software\. 

The AWS Marketplace Metering Service enables several new scenarios\. For example, if your software monitors hosts, you can charge for each host monitored\. You can have different prices based on the host size, and charge for the number of concurrent hosts monitored each hour\. Similarly, if your software allows many users across an organization to sign in, you can charge by the number of users\. Each hour, the customer is charged for the total number of provisioned users\. 

## Metering service concepts<a name="metering-service-concepts"></a>

The AWS Marketplace Metering Service enables software sellers to modify their software to send metering records to an endpoint to capture usage\. Sellers can select a usage category and define up to 24 dimensions of that one category\. These dimensions are metered once per hour, aggregated, and charged against a price plan defined by the seller\. As a seller, the first thing you need to do is determine which dimension you want to use\. After the AMI is published, you will not be able to change it\. Important service concepts include the following: 
+  **Usage Category** \- Any software product priced through the use of the Metering Service will select one usage category along which to charge customers, including but not limited to: 
  + Users \- A defined set of permissions associated with a single identifier\. This category is appropriate for software in which a customer’s users connect to the software directly \(for example, for customer\-relationship management or business intelligence reporting\)\. 
  + Hosts \- Any server, node, instance, endpoint, or other part of a computing system\. This category is appropriate for software that monitors or scans many customer\-owned instances \(for example, performance or security monitoring\)\. 
  + Data \- Storage or information, measured in MB, GB, or TB\. This category is appropriate for software that manages stored data or processes data in batches\. 
  + Unit \- Unit of measurement; see the examples described next\.
+  **Usage Unit** – A software product will select a specific usage unit corresponding to the selected usage category\. This is usually more specific and describes the unit your software will charge on\. Examples include: 
  + NodesHrs \(corresponding to the Hosts category\)
  + UserHrs \(corresponding to the User category\)
  + GBStored \(corresponding to the Data category\)
+  **Consumption** \- Any software product priced through the use of the Metering Service will charge for consumption in one of three ways: 
  +  Provisioned \- The software allows customers to configure a specific amount of resources for use \(for example, number of users or a fixed amount of bandwidth\)\. Each hour, customers pay for what they have provisioned\. 
  +  Concurrent \- The software allows any number of distinct hosts or users to connect to the software\. Each hour, customers pay based on the number of hosts or users who accessed the software\. 
  +  Accumulated \- The software allows customers to use any amount of data, either processed or stored\. Each hour, customers pay for the aggregated amount\. 
+  **Pricing** \- Any software product priced through the use of the Metering Service must specify either a single price or define up to 24 dimensions, each with their own price\. 
  +  Single dimension \- This is the simplest pricing option\. Customers pay a single price per resource unit per hour, regardless of size or volume \(for example, $0\.014 per user per hour, or $0\.070 per host per hour\)\. 
  +  Multiple dimensions \- This pricing option is appropriate when the selected usage category varies along multiple axes\. For example, for host monitoring, a different price could be set depending on the size of the host\. Or for user\-based pricing, a different price could be set based on the type of user \(for example, admin, power user, and read\-only user\)\. 
+  **Metering** \- All usage is recorded as a metering event, once each hour\. Your software must be configured to send the appropriate dimension and usage amount to the AWS Marketplace Metering Service\. 

## Pricing your software<a name="pricing-your-software"></a>

 When pricing your software with the AWS Marketplace Metering Service, you must first decide on a usage category and how it will be consumed\. At this time, the service supports six distinct pricing scenarios\. You must select only one of these for your product: 
+  Provisioned user \(per hour\) 
+  Concurrent user \(per hour\) 
+  Provisioned host \(per hour\) 
+  Concurrent host \(per hour\) 
+  Provisioned bandwidth \(per hour\) 
+  Accumulated data \(per hour\) 

 Next, you must decide how to price the selected usage category: 
+  Single price 
+  Multiple dimensions \(up to 24\) 

 [Adding your product to AWS Marketplace ](#listing-your-product-on-aws-marketplace) describes how to provide a customer\-friendly description of your dimension and pricing\. 

### Example: Provisioned bandwidth with nonlinear pricing<a name="example-provisioned-bandwidth-with-non-linear-pricing"></a>

 Imagine you offer network appliance software\. You choose to bill by provisioned bandwidth\. For your usage category, select bandwidth\. In addition to charging by bandwidth, you want to charge a different price as buyers scale up\. You can define multiple dimensions within the bandwidth category\. You can define a distinct price for 25 Mbps, 100 Mbps, and 1 Gbps\. 

### Example: Concurrent hosts with multiple dimensions<a name="example-concurrent-hosts-with-multiple-dimensions"></a>

 Imagine you offer software that monitors other Amazon EC2 instances\. You choose to bill by the number of hosts that are being monitored\. For your usage category, select host\. In addition to charging by host, you want to charge for the extra value for monitoring larger hosts\. You can use multiple dimensions within the host category\. You can define a distinct price for micro, small, medium, large, x\-large, 2XL, 4XL, 8XL instances\. Your software is responsible for mapping each particular host to one of your defined dimensions\. Your software is responsible for sending a separate metering record for each dimension of your usage category if applicable\. 

## Adding your product to AWS Marketplace<a name="listing-your-product-on-aws-marketplace"></a>

 To take advantage of the Metering Service, you must create a new product for AWS Marketplace to list\. If your product is already on the AWS Marketplace, you will need to decide whether the new AWS Marketplace Metering Service product will be made available in addition to your current product, or if it will replace your current product as the only version available to new users\. If you choose replacement, the existing product will be removed from the AWS Marketplace so that it is no longer available for new buyers\. Existing customers will continue to have access to their old product and instances, but they can migrate to the new product at their convenience\. The new product must meter usage to the AWS Marketplace Metering Service, as described in [Modifying your software to use the Metering Service](#modifying-your-software-to-use-the-metering-service)\.

 After you have your AMI, follow the standard process to share and scan your AMI using the self\-service tool\. In addition to using the template available on the management portal, fill out the product load form and upload it to start the ingestion process\. 

Use the following definitions to complete the fields of the product load form for the AWS Marketplace Metering Service\. On the product load form, these fields are labeled as Flexible Consumption Pricing \(FCP\) to differentiate them from hourly and monthly priced products\. 
+  **Title**: If you already have a product on AWS Marketplace and you are adding the same product with the AWS Marketplace Metering Service, include the FCP category/dimension in parentheses to differentiate the two \(for example, “PRODUCT TITLE \(Data\)”\)\. 
+  **Pricing Model**: From the drop\-down list, choose **Usage**\. 
+  **FCP Category**: The category in which customers are charged for paid products with a **Usage** pricing component\. From the drop\-down list, choose **Users**, **Hosts**, **Data**, or **Bandwidth**\. 
+  **FCP Unit**: The unit of measurement on which customers will be charged for paid products with a **Usage** pricing component\. Options will appear in the drop\-down list based on the FCP category you selected\. The following table lists the valid units for each category\. 


|   **Category **   |   **Valid Units **   | 
| --- | --- | 
|  Users  |   UserHrs   | 
|  Hosts  |   HostHrs   | 
|  Data  |   MB, GB, TB   | 
|  Bandwidth  |   Mbps, Gbps   | 
+  **FCP Dimension Name**: The name used when sending metering records by calling MeterUsage API\. It is visible in billing reports, but because it is not external\-facing, the name does not need to be user friendly\. The name can be no more than 15 characters and can only include alphanumeric and underscore characters\. After you set the name, you cannot change it\. Changing the name requires a new AMI\. 
+  **FCP Dimension Description**: The customer\-facing statement that describes the dimension for the product\. The description \(for example, Administrators per hour, Per Mbps bandwidth provisioned\) can be no more than 70 characters and should be user\-friendly\. After the product is published, you cannot change this description\. 
+  **FCP Rate**: The software charge per unit for this product\. This field supports 3 decimal places\. 

**Notes:**  
You do not need to fill out hourly and annual pricing fields\. 
Free trial and annual pricing are not compatible\. 
Currently, products that use multiple AMIs and the Clusters and AWS Resources feature cannot use the AWS Marketplace Metering Service\. 
Price, instance type, or region change will follow the regular process as other AWS Marketplace products\.
Products with the AWS Marketplace Metering Service cannot be converted to other pricing models such as hourly, monthly, or BYOL\. 
AWS Marketplace recommends adding IAM policy information in your usage instructions or document\. 

If you have questions, contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

## Modifying your software to use the Metering Service<a name="modifying-your-software-to-use-the-metering-service"></a>

 You will need to modify your software to record customer usage, send hourly usage reports to the Metering Service, and handle new failure modes\. The software operates independently of pricing, but the software will need to know about the usage category, how it is consumed, and any dimensions\. 

### Measuring consumption<a name="measuring-consumption"></a>

 Your software must determine how much of the selected usage category and which dimensions the customer has consumed\. This value will be sent, once each hour, to the AWS Marketplace Metering Service\. In all cases, it is assumed that your software has the ability to measure, record, and read consumption of resources for the purpose of sending it on an hourly basis to the Metering Service\. 

 For provisioned consumption, this will typically be read from the software configuration as a sampled value, but might also be a maximum configured value, recorded each hour\. For concurrent consumption, this might be either a periodic sample or a maximum value recorded each hour\. For accumulated consumption, this will be a value that is accumulated each hour\. 

 For pricing on multiple dimensions, multiple values must be measured and sent to the Metering Service, one per dimension\. This requires your software to be programmed or configured with the known set of dimensions when you provide the AMI\. The set of dimensions cannot change after a product is created\. 

 For each pricing scenario, this table describes recommended ways for measuring consumption each hour: 


|  **Scenario **  |  **How to measure **  | 
| --- | --- | 
|  Provisioned user   |  Current number of provisioned users \(sampled\)\.  \-OR\-  Maximum number of provisioned users \(seen that hour\)\.   | 
|  Concurrent user   |  Current number of concurrent users \(sampled\)\.  \-OR\-  Maximum number of concurrent users \(seen that hour\)\.  \-OR\-  Total number of distinct users \(seen that hour\)\.   | 
|  Provisioned host   |  Current number of provisioned hosts \(sampled\)\.  \-OR\-  Maximum number of provisioned hosts \(seen that hour\)\.   | 
|  Concurrent host   |  Current number of concurrent hosts \(sampled\)\.  \-OR\-  Maximum number of concurrent hosts \(seen that hour\)\.  \-OR\-  Total number of distinct hosts \(seen that hour\)\.   | 
|  Provisioned bandwidth   |  Current provisioned bandwidth setting \(sampled\)\.  \-OR\-  Maximum provisioned bandwidth \(seen that hour\)\.   | 
|  Accumulated data   |  Current GB of data stored \(sampled\)\.  \-OR\-  Maximum GB of data stored \(seen that hour\)\.  \-OR\-  Total GB of data added or processed that hour\.  \-OR\-  Total GB of data processed that hour\.   | 

## Call AWS Marketplace Metering Service<a name="call-aws-marketplace-metering-service"></a>

 Your software must call the Metering Service hourly and record the consumption value for that hour\. 

 When your software starts, it should record the minute\-of\-the\-hour at which it started\. This will be referred to as the *start\-minute*\. Every hour on the start\-minute, your software must retrieve the consumption value for that 

 hour and call the Metering Service\. For information about how to obtain this value, see the *Measuring Consumption* section\. 

 To wake up each hour at the start\-minute, your software must use one of three approaches: 
+  A thread within your software\. 
+  A daemon process that starts up with the instance or software\. 
+  A cron job that is configured during application startup\. 
**Note**  
 Your software must call the AWS Marketplace Metering Service using the IAM role configured on the customer’s instance and specify the consumption dimension and amount\. 

Your software can use the AWS SDK to call the AWS Marketplace Metering Service, similar to this example implementation\. 

1. Use the instance profile to create a service client\. This requires the role configured for the EC2 instance\. 

 The role credentials are refreshed by the SDK automatically\. 

 AmazonMeteringService meteringClient = new AmazonMeteringService\(new InstanceProfileCredentialsProvider\(\)\); 

1. Each hour, read your software configuration and state to determine consumption values for that hour\. This might include collecting a value\-per\-dimension\. 

1. Call the `meterUsage` method on the SDK client with the following parameters \(call additionally for each dimension that has usage\): 
   +  `timestamp`: timestamp of the hour being recorded\. \(Use UTC\.\) 
   +  `productCode`: product code assigned to the software\. 
   +  `dimension`: dimension \(or dimensions\) assigned to the software 
   +  `quantity`: consumption value for the hour 

In addition, your software must call an in\-region AWS Marketplace Metering Service endpoint\. Your product must have a correct regional endpoint set up, so `us-east-1` sends records to a `us-east-1` endpoint, and `us-west-2` sends records to a `us-west-2` endpoint\. Making in\-region calls provides buyers with a more stable experience and prevents situations in which an unrelated region’s availability could impact software running in another region\. 

When you send metering records to the service, you must connect to the AWS Marketplace Metering Service in your region\. Use the `getCurrentRegion()` helper method to determine the region in which the EC2 instance is running, and then pass this region information to the `MeteringServiceClient` constructor\. If you do not specify an AWS Region in the SDK constructor, the default, `us-east-1`, is used\. If your application attempts to make cross\-region calls to the service, the calls are rejected\. For more information, see [Determining an Application’s Current Region](https://java.awsblog.com/post/Tx3GBOIEN1JJMQ5/Determining-an-Application-s-Current-Region) and [getCurrentRegion\(\)](http://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/regions/Regions.html#getCurrentRegion())\. 

## Failure handling<a name="important-information-about-failure-handling"></a>

Your product must send metering records to the service, a public internet endpoint, so that usage can be captured and billed\. Because it is possible for a customer to modify network settings in a way that prevents your metering records from being delivered, your product should account for this by choosing a failure mode\. 

Typically, software can fail open \(provide a warning message but maintain full functionality\) or fail closed \(disable all functionality in the application until a connection has been reestablished\)\. You can choose to fail open, closed, or something specific to your application\. We strongly recommend that you refrain from failing closed after less than two hours of metering failures\. 

As an example of failing partially open, you could continue to allow access to the software but not allow the buyer to modify the software settings\. Or, a buyer could still access the software, but would not be able to create additional users\. Your software is responsible for defining and enforcing this failure mode\. Your software’s failure mode must be included when your AMI is submitted, and it cannot be changed later\. 

## Limitations<a name="limitations"></a>

 Keep these limitations in mind when designing and submitting your Metering Service\-enabled software: 
+ ** IAM role and internet gateway requirements for your customers** \- Your customers must have an internet gateway and must launch your software with an IAM role with specific permissions\. For more information, see [AWS Marketplace metering and entitlement API permissions](iam-user-policy-for-aws-marketplace-actions.md)\. Your software cannot connect to the Metering Service if these two conditions are not met\. 
+  **Inability to add or change new usage category or dimensions to existing Metering Service product** \- When customers subscribe to your software product, they are agreeing to terms and conditions\. Changing the dimensions in products with the Metering Service requires a new product and a new subscription\. 
+  **Lack of free trial and annual subscriptions** \- Metering Service products do not support free trials and annual subscriptions at launch\. 
+  **Multi\-instance or cluster\-based deployment considerations** \- Some software is deployed as part of a multi\-instance deployment\. When you design your software, consider how and where consumption is measured and where metering records are emitted\. 