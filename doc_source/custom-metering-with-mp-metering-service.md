# Custom metering for AMI products with AWS Marketplace Metering Service<a name="custom-metering-with-mp-metering-service"></a>

The AWS Marketplace Metering Service is a pricing and metering feature that sellers can use to directly charge for their software by usage category\. There are five usage categories: users, data, bandwidth, hosts, or unit\. You can use the Metering Service with Amazon Machine Image \(AMI\)\-based, container\-based, and software as a service \(SaaS\)\-based products\. For more information, see the [https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html)\.

All AMI\-based software that uses the Metering Service must meet the following requirements: 
+ Your software must be launched from AWS Marketplace through an Amazon Machine Image \(AMI\)\. 
+ If you have an existing product in AWS Marketplace, you must submit a new AMI and create a new product to enable this feature\. 
+ All software must be provisioned with an AWS Identity and Access Management \(IAM\) role\. The end customer must add an IAM role to the Amazon Elastic Compute Cloud \(Amazon EC2\) instance the user is provisioning with the software\. The use of an IAM role is optional when you deploy software through AWS Marketplace\. It's required when you deploy AWS Marketplace Metering Service software\. 
+ Your software must be able to determine consumption in some way\. 

Products that use the Metering Service must charge customers by a single usage category, but you can define up to 24 dimensions of a single category\. Depending on the category, software can be priced by provisioned resources, concurrent resources, or accumulated resource consumption\. All charges are still incurred hourly by the customer\. All usage is calculated and billed monthly using the same mechanism as existing AWS Marketplace software\.

The AWS Marketplace Metering Service enables several new scenarios\. For example, if your software monitors hosts, you can charge for each host monitored\. You can have different prices based on the host size, and charge for the number of concurrent hosts monitored each hour\. Similarly, if your software allows many users across an organization to sign in, you can charge by the number of users\. Each hour, the customer is charged for the total number of provisioned users\. 

## Call AWS Marketplace Metering Service<a name="call-aws-marketplace-metering-service"></a>

 Your software must call the Metering Service hourly and record the consumption value for that hour\. 

 When your software starts, it should record the minute\-of\-the\-hour at which it started\. This is referred to as the *start\-minute*\. Every hour on the start\-minute, your software must retrieve the consumption value for that hour and call the Metering Service\. For information about how to obtain this value, see the linkend="custom\-metering\-pricing\-ami\-products" endterm="custom\-metering\-pricing\-ami\-products\.title"/> section\.

 To wake up each hour at the start\-minute, your software must use one of the following approaches: 
+  A thread within your software\. 
+  A daemon process that starts up with the instance or software\. 
+  A cron job that is configured during application startup\. 
**Note**  
 Your software must call the AWS Marketplace Metering Service using the IAM role configured on the customer’s instance and specify the consumption dimension and amount\. 

Your software can use the AWS SDK to call the AWS Marketplace Metering Service, similar to the following example implementation: 

1. Use the instance profile to create a service client\. This requires the role configured for the EC2 instance\. The role credentials are refreshed by the SDK automatically\.

1. Each hour, read your software configuration and state to determine consumption values for that hour\. This might include collecting a value\-per\-dimension\. 

1. Call the `meterUsage` method on the SDK client with the following parameters \(call additionally for each dimension that has usage\): 
   + `timestamp` – Timestamp of the hour being recorded \(in UTC\)\. 
   + `productCode` – Product code assigned to the software\. 
   + `dimension` – Dimension \(or dimensions\) assigned to the software\. 
   + `quantity` – Consumption value for the hour\. 
   + `allocations` – \(Optional\) You may provide allocations for the usage across properties that you track\. These allocations must add up to the total consumption in the record\. To the buyer, these display as potential cost allocation tags in their billing tools \(such as the AWS Billing and Cost Management console\)\. The buyer must activate the tags in their account in order to track their cost using these tags\.

In addition, your software must call an in\-Region AWS Marketplace Metering Service endpoint\. Your product must have a correct Regional endpoint set up, so `us-east-1` sends records to a `us-east-1` endpoint, and `us-west-2` sends records to a `us-west-2` endpoint\. Making in\-Region calls provides buyers with a more stable experience and prevents situations in which an unrelated Region’s availability could impact software running in another Region\. 

When you send metering records to the service, you must connect to the AWS Marketplace Metering Service in your Region\. Use the `getCurrentRegion()` helper method to determine the Region in which the EC2 instance is running, and then pass this Region information to the `MeteringServiceClient` constructor\. If you don't specify an AWS Region in the SDK constructor, the default `us-east-1` Region is used\. If your application attempts to make cross\-Region calls to the service, the calls are rejected\. For more information, see [Determining an Application’s Current Region](https://java.awsblog.com/post/Tx3GBOIEN1JJMQ5/Determining-an-Application-s-Current-Region) and [getCurrentRegion\(\)](http://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/regions/Regions.html#getCurrentRegion())\. 

## Failure handling<a name="important-information-about-failure-handling"></a>

Your product must send metering records to the service, a public internet endpoint, so that usage can be captured and billed\. Because it's possible for a customer to modify network settings in a way that prevents your metering records from being delivered, your product should account for this by choosing a failure mode\. 

**Note**  
Some metering failures may be transient issues in connecting to the AWS Marketplace Metering Service\. AWS Marketplace strongly recommends implementing retries for up to 30 minutes, with exponential back off, to avoid short\-term outages or network issues\.

Typically, software can fail open \(provide a warning message but maintain full functionality\) or fail closed \(disable all functionality in the application until a connection has been reestablished\)\. You can choose to fail open, closed, or something specific to your application\. We strongly recommend that you refrain from failing closed after less than two hours of metering failures\. 

As an example of failing partially open, you could continue to allow access to the software but not allow the buyer to modify the software settings\. Or, a buyer could still access the software but would not be able to create additional users\. Your software is responsible for defining and enforcing this failure mode\. Your software’s failure mode must be included when your AMI is submitted, and it can't be changed later\. 

## Limitations<a name="limitations"></a>

 Keep these limitations in mind when designing and submitting your Metering Service\-enabled software: 
+ **IAM role and internet gateway requirements for your customers** – Your customers must have an internet gateway and must launch your software with an IAM role with specific permissions\. For more information, see [AWS Marketplace metering and entitlement API permissions](iam-user-policy-for-aws-marketplace-actions.md)\. Your software can't connect to the Metering Service if these two conditions aren't met\. 
+  **Inability to add new or change usage category to existing Metering Service product** – When customers subscribe to your software product, they're agreeing to terms and conditions\. Changing the usage categories in products with the Metering Service requires a new product and a new subscription\. 
+ **Inability to change dimensions to existing Metering Service product** – When customers subscribe to your software product, they're agreeing to terms and conditions\. Changing the dimensions in products with the Metering Service requires a new product and a new subscription\. You *can* add new dimensions to existing products, up to the limit of 24\.
+  **Lack of free trial and annual subscriptions** – Metering Service products don't support free trials and annual subscriptions at launch\. 
+  **Multi\-instance or cluster\-based deployment considerations** – Some software is deployed as part of a multi\-instance deployment\. When you design your software, consider how and where consumption is measured and where metering records are emitted\. 

## Code example<a name="ami-metering-code-example"></a>

The following code example is provided to help you integrate your AMI product with the AWS Marketplace APIs required for publishing and maintaining your product\.

### `MeterUsage` with usage allocation tagging \(Optional\)<a name="ami-meterusage-code-example"></a>

The following code example is relevant for AMI products with consumption pricing models\. The Python example sends a metering record with appropriate usage allocation tags to AWS Marketplace to charge your customers for pay\-as\-you\-go fees\.

```
# NOTE: Your application will need to aggregate usage for the 
#       customer for the hour and set the quantity as seen below. 
#       AWS Marketplace can only accept records for up to an hour in the past. 
#
# productCode is supplied after the AWS Marketplace Ops team has 
# published the product to limited

# Import AWS Python SDK
import boto3
import time

usageRecord = [
    { 
        "AllocatedUsageQuantity": 2, 
        "Tags": 
            [ 
                { "Key": "BusinessUnit", "Value": "IT" },
                { "Key": "AccountId", "Value": "123456789" },
            ]

    },
    { 
        "AllocatedUsageQuantity": 1, 
        "Tags": 
            [ 
                { "Key": "BusinessUnit", "Value": "Finance" },
                { "Key": "AccountId", "Value": "987654321" },
            ]

    }
]

marketplaceClient = boto3.client("meteringmarketplace")

response = marketplaceClient.meter_usage(
    ProductCode="testProduct",
    Timestamp=int(time.time()),
    UsageDimension="Dimension1",
    UsageQuantity=3,
    DryRun=False,
    UsageAllocations=usageRecord 
)
```

For more information about `MeterUsage`, see [MeterUsage](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_MeterUsage.html) in the *AWS Marketplace Metering Service API Reference*\.

### Example response<a name="ami-meterusage-code-response"></a>

```
{ "MeteringRecordId": "string" }
```