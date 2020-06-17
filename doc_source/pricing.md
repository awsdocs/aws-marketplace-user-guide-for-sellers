# Product pricing<a name="pricing"></a>

The following is general pricing information about products in AWS Marketplace\. All pricing is based on US dollars \(USD\)\. For information on refunds, see [Refunds](refunds.md)\.
+ For Paid products, AWS Marketplace collects software charges from the customer\. 
+ There is no service fee for Bring Your Own License \(BYOL\) products on AWS Marketplace\. 
+ To deliver on our customer promise of selection, we require that all BYOL products also have a paid option\. This is so that customers who don’t have existing licenses have the option to purchase and use the products\. 
  + For BYOL products, we realize that the online purchase of software is a departure from how some companies do business\. In light of this, for the first 90 days after launch we will relax the requirement that this software is accompanied by a version available for purchase on AWS Marketplace\. During this time, the AWS Marketplace account management teams will work with you to address challenges and to determine if and how the software can be made available for purchase on AWS Marketplace\. 
+  There is no service fee for Free or Open Source Software that is made available to customers without charge\. 

## AWS charges versus software charges<a name="aws-charges-vs-software-charges"></a>
+ All AMI\-based products will incur associated AWS infrastructure charges depending on the services and infrastructure used\. These rates and fees are defined and controlled by AWS, and can vary between regions\. For more information, see [Amazon EC2 Pricing](https://aws.amazon.com/ec2/pricing/)\.
+ For Paid products, the seller defines the charges for using the software\. 

These two types of prices are displayed separately on the AWS Marketplace detail pages to help customers understand the potential cost of using the products\. 

### Free trial<a name="free-trial"></a>

 Hourly products are eligible for the optional Free Trial program, where a customer can subscribe to the product and use a single instance for up to 31 days without paying software charges on the product\. Applicable AWS infrastructure charges still apply\. Simply define the duration of the trial period \(5 to 31 days\) and notify the [AWS Marketplace Managed Catalog Operations \(MCO\)](https://aws.amazon.com/marketplace/management/contact-us/) team\.

When customers subscribe to a Free Trial product, they receive a welcome email that includes the term of the Free Trial, a calculated expiration date, and details on unsubscribing\. A reminder email is sent three days before the expiration date\.

If you offer a Free Trial product in AWS Marketplace, you agree to the specific refund policies described under **Refund Policy**\.

### Changing prices<a name="changing-prices"></a>

You can update prices and metadata through the AWS Marketplace Management Portal\. 

**To change prices**

1. Sign in to the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/)\.

1. In the **Products** tab, you will find a list of current products that you created\. In the table for your current products, choose the **Action** column to edit your product\. 

### Changing pricing models<a name="changing-pricing-models"></a>

 Changes to pricing models must be reviewed and approved by AWS Marketplace to ensure a positive customer experience and reduced risk to all parties\. Discuss the pricing model changes you want to make by contacting the [AWS Marketplace Managed Catalog Operations \(MCO\)](https://aws.amazon.com/marketplace/management/contact-us/) team\. All requests for pricing model changes can take 30\-90 days to process and review\. 

## Annual pricing<a name="annual-pricing"></a>

An annual pricing model enables you to offer products to customers who can purchase a 12\-month subscription\. The subscription pricing can provide up to 40% savings versus running the same product hourly for extended periods\. The customer is invoiced for the full amount of the contract at the time of subscription\. For more information about how annual subscriptions are presented to customers, see [AMI Subscriptions](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-ami-subscriptions.html)\. 

See the following considerations when working with an annual subscriptions\. 
+ Annual pricing is defined per instance type\. It can be the same for all Amazon EC2 instance types or different for each instance type\. 
+ All Annual instance types must also have an Hourly instance type defined\. AWS Marketplace doesn't offer Annual\-only pricing or Hourly without Annual on the same product\. For any product offering Annual pricing, Hourly pricing also needs to be specified\. 
+ A $0 Annual price is allowed on a specific instance type, if the Hourly price is also $0 and there are other non\-$0 Annual instance types defined\. 
+ At the end of the annual subscription period, the customer will start being charged at the hourly price\. 
+  If a customer buys X Annual subscriptions but is running Y software on Y instances, then the customer will be charged at Hourly software price for \(Y\-X\) instances which are not covered by Annual subscriptions\. As such, an Hourly rate must be included for all Annual pricing instance types\. 
+ Using seller private offers, you can offer a multi\-year \(up to 3 years\) or custom duration AMI with upfront payment, or flexible payment schedule\. For more information about multi\-year and custom duration contracts, see [Private offers](private-offers-overview.md) and [Flexible payment scheduler](flexible-payment-scheduler.md)\.

If you offer an Annual product in AWS Marketplace, you agree to the specific refund policies for Annual products, located in the **File Uploader** documents section in the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour)\. 

## Usage pricing<a name="usage-pricing"></a>

 The AWS Marketplace Metering Service enables you to define additional dimensions you want to charge your customers for the value your software provides\. As a seller, you can choose one of the usage categories from the following:

1. Users

1. Hosts

1. Bandwidth

1. Data

You can also define up to 24 dimensions for the product\. All charges must be measured and reported every hour from the software deployed in the customer’s account\. All usage is calculated monthly and billed monthly using the same mechanism as existing AWS Marketplace software\. 

Using the AWS Marketplace Metering Service, you can handle several new pricing scenarios\. For example, if your software monitors hosts, you can charge for each host monitored and set different pricing based on the host size\. If your software allows multiple users across an organization, you can charge by user\. Each hour, the customer would be charged for the total number of provisioned users\. 

**Note**  
In the product load form, relevant columns are named as Flexible Consumption Pricing \(FCP\)\. 

For AWS Marketplace Metering Service products, note the following: 
+ If your software is already on AWS Marketplace, you will need to create a product to enable an alternate usage dimension\. That is, currently, we are unable to convert a standard product to use the AWS Marketplace Metering Service\. After the new product is published, you can remove the old product or keep both on site\. 
+ The AWS Marketplace Metering Service requires that your software reports usage every hour, recording the customer usage for the hour\. If there is a failure in the transmission or receipt of metering service records, AWS will be unable to bill for such usage\. You are responsible for ensuring the successful receipt of metering records\. 
+ At this time, products that use the AWS Marketplace Metering Service don't support 1\-Click\. Buyers are required to launch your software with an IAM role with specific permissions and have an Internet Gateway\. 
+ Free Trial and Annual Pricing are not compatible with the AWS Marketplace Metering Service at this time\. 
+ Changing dimension \(user, hosts, bandwidth, and data\) or dimension name is not supported\. You will need to create a new product\. 

## Private offers<a name="private-offers"></a>

The AWS Marketplace Seller Private Offer program allows AWS Marketplace sellers to negotiate custom pricing and end user license agreements with individual AWS Marketplace customers \(buyers\)\. For more information, see [Private offers](private-offers-overview.md)\.

## SaaS subscriptions pricing<a name="saas-subscriptions-pricing"></a>

 For SaaS Subscriptions, AWS Marketplace bills your customers based on the metering records received by us\. All charges must be measured and reported every hour from the software deployed in the customer's account\. All usage is then calculated monthly and billed monthly using the same mechanism as AMI based AWS Marketplace offerings\. AWS’ ability to bill customers for usage of your product is dependent upon receiving metering records from you\. You are responsible for ensuring that your product’s metering records are successfully transmitted and received\. 

## SaaS contracts pricing<a name="saas-contracts-pricing"></a>

For SaaS Contracts, the customer initiates a purchase of your software and enters into an agreement with you\. Under the agreement, the customer is entitled to a specified quantity of use of your SaaS product\. AWS Marketplace communicates these entitlements to your SaaS application\. This is done through the AWS Marketplace Entitlement Service\. When using SaaS Contracts, your application never sends metering records\. Instead, it verifies entitlement by calling the AWS Marketplace Entitlement Service\. You define the usage categories, dimensions, and the length of the contract\. 

## AMI pricing models<a name="ami-pricing-models"></a>

AWS Marketplace has multiple pricing models for AMI products\. With seller private offers, there are options available for multi\-year and custom duration contracts\. For more information about multi\-year and custom duration contracts, see [Private offers](private-offers-overview.md) and [Flexible payment scheduler](flexible-payment-scheduler.md)\. The following table provides general information about pricing models\.

**Note**  
 You must be able to provide a W\-9 tax form \(for U\.S\. based entities\) or a W\-8 form \(for EU\- based entities\) as described in [Seller registration process](seller-registration-process.md)\. 


|  Pricing model  |  Description  | 
| --- | --- | 
| Bring Your Own License \(BYOL\)  | AWS Marketplace does not charge customers for usage of the software, but customers must supply a license key to activate the product\. This key is purchased outside of AWS Marketplace\. The entitlement/ licensing enforcement, as well as all pricing and billing are handled by you\.  | 
|  Free  | Customers are allowed to run as many instances as Amazon EC2 supports with no additional software charges incurred\.  | 
|  Hourly  |  **Hourly** – Software is charged by the hour\. Each instance type can be priced differently \(but is not required to be\) and usage is rounded up to the nearest whole hour\.  **Hourly with Free Trial** – Customers are limited to running exactly one instance of the software without incurring a charge\. You define the duration, between 5 and 30 days\. The free trial applies to the most expensive instance type that is running, and any concurrent usage outside the 1 instance is billed at the hourly rate\. NOTE\- This is a different model than the AWS Free Tier for Amazon EC2 usage whereby customers are given 750 hours of free usage each month\.  **Hourly with Monthly** – Both hourly and monthly charges are applied independently; the monthly fee is charged every month regardless of usage, the hourly fee is applied based on hourly usage only\.  **Hourly with Annual** – Customers have the option to purchase a year’s worth of usage upfront for one Amazon EC2 instance of one instance type\. You set the pricing for each instance type and can offer net savings over the hourly price\. Any customer usage above the number of annual subscriptions purchased is billed at the hourly rate you set for that instance type\.  **Hourly with Multi\-Annual and Custom Duration** – This type offer is only available through seller private offers\. Using seller private offers, you specify a custom contract duration, up to 3 years\. You can specify upfront payment, or include a flexible payment schedule\. You set the pricing for each instance type\. If there is a flexible payment schedule in the offer, you also set the invoice dates, payment amounts, and number of instances for each instance type included in the offer\. For an active seller private offer with a flexible payment schedule, after the customer launches the specified number of instances, any additional instances launched are charged at the hourly rate specified in the seller private offer\. For more information about multi\-year and custom duration contracts, see [Private offers](private-offers-overview.md) and [Flexible payment scheduler](flexible-payment-scheduler.md)\. **Hourly with Free Trial and Annual** – This is identical to the Hourly model with an Annual option, except it includes a Free Trial allowing a customer to run 1 instance of any instance type for free for a set number of days that you determine\. Annual subscriptions can be purchased at any time, and they are combined with the Free Trial subscription\.   | 
|  Monthly  |  **Monthly** – Software is paid for on a fixed monthly basis, regardless of the number of instances the customer runs\. Monthly Charges are pro\-rated at sign\-up and upon cancellation\. Example: A customer who subscribes for 1 day of the month will be charged for 1/30th of the month\.  **Monthly with Hourly** – Both Hourly and Monthly charges are applied independently\. The monthly fee is charged every month regardless of usage and the hourly fee is applied based on hourly usage only\.   Free Trial and Annual pricing cannot be combined with Monthly pricing\.   | 
|  Annual  |  **Annual with Hourly** – Same as the hourly with annual pricing model\. Customers have the option to purchase a year’s worth of usage upfront for one Amazon EC2 instance of one instance type\. You set the pricing for each instance type and can offer net savings over the hourly price, but offering savings is not required\. Any customer usage above the number of annual subscriptions purchased is billed at the hourly rate you set for that instance type\.  **Multi\-Annual and Custom Duration with Hourly** – This is only available through [Private offers](private-offers-overview.md) \. Using seller private offers, you can specify a custom duration contract of up to three years\. You can require upfront payment, or can offer a flexible payment schedule to the customer\. You set the pricing for each instance type for the duration of the contract, and the hourly pricing for additional instances launched\. If you offer a flexible payment schedule, you also set the invoice dates, payment amounts, and number of instances for each instance type included in the offer\. For an active private offer with a flexible payment schedule, after the specified number of instances have been launched, any additional instances the customer launches are charged at the hourly rate specified in the private offer\. For more information about multi\-year and custom duration contracts, see [Private offers](private-offers-overview.md) and [Flexible payment scheduler](flexible-payment-scheduler.md)\.  | 
|  Usage  |  **Usage** – Software is directly charged for the value you provide along with one of four usage categories: users, data, bandwidth, or hosts\. You can define up to 24 dimensions for the product\. All charges are still incurred hourly by the customer\. All usage is calculated monthly and billed monthly using the same mechanism as existing AWS Marketplace software\. Usage pricing is also referred to as AWS Marketplace Metering Service   Free trial and Annual pricing cannot be combined with Usage pricing\.   | 

## Pricing your software with SaaS<a name="pricing-your-software-with-saas"></a>

 To set prices, you first define pricing dimensions that represent the units of value in your software and then assign a price to each dimension\. For example, dimensions can be protected hosts, users, or storage volumes\. You can define up to 24 dimensions\. Next you will also select a category for those dimensions which can be one of our preset categories \(bandwidth, data, hosts, requests, tiers, users\)\. If none of the presets fit your use case, you can choose the generic 'units' category and describe the units in the dimension description\. 

### Example: Provisioned bandwidth with nonlinear pricing<a name="example-provisioned-bandwidth-with-non-linear-pricing"></a>

 Imagine you offer network appliance software\. You choose to bill by provisioned bandwidth\. For your usage category, select bandwidth\. In addition to charging by bandwidth, you want to charge a different price as buyers scale up\. You can define multiple dimensions within the bandwidth category\. You can define a distinct price for 25 Mbps, 100 Mbps, and 1 Gbps\. 

### Example: Concurrent hosts with multiple dimensions<a name="example-concurrent-hosts-with-multiple-dimensions"></a>

 Imagine you offer software that monitors other Amazon EC2 instances\. You choose to bill by the number of hosts that are being monitored\. For your usage category, select host\. In addition to charging by host, you want to charge for the extra value for monitoring larger hosts\. You can use multiple dimensions within the host category\. You can define a distinct price for micro, small, medium, large, x\-large, 2XL, 4XL, 8XL instances\. Your software is responsible for mapping each particular host to one of your defined dimensions\. Your software is responsible for sending a separate metering record for each dimension of your usage category if applicable\. 

### Listing your SaaS product on AWS Marketplace<a name="listing-your-saas-product-on-aws-marketplace"></a>

 To take advantage of the Metering Service, you must create a new product\. If your product is already on AWS Marketplace, you will need to decide whether the new AWS Marketplace Metering Service product will be made available in addition to your current one, or if it will replace it as the only version available to new users\. If you choose replacement, the existing product will be removed from the AWS Marketplace so that it is no longer available for new buyers\. Existing customers will continue to have access to their old product and instances, but they can migrate to the new product at their convenience\. The new product must meter usage to the AWS Marketplace Metering Service\. 

 After you have your AMI, follow the standard process to share and scan your AMI using the self\-service tool\. In addition, using the template available on the management portal, fill out the product load form and upload it to start the ingestion process\. 

 The following definitions will help you fill out the fields of the product load form for the AWS Marketplace Metering Service\. On the product load form, these fields are labeled as Flexible Consumption Pricing \(FCP\) to differentiate them from hourly and monthly priced products\. 
+ **Title** – If you already have a product, and you are adding the same product with the AWS Marketplace Metering Service, include the FCP category/dimension in parenthesis to differentiate the two \(for example, “PRODUCT TITLE \(Data\)”\)\. 
+ **Pricing Model** – From the dropdown list, choose **Usage**\.
+ **FCP Category** – The category in which customers will be charged for paid products with a **Usage** pricing component\. From the dropdown menu, choose **Users**, **Hosts**, **Data**, or **Bandwidth**\.
+ **FCP Unit** – The unit of measurement on which customers will be charged for paid products with a **Usage** pricing component\. Options will appear in the dropdown menu based on the FCP category that you chose\. 

  The following table lists the valid units for each category\.    
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/pricing.html)
+ **FCP Dimension Name** – The name used when sending metering records by calling MeterUsage API\. It is visible in billing reports, but because it is not external\-facing, the name does not need to be user\-friendly\. The name can be no more than 15 characters and can only include alphanumeric and underscore characters\. After you set the name, you will not be able to change it\. Changing the name requires a new AMI\.
+ **FCP Dimension Description** – The customer\-facing statement that describes the dimension for the product\. The description \(for example, Administrators per hour, Per Mbps bandwidth provisioned\) can be no more than 70 characters and should be user\-friendly\. After the product is published, you will not be able to change this description\.
+ **FCP Rate** – The software charge per unit for this product\. This field supports 3 decimal places\. 

**Note**  
 You don't need to fill out hourly and annual pricing fields\. 
 Free trial and annual pricing are not compatible\. 
 Products that use the clusters and AWS Resources feature can't the AWS Marketplace Metering Service\. 
 Price, instance type, or region change will follow the regular process as other AWS Marketplace products\. 
 Products with the AWS Marketplace Metering Service cannot be converted to other pricing models such as hourly, monthly, or BYOL\. 
 We recommend adding IAM policy information in your usage instructions or document\. 

 If you have questions, contact the [AWS Marketplace Managed Catalog Operations \(MCO\)](https://aws.amazon.com/marketplace/management/contact-us/)

### Modifying your SaaS software to use the Metering Service<a name="modifying-your-saas-software-to-use-the-metering-service"></a>

 You will need to modify your software to record customer usage, send hourly usage reports to the Metering Service, and handle new failure modes\. The software operates independently of pricing, but the software will need to know about the usage category, how it is consumed, and any dimensions\. 

#### Measuring consumption<a name="measuring-consumption"></a>

 Your software must determine how much of the selected usage category and which dimensions the customer has consumed\. This value will be sent, once each hour, to the AWS Marketplace Metering Service\. In all cases, it is assumed that your software has the ability to measure, record, and read consumption of resources for the purpose of sending it on an hourly basis to the Metering Service\. 

 For provisioned consumption, this will typically be read from the software configuration as a sampled value, but might also be a maximum configured value, recorded each hour\. For concurrent consumption, this might be either a periodic sample or a maximum value recorded each hour\. For accumulated consumption, this will be a value that is accumulated each hour\. 

 For pricing on multiple dimensions, multiple values must be measured and sent to the Metering Service, one per dimension\. This requires your software to be programmed or configured with the known set of dimensions when providing the product AMI\. The set of dimensions cannot change after a product has been created\. 

 For each pricing scenario, this table describes recommended ways for measuring consumption each hour: 


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

1. A thread within your software\. 

1. A daemon process that starts up with the instance or software\. 

1. A cron job that is configured during application startup\. 

Your software must call the AWS Marketplace Metering Service using the IAM role configured on the customer’s instance and specify the consumption dimension and amount\. 

 Your software can use the AWS SDK to call the AWS Marketplace Metering Service\. The following is a typical implementation: 

1. Use the instance profile to create a service client\. This requires the role configured for the Amazon EC2 instance\. The role credentials are refreshed by the SDK automatically\.   
**Example**  

   ```
   AmazonMeteringService meteringClient = new AmazonMeteringService(new InstanceProfileCredentialsProvider());
   ```

1. Each hour, read your software configuration and state to determine consumption values for that hour\. This might include collecting a value\-per\-dimension\. 

1. Call the `meterUsage` action on the SDK client with the following parameters \(call additionally for each dimension that has usage\): 
   +  `timestamp` – Timestamp of the hour being recorded \(use UTC\)\. 
   +  `productCode` – The product code assigned to the software\. 
   +  `dimension` – The dimensions assigned to the software\.
   +  `quantity` – The consumption value for the hour\. 

In addition, your software must call an in\-region AWS Marketplace Metering Service endpoint\. Your product must have a correct regional endpoint setup, so US East \(N\. Virginia\) sends records to US East \(N\. Virginia\) endpoint, and US West \(Oregon\) sends records to US West \(Oregon\) endpoint\. Making in\-region calls provides buyers with a more stable experience and prevents situations in which an unrelated region’s availability could impact software running in another region\. 

 When you send metering records to the service, you must connect to the AWS Marketplace Metering Service in your region\. Use the `getCurrentRegion` action to determine the region in which the Amazon EC2 instance is running, and then pass this region information to the `MeteringServiceClient` constructor\. If you don't specify a region in the SDK constructor, it defaults to the us\-east\-1 region\. If your application attempts to make cross\-region calls to the service, it will be rejected\. 

### Failure handling<a name="important-information-about-failure-handling"></a>

 Your product must send metering records to the service, a public internet endpoint, so that usage can be captured and billed\. Because it's possible for a customer to modify network settings in a way that prevents your metering records from being delivered, your product should account for this by choosing a failure mode\.

 Typically, software can fail open \(provide a warning message but maintain full functionality\) or fail closed \(disable all functionality in the application until a connection has been reestablished\)\. You can choose to fail open, closed, or something specific to your application\. We recommend that you refrain from failing closed after less than two hours of metering failures\.

 As an example of failing partially open, you could continue to allow access to the software but not allow the buyer to modify the software settings\. Or, a buyer could still access the software, but would not be able to create additional users\. Your software is responsible for defining and enforcing this failure mode\. Your software’s failure mode must be included when your AMI is submitted, and it can't be changed later\. 

## Annual products<a name="annual-products"></a>

These guidelines apply to all sellers who are offering a product on AWS Marketplace with annual pricing\. 

### Price change<a name="price-change"></a>

You can change annual prices \(the $ value, for example $1000/year to $1200/year\) whenever desired but with 90 day notice to existing customers of annual pricing\. The new price will apply to new subscriptions but will have no impact on existing subscriptions\. Price changes will be effective for auto\-renewals only if the price was changed at least 90 days before the auto\-renewal date\. The customer will receive an email prior to auto\-renewal that includes the new price\. 

### Refund / cancellation / upgrade / downgrade<a name="refund-cancellation-upgrade-downgrade"></a>

For uniform and great customer experience, AWS requires sellers to implement the following cancellation/change windows: 


| Applicable policy  | Time period or window  | Who can authorize it  | 
| --- | --- | --- | 
| Full refund cancellation \(cancel with 100% refund\) | Within 48 hours of purchase  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/pricing.html)  | 
| Pro\-rata refund cancellation \(cancel with pro\-rata refund\) | Within 14 days of purchase  | Seller only  | 
| Downgrade subscription \(replace existing subscriptions with less expensive subscription\)  | Within 30 days of purchase  | Seller only  | 
| Upgrade subscription \(replace existing subscriptions with more expensive or same priced subscription\)  | Any time during 12 months  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/pricing.html)  | 
| Full refund cancellation in case of auto\-renewal  | Within 14 days of purchase  | AWS customer support or the seller  | 

**Note**  
You should not include windows length and other details in product details/description\. 
Upgrade or downgrade is a 2\-step process for customer: buy new subscriptions and request cancellation of old subscription with a refund\. 
In some cases AWS might issue refunds on your behalf\. No action on your part is required to process those refunds\. 

### End user license agreement<a name="end-user-license-agreement"></a>

AWS customer’s usage of software for 12 months under annual subscription is covered by the EULA you have provided on your product’s details page on AWS Marketplace\. 