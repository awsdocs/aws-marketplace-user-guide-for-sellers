# Custom metering for container products with AWS Marketplace Metering Service<a name="container-metering-meterusage"></a>

AWS Marketplace container products can have custom metering on up to 24 different pricing dimensions per product\. Each dimension can have a long\-term contract price associated with it\. To enable custom metering, integrate your container product with AWS Marketplace Metering Service\. You can define your own pricing units and custom metering for that usage to AWS for billing using the [https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_MeterUsage.html](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_MeterUsage.html) API operation\.

Price dimensions are defined in two locations, once in the product load form and once through the `MeterUsage` operation\. This two\-factor method ensures that the subsequent offers are working as intended before they're made available to the public\.

To set up custom metering, you'll need to choose the usage category, the unit type, and pricing dimensions: 
+ **Usage category** – The usage category helps buyers understand what your product is and how to use it\. 
+ **Unit type** – The unit type defines the unit of measure for billing\. For example, bandwidth measured in GBps or MBps, the number of hosts, or data measured in MB, GB, or TB\.
+ **Pricing dimensions** – The pricing dimensions represents a feature or service that you've set a per\-unit price for \(for example, users, scans, vCPUs, or deployed agents\)\. Pricing dimensions are public\. However, you can still define private and Bring Your Own License \(BYOL\) offers for public products\. Don't send pricing in the metering records\. You meter the quantity of units, and we use that along with the prices you defined when creating your product to compute the buyer's bill\. 

  If your product pricing doesn't fit with any of the predefined categories or unit types, you can choose the generic **Units** category\. Then, use the dimension description to describe what the unit is\.

Optionally, you may distribute the usage into allocations by properties that you track\. The allocations are represented as tags to the buyer\. These tags allow the buyer to view their costs split into usage by tag values\. For example, if you charge by the user, and users have a "Department" property, you could create usage allocations with tags that have a key of "Department", and one allocation per value\. This does not change the price, dimensions, or the total usage that you report, but allows your customer to view their costs by categories appropriate to your product\.

We recommend that you send a metering record every hour\. However, you can aggregate usage over daily or monthly periods as well\. If you experience an outage, you can aggregate buyer software use and send it in the following hours metering\. You can't send more than one record per hour\.

**Important**  
Free trial and prepaid entitlement are tracked on an hourly level\. As a result, sending these records in separately might lead to the buyer being overcharged\.

## Custom metering prerequisites<a name="custom-metering-prereqs"></a>

Before publishing the product, you must do the following:

1. Create a new container product in the AWS Marketplace Management Portal, and make a note of its product code\.

1. Fill out the product load form with the necessary dimension information, and return it to us for processing\.

1. Use an AWS Identity and Access Management \(IAM\) role for the task or pod running your application with the IAM permissions necessary to call `MeterUsage`\. The IAM managed policy `AWSMarketplaceMeteringRegisterUsage` has these permissions\.

1. \(Optional\) We recommend that you enable AWS CloudTrail logging in the task or pod definition if you want to see logging\.

1. Make a test call to the `MeterUsage` API operation with a record for all of the pricing dimensions you define\.

## Product load form for custom metering<a name="custom-metering-product-load-form"></a>

When filling out the product load form for custom metering, each product can have up to 24 dimensions\. The dimensions are defined in the following fields:
+ **Dimension Name** – The name used when your container application is sending metering records to the AWS Marketplace Metering Service\. This name indicates which dimension your buyer will use\. This name is visible in billing reports\. After you set the name, you can't change it\.
+ **Dimension Description** – The buyer\-facing description for the dimension\. The description can't exceed 70 characters\. After the product is published publicly to buyers, this field can't be changed\.
+ **Dimension Rate** – The software price per unit for this product when buyers pay as they go\. This ﬁeld supports three decimal places\.
+ **Dimension Long Term Rate** – The total software price over a long\-term contract when buyers pay upfront\.
+ **Long Term Duration \(Days\)** – The duration, in days, for the long\-term contract\.

## Testing `MeterUsage` integration and preview mode<a name="custom-metering-preview-mode"></a>

Use the `MeterUsage` operation to test your integration before submitting your image to AWS Marketplace for publishing\.

Preview mode operates identically to production mode, except preview mode does not verify entitlement to use your product\. To call `MeterUsage` in preview mode, call `MeterUsage` from the container images by running your product on Amazon Elastic Container Service \(Amazon ECS\) or Amazon Elastic Kubernetes Service \(Amazon EKS\) with the AWS account you are using to list the product on AWS Marketplace\. Your metering integration must dynamically set the AWS Region, rather than hard coding it\. However, when testing, launch at least one Amazon ECS task or Amazon EKS pod containing your paid container in the US East \(N\. Virginia\) Region so that the AWS Marketplace operations team can verify your work with the logs in that Region\.

**Note**  
If your product supports both Amazon ECS and Amazon EKS, you only need to launch in Amazon EKS for us to validate your integration\.

You can't fully test the integration until your product is published with all the required metadata and pricing information\. If requested, the AWS Marketplace catalog operations team can verify receipt of your metering records in preview mode\.

## Error handling for `MeterUsage`<a name="custom-metering-entitlement-error-handling"></a>

If your container image integrates with the `MeterUsage` operation and receives an exception other than `ThrottlingException` at container startup, you should terminate the container to prevent unauthorized use\.

Exceptions other than `ThrottlingException` are thrown only on the initial call to `MeterUsage`\. Subsequent calls from the same Amazon ECS task or Amazon EKS pod do not throw `CustomerNotSubscribedException` even if the customer unsubscribes while the task or pod is still running\. These customers are still charged for running containers after they unsubscribe and their usage is tracked\.

See [MeterUsage](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_MeterUsage.html) in the *AWS Marketplace Metering Service API Reference*for detailed descriptions of common errors for `MeterUsage`\. Each AWS SDK programming language has a set of error handling guidelines that you can refer to for additional information\. 

## Vendor\-metered tagging \(Optional\)<a name="container-vendor-metered-tagging"></a>

Vendor\-metered tagging helps Independent Software Vendors \(ISVs\) give the buyer more granular insight into their software usage and can help them perform cost allocation\.

There are many ways to tag a buyer's software usage\. One way is to first ask your buyers what they want to see in their cost allocation\. Then you can split the usage across properties that you track for the buyer’s account\. Examples of properties include `AccountId`, `Business Unit`, `Cost Centers`, and other relevant metadata for your product\. These properties are exposed to the buyer as tags\. Using tags, buyers can view their costs split into usage by the tag values in their AWS Billing Console \([https://console\.aws\.amazon\.com/billing/](https://console.aws.amazon.com/billing/)\)\. Vendor\-metered tagging doesn't change the price, dimensions, or the total usage that you report\. It allows your customer to view their costs by categories appropriate to your product\.

In a common use case, a buyer subscribes to your product with one AWS account\. The buyer also has numerous user accounts associated with the same product subscription\. You can create usage allocations with tags that have a key of `AccountId`, and then allocate usage to each user account\. In this case, buyers can activate the `AccountId` tag in their Billing and Cost Management console and analyze individual user account usage\.

### Seller experience<a name="container-vendor-metered-tag-seller"></a>

Sellers can aggregate the metering records for resources with the same set of tags instead of aggregating usage for all resources\. For example, sellers can construct the metering record that includes different buckets of `UsageAllocations`\. Each bucket represents `UsageQuantity` for a set of tags, such as `AccountId` and `BusinessUnit`\. 

In the following diagram, **Resource 1** has a unique set of `AccountId` and `BusinessUnit` tags, and appears in the **Metering Record** as a single entry\. 

**Resource 2** and **Resource 3** both have the same `AccountId` tag, `2222`, and the same `BusinessUnit` tag, `Operations`\. As a result, they're combined into a single `UsageAllocations` entry in the **Metering Record**\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/seller-vendor-meter-tag.png)

Sellers can also combine resources without tags into a single `UsageAllocation` with the allocated usage quantity and send it as one of the entries in `UsageAllocations`\.

Limits include:
+ Number of tags – 5
+ Size of `UsageAllocations` \(cardinality\) – 2,500

Validations include:
+ Characters allowed for the tag key and value – a\-zA\-Z0\-9\+ \-=\.\_:\\/@
+ Maximum tags across `UsageAllocation` list – 5
+ Two `UsageAllocations` can't have the same tags \(that is, the same combination of tag keys and values\)\. If that's the case, they must use the same `UsageAllocation`\.
+ The sum of `AllocatedUsageQuantity` of `UsageAllocation` must equal the `UsageQuantity`, which is the aggregate usage\.

### Buyer experience<a name="container-vendor-metered-tag-buyer"></a>

The following table shows an example of the buyer experience after a buyer activates the `AccountId` and `BusinessUnit` vendor tags\. 

In this example, the buyer can see allocated usage in their **Cost Usage Report**\. The vendor\-metered tags use the prefix `“aws:marketplace:isv”`\. Buyers can activate them in the Billing and Cost Management, under **Cost Allocation Tags**, **AWS\-generated cost allocation tags**\.

The first and last rows of the **Cost Usage Report** are relevant to what the Seller sends to the Metering Service \(as shown in the [Seller experience](#container-vendor-metered-tag-seller) example\)\.


**Cost Usage Report \(Simplified\)**  

| ProductCode  | Buyer | UsageDimension | UsageQuantity | `aws:marketplace:isv:AccountId ` | `aws:marketplace:isv:BusinessUnit` | 
| --- | --- | --- | --- | --- | --- | 
| xyz | 111122223333 | Network: per \(GB\) inspected  | 70 | 2222 | Operations | 
| xyz | 111122223333 | Network: per \(GB\) inspected  | 30 | 3333 | Finance | 
| xyz | 111122223333 | Network: per \(GB\) inspected  | 20 | 4444 | IT | 
| xyz | 111122223333 | Network: per \(GB\) inspected  | 20 | 5555 | Marketing | 
| xyz | 111122223333 | Network: per \(GB\) inspected  | 30 | 1111 | Marketing | 

For a code example, see [`MeterUsage` code example with usage allocation tagging \(Optional\)](#container-meterusage-code-example)\.

## Code example<a name="container-meter-code-example"></a>

The following code example is provided to help you integrate your container product with the AWS Marketplace APIs required for publishing and maintaining your product\.

### `MeterUsage` code example with usage allocation tagging \(Optional\)<a name="container-meterusage-code-example"></a>

The following code example is relevant for container products with consumption pricing models\. The Python example sends a metering record with appropriate usage allocation tags to AWS Marketplace to charge your customers for pay\-as\-you\-go fees\.

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

### Example response<a name="container-meterusage-code-response"></a>

```
{ "MeteringRecordId": "string" }
```