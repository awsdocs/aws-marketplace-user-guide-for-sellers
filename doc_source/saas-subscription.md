# SaaS Subscriptions<a name="saas-subscription"></a>

 AWS Marketplace SaaS Subscriptions provides the AWS Marketplace Metering Service as a pricing and metering feature that AWS Marketplace sellers can use to directly charge for their software along one of four usage categories: users, data, bandwidth, or hosts\. 

 All software that uses the Metering Service must meet the following requirements: 
+  Your software must be launched from the AWS Marketplace through an Amazon Machine Image \(AMI\)\. 
+  If you have an existing product in the AWS Marketplace, you must submit a new AMI and create a new product listing to enable this feature\. 
+  All software must be provisioned with an AWS Indentity and Access Management \(IAM\) role\. The end customer will be required to add an IAM role to the Amazon Elastic Compute Cloud \(EC2\) instance the user is provisioning with the software\. Although the use of an IAM role is currently optional when deploying software through the AWS Marketplace, it is required when deploying AWS Marketplace Metering Service software\. 
+  Your software must be able to determine consumption in some way\. 

 Products that use the Metering Service must charge customers along a single usage category, but multiple dimensions of a single category can be defined\. Depending on the category selected, software can be priced by provisioned resources, concurrent resources, or accumulated resource consumption\. All charges are still incurred hourly by the customer\. All usage is calculated and billed monthly using the same mechanism as existing AWS Marketplace software\. 

 The AWS Marketplace Metering Service enables several new scenarios\. For example, if your software monitors hosts, you can charge for each host monitored\. You can have different prices based on the host size, and charge for the number of concurrent hosts monitored each hour\. Similarly, if your software allows many users across an organization to sign in, you can charge by the number of users\. Each hour, the customer would be charged for the total number of provisioned users\. 

## Metering Service Concepts<a name="metering-service-concepts"></a>

 The AWS Marketplace Metering Service enables software sellers to modify their software to send metering records to an endpoint to capture usage\. Sellers can select a usage category and multiple dimensions of that one category\. These dimensions are metered once per hour, aggregated, and charged against a price plan defined by the seller\. As a seller, the first thing you need to do is determine which dimension you want to use\. After the AMI is published, you will not be able to change it\. 
+  **Consumption** \- Any software product priced through the use of the Metering Service will charge for consumption in one of three ways: 
  +  Provisioned \- The software allows customers to configure a specific amount of resources for use \(for example, number of users or a fixed amount of bandwidth\)\. Each hour, customers pay for what they have provisioned\. 
  +  Concurrent \- The software allows any number of distinct hosts or users to connect to the software\. Each hour, customers pay based on the number of hosts or users who accessed the software\. 
  +  Accumulated \- The software allows customers to use any amount of data, either processed or stored\. Each hour, customers pay for the aggregated amount\. 
+  **Pricing** \- Any software product priced through the use of the Metering Service must specify either a single price or define dimensions, each with their own price\. 
  +  Single dimension \- This is the simplest pricing option\. Customers pay a single price per resource unit per hour, regardless of size or volume \(for example, $0\.014 per user per hour, or $0\.070 per host per hour\)\. 
  +  Multiple dimensions \- This pricing option is appropriate when the selected usage category varies along multiple axes\. For example, for host monitoring, a different price could be set depending on the size of the host\. Or for user\-based pricing, a different price could be set based on the type of user \(for example, admin, power user, and read\-only user\)\. 
+  **Metering** \- All usage is recorded as a metering event, once each hour\. Your software must be configured to send the appropriate dimension and usage amount to the AWS Marketplace Metering Service\. 

### Configure Your Application to Meter Usage<a name="configure-your-application-to-meter-usage"></a>

 You use the **BatchMeterUsage** operation on AWS Marketplace Metering Service to deliver metering records to AWS\. Keep the following in mind: 
+  We require sellers to use batching by using the **BatchMeterUsage** API\. 
+  We de\-duplicate metering requests on the hour\. 
  +  Requests are deduped per product\-customer\-hour\-dimension\. 
  +  You can always retry any request, but if you meter for a different quantity, the original quantity will be billed\. 
  +  If you send multiple requests for the same customer/dimension/hour, they will not accumulate usage\. 
  +  If you are sending daily reports on the number of users consumed, you must send all of these at the same hour, or you your customers will be charged twice\. 
+  Your metering records will contain a timestamp, which cannot be more than one hour in the past\. 
+  AWS Marketplace Metering Service is currently available in 14 AWS regions\. The *us\-east\-1* region is enabled by default for SaaS Metering products when you request your listing\. If you intend to use other regions, please inform the Seller Operations team \(aws\-marketplace\-seller\-ops@amazon\.com?subject=SaaS%20Metering%20Regions\) via email\. For information about the BatchMeterUsage API, see the [AWS Marketplace documentation](https://aws.amazon.com/documentation/marketplace/)\. 

#### Authentication and Authorization<a name="authentication-and-authorization"></a>

 Your vendor profile on AWS Marketplace is tied to one AWS account\. For both the **BatchMeterUsage** and the **ResolveCustomer** operations, you will authenticate using AWS credentials that belong to your seller AWS account\. Like most AWS services, AWS Marketplace Metering Service uses standard [AWS Signature Version 4](http://docs.aws.amazon.com/AmazonS3/latest/API/sig-v4-authenticating-requests.html) to authenticate requests\. You will not be able to invoke **BatchMeterUsage** or **ResolveCustomer** using credentials other than those that belong to your seller AWS account\. 

 You’ll use using AWS Identity and Access Management to set up AWS credentials\. You can make calls to AWS Marketplace Metering Service using an IAM user or role\. 

 The following is an example IAM policy to use when calling **BatchMeterUsage** or **ResolveCustomer**: 

### Metering Usage \(SaaS Subscriptions\)<a name="metering-usage-saas-subscriptions"></a>

 In the SaaS Subscriptions model, you will need to report usage to AWS on an hourly basis for all your customers, in batches of up to 25 at a time\. The dimensions on which you meter are defined when you list your product on AWS Marketplace\. 

 Figure : Metering usage 

#### Example: Log Analysis<a name="example-log-analysis"></a>

 As your application receives logs from a customer, you accumulate usage in a usage log unique to each customer\. On the tenth minute of every hour, a cron job reads this usage for each customer for the previous hour\. The job builds a batch report and uses the BatchMeterUsage API to send it to AWS\. 

### Testing Your SaaS Application<a name="testing-your-saas-application"></a>

 During the onboarding process, you’ll create a second AWS account ID for testing your product\. You can sign in to this test account to view your SaaS listing on AWS Marketplace and, on an ongoing basis, use it to verify the metering and billing process\. You will also be able to use seller reports provided through the AWS Marketplace Seller Portal to confirm that metered usage corresponds with the account identifiers of your customers\. Any charges incurred by this test account when using your product will be voided\. 

 **Note**: If you create a SaaS product for use in the GovCloud region, that SaaS product must be tested and meet the requirements for the GovCloud region\. 

#### Test New Customer Registration<a name="test-new-customer-registration"></a>

 Verify the customer registration process through the **Accept Terms and Register** step: 
+  Create a new account in your application\. 
+  Verify your redirect page is functional\. 
+  Verify your website resolves the registration token for a customer identifier\. 
+  Verify your website allows a new account to be created\. 
+  Verify the product code matches the one assigned to your application\. 
+  Verify the customer identifier is added to your accounts database\. 
+  Verify you receive a subscription notification\. 

#### Optional: Test Existing Customer Registration<a name="optional-test-existing-customer-registration"></a>

 You can build your landing page so that existing accounts can be changed to use AWS for billing\. You should repeat the process above with an existing account that does not have AWS billing information attached\. 

#### Verify Records Using AWS CloudTrail<a name="verify-records-using-aws-cloudtrail"></a>

 BatchMeterUsage API calls are captured by AWS CloudTrail\. You can use CloudTrail to verify the SaaS metering records you sent are accurate by searching for records with the event Name of BatchMeterUsage\. You can also use CloudTrail to audit records over time\. 

 For more information, see [AWS Marketplace Metering Service](http://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) and the [AWS CloudTrail](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-supported-services.html#additional-software-and-services)\., 

#### Test Duplicate Accounts<a name="test-duplicate-accounts"></a>

 Use your test AWS account to create a new account in your system, and then repeat the process\. 
+  Verify that you are unable to create a new account in your SaaS application because another account with that customer identifier already exists\. 

#### Test Metering<a name="test-metering"></a>

 Sign in to a test account in your SaaS application and begin consuming resources\. 
+  Verify that your system is emitting metering records\. Confirm with your AWS representative that these records have been received\. 

#### Test Unsubscribe<a name="test-unsubscribe"></a>

 Unsubscribe your test account through the **Your Software** page on AWS Marketplace\. Verify: 
+  Your application received an unsubscribe\-pending notification\. 
+  Your application responds as expected in an unsubscribe scenario\. For example, your application might complete existing work, but prevent new work from being created for your test account\. 
+  Your application received an unsubscribe\-success notification\. 
+  Your application no longer sends metering records after receiving the unsubscribe\-success notification\. 