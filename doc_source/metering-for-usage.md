# Metering for usage<a name="metering-for-usage"></a>

For software as a service \(SaaS\) subscriptions, you meter for all usage, and then customers are billed by AWS based on the metering records that you provide\. For SaaS contracts, you only meter for usage beyond a customer’s contract entitlements\. When your application meters usage for a customer, your application is providing AWS with a quantity of usage accrued\. Your application meters for the pricing dimensions that you defined when you created your product, such as gigabytes transferred or hosts scanned in a given hour\. For example, if you charge based on the amount of data sent into your application, you can measure the amount of data and send a corresponding metering record once an hour\. AWS calculates a customer’s bill using the metering data along with the prices that you provided when you created your product\.

**Note**  
Optionally, you can split the usage across properties that you track\. These properties are exposed to the buyer as tags\. These tags allow the buyer to view their costs split into usage by the tag values\. For example, if you charge by the user, and users have a `Department` property, you could create a usage allocations with tags that have a key of `Department`, and one allocation per value\. This doesn't change the price, dimensions, or the total usage that you report, but allows your customer to view their costs by categories appropriate to your product\. For more information, see [Vendor\-metered tagging \(Optional\)](#saas-vendor-metered-tagging)\.

We recommend that you send a metering record every hour to give customers as much granular visibility into their usage and costs as possible\. If you aggregate usage in time periods greater than an hour \(for example, one day\), continue sending metering records every hour and record a quantity of 0 if there is no usage to report for that hour\. Report usage to AWS on an hourly basis for all of your customers, in batches of up to 25 at a time\. 

AWS can only bill customers for usage of your product upon receiving metering records from you\. You're responsible for ensuring that your product’s metering records are successfully transmitted and received\. You can use AWS CloudTrail to verify the record or records that you send are accurate\. You can also use the information to perform audits over time\. For more information, see [Logging AWS Marketplace API calls with AWS CloudTrail](logging-aws-marketplace-api-calls-with-aws-cloudtrail.md)\. 

**Note**  
If your SaaS product is integrated with another AWS managed service that handles metering in a different way \(such as Amazon SageMaker Ground Truth, or AWS WAF\), then you do not need to integrate with AWS Marketplace metering service\. Metering for your product should only happen in one system to avoid double billing your customer\.

## Configure your product to meter usage<a name="configure-application-for-meter-usage"></a>

 You use the `BatchMeterUsage` operation in the AWS Marketplace Metering Service to deliver metering records to AWS\. Keep the following in mind: 
+  We require sellers to use batching by using the `BatchMeterUsage` operation\. 
+  We deduplicate metering requests on the hour\. 
  +  Requests are deduplicated per product/customer/hour/dimension\. 
  +  You can always retry any request, but if you meter for a different quantity, the original quantity is billed\. 
  +  If you send multiple requests for the same customer/dimension/hour, the records are not aggregated\. 
+ Sellers can send metering records with a timestamp up to 6 hours in the past if the customer is subscribed to your product\. If the customer unsubscribes, sellers have to send the metering records within 1 hour of the customer unsubscribing\. 
+ `BatchMeterUsage` payloads must not exceed 1MB\. Choose the number of usage records to send in a `BatchMeterUsage` request so that you don't exceed the size of the payload\.
+  The AWS Marketplace Metering Service is available in the AWS Regions listed in [AWS Marketplace endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/aws-marketplace.html) in the *AWS General Reference*\. By default, the US East \(N\. Virginia\) Region is enabled for SaaS metering products when you request your product\. If you intend to use other Regions, contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. For more information, see [BatchMeterUsage](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_BatchMeterUsage.html)\. 

For code examples, see [Code examples for SaaS product integration](saas-code-examples.md)\.

### Example: Host scanning<a name="host-scanning-example"></a>

 Your product analyzes computing hardware for known security vulnerabilities\. Customers manually initiate or schedule these scans of their Amazon Elastic Compute Cloud \(Amazon EC2\) instances\. As your product performs these scans, it tallies the number of unique hosts scanned every hour\. In this example, your product uses the **Hosts** category\. You can declare multiple dimensions for the types of hosts scanned\. For example, you can charge different prices for small, medium, and large hosts\. 

### Example: Log analysis<a name="log-analysis-example"></a>

 Your SaaS product digests logs that are generated by customer products, reporting trends, and anomalies\. As customers upload logs to your product, you measure the quantity of data received in megabytes, gigabytes, or terabytes\. On the tenth minute of every hour, a cron job reads this usage for each customer for the previous hour\. The job builds a batch report and uses the `BatchMeterUsage` operation to send it to AWS\. In this example, your product uses the **Data** category\. Your product can also meter for the amount of log data stored for any given hour\. In this case, your product can meter along two dimensions: data received in the hour and total data stored in the hour\. You can continue to meter for data stored until the customer deletes this data or it expires\. 

## Vendor\-metered tagging \(Optional\)<a name="saas-vendor-metered-tagging"></a>

Vendor\-metered tagging helps Independent Software Vendors \(ISVs\) give the buyer more granular insight into their software usage and can help them perform cost allocation\.

There are many ways to tag a buyer's software usage\. One way is to first ask your buyers what they want to see in their cost allocation\. Then you can split the usage across properties that you track for the buyer’s account\. Examples of properties include `Account ID`, `Business Unit`, `Cost Centers`, and other relevant metadata for your product\. These properties are exposed to the buyer as tags\. Using tags, buyers can view their costs split into usage by the tag values in their AWS Billing Console \([https://console\.aws\.amazon\.com/billing/](https://console.aws.amazon.com/billing/)\)\. Vendor\-metered tagging doesn't change the price, dimensions, or the total usage that you report\. It allows your customer to view their costs by categories appropriate to your product\.

In a common use case, a buyer subscribes to your product with one AWS account\. The buyer also has numerous user accounts associated with the same product subscription\. You can create usage allocations with tags that have a key of `Account ID`, and then allocate usage to each user account\. In this case, buyers can activate the `Account ID` tag in their Billing and Cost Management console and analyze individual user account usage\.

### Seller experience<a name="saas-vendor-metered-tag-seller"></a>

Sellers can aggregate the metering records for resources with the same set of tags instead of aggregating usage for all resources\. For example, sellers can construct the metering record that includes different buckets of `UsageAllocations`\. Each bucket represents `UsageQuantity` for a set of tags, such as `AccountId` and `BusinessUnit`\. 

In the following diagram, **Resource 1** has a unique set of `AccountId` and `BusinessUnit` tags, and appears in the **Metering Record** as a single entry\. 

**Resource 2** and **Resource 3** both have the same `AccountId` tag, `2222`, and the same `BusinessUnit` tag, `Operations`\. As a result, they're combined into a single `UsageAllocations` entry in the **Metering Record**\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/seller-vendor-meter-tag.png)

Sellers can also combine resources without tags into a single `UsageAllocation` and send it as one of the entries in `UsageAllocations`\.

Limits include:
+ Number of tags – 5
+ Size of `UsageAllocations` \(cardinality\) – 2,500
+ Maximum request size – 1 MB 

Validations include:
+ Characters allowed for the tag key and value – a\-zA\-Z0\-9\+ \-=\.\_:\\/@
+ Maximum tags across `UsageAllocation` list – 5
+ Two `UsageAllocations` can't have the same tags \(that is, the same combination of tag keys and values\)\. If that's the case, they must use the same `UsageAllocation`\.
+ The sum of `AllocatedUsageQuantity` of `UsageAllocation` must equal the `UsageQuantity`, which is the aggregate usage\.
+ The maximum payload size can't be more than 1 MB\. This includes input attribute keys \(for example, `UsageRecords`, `AllocatedUsageQuantity`, tags\)\.
**Note**  
To make sure that you aren't breaching the payload limit, create a sample request object with a maximum size based on the business requirement, convert the object into a JSON string, and obtain the size in bytes\. Make sure that a single API call won't breach the 1 MB limit\. For example\. if a request with 1 `UsageRecord` has a maximum size of 200 KB, don't send more than 5 `UsageRecords` as part of the request \(200KB \* 5 = 1MB\)\.

### Buyer experience<a name="saas-vendor-metered-tag-buyer"></a>

The following table shows an example of the buyer experience after a buyer activates the `AccountId` and `BusinessUnit` vendor tags\. 

In this example, the buyer can see allocated usage in their **Cost Usage Report**\. The vendor\-metered tags use the prefix `“aws:marketplace:isv”`\. Buyers can activate them in the Billing and Cost Management, under **Cost Allocation Tags**, **AWS\-generated cost allocation tags**\.

The first and last rows of the **Cost Usage Report** are relevant to what the Seller sends to the Metering Service \(as shown in the [Seller experience](container-metering-meterusage.md#container-vendor-metered-tag-seller) example\)\.


**Cost Usage Report \(Simplified\)**  

| ProductCode  | Buyer | UsageDimension | UsageQuantity | `aws:marketplace:isv:AccountId ` | `aws:marketplace:isv:BusinessUnit` | 
| --- | --- | --- | --- | --- | --- | 
| xyz | 111122223333 | Network: per \(GB\) inspected  | 70 | 2222 | Operations | 
| xyz | 111122223333 | Network: per \(GB\) inspected  | 30 | 3333 | Finance | 
| xyz | 111122223333 | Network: per \(GB\) inspected  | 20 | 4444 | IT | 
| xyz | 111122223333 | Network: per \(GB\) inspected  | 20 | 5555 | Marketing | 
| xyz | 111122223333 | Network: per \(GB\) inspected  | 30 | 1111 | Marketing | 

For a code example, see [`BatchMeterUsage` with usage allocation tagging code example \(Optional\)](saas-code-examples.md#saas-batchmeterusage-tagging)\.