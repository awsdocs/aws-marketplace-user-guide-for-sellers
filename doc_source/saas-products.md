# Software\-as\-a\-Service\-Based Products<a name="saas-products"></a>

 As a software as a service \(SaaS\) seller, you deploy software hosted on AWS infrastructure and are responsible for granting AWS Marketplace customers access to the software\. There are no AMIs to configure and your customers do not have to run your software on their own EC2 instances\. With SaaS, customers subscribe to products through AWS Marketplace, but access the product in your environment\. AWS Marketplace offers 2 different pricing models for SaaS listings: 
+  SaaS Subscriptions 
+  SaaS Contracts 

 With **SaaS Subscriptions**, you use the AWS Marketplace Metering Service to report metering usage to AWS\. The usage data is used to bill customers for SaaS application use\. All charges must be measured and reported every hour from the software deployed in the customer's account\. 

 With **SaaS Contracts**, you use the AWS Marketplace Contract Service to bill customers in advance for the use of your software\. Customers pay upfront for a time\-bound entitlement to use your SaaS software\. Under SaaS Contracts, the customer is entitled to a specified quantity and duration of use of the SaaS product\. 

 With SaaS Subscriptions and SaaS Contracts, customers subscribe to your SaaS listings through AWS Marketplace\. After a customer finds and subscribes to your SaaS product on AWS Marketplace, AWS Marketplace passes a billing identifier to your website\. Customer account creation, resource provisioning and account management is done through your website or APIs, but access the product in your AWS environment, or through a VPC endpoint service connection you create\. 

 For both SaaS Subscriptions and SaaS Contracts listings, you can use AWS PrivateLink technology, to configure your service as an Amazon Virtual Private Cloud \(VPC\) endpoint service and your customers can create a VPC endpoint and access your software across the Amazon network\. Alternatively, you can provide access to your software product through your website, with customers creating a connection across the Internet\. 

 There are two additional guides available for SaaS products: 
+  [AWS Marketplace SaaS Seller Integration Guide](https://s3.amazonaws.com/awsmp-loadforms/SaaS%20Seller%20Integration%20Guide.pdf) 
+  [AWS Marketplace SaaS Quick Start](https://s3.amazonaws.com/awsmp-loadforms/aws-marketplace-saas-quick-start.pdf) 

## Requirements for SaaS Subscriptions and SaaS Contracts listings<a name="requirements-for-saas-subscriptions-and-saas-contracts-listings"></a>

### SaaS Subscriptions and SaaS Contracts Comparison<a name="saas-subscriptions-and-saas-contracts-comparison"></a>

 As a SaaS application owner offering through AWS Marketplace, you must pick one of two options available for listing and billing your software: 
+  SaaS Subscriptions \(also known as: pay as you go, consumption monetization model\) 
+  SaaS Contracts \(also known as: entitlement monetization model\) 

 **With SaaS Subscriptions**, you use the AWS Marketplace Metering Service to report metering usage to AWS which will be used to bill customers for SaaS application use\. 

 AWS Marketplace Metering Service provides a *consumption* monetization model in which customers are charged only for the number of resources they use in your application\. The consumption model is similar to that for most AWS services\. Customers pay as they go\. 

 **With SaaS Contracts model**, you use the AWS Marketplace Contract Service to bill customers in advance for the use of your software\. AWS Marketplace Contract Service provides an *entitlement* monetization model in which customers are invoiced in advance for a certain amount of usage of your software, and AWS communicates this *entitlement* to your application\. For example, you might sell your customer a certain amount of storage per month for a year, or a certain amount of end\-user licenses for 2 years\. The customer makes a payment as part of their standard billing cycle\. 

 Table 1: Comparision chart for SaaS Subscription and SaaS Contract models\. 


|   |  SaaS Subscriptions  |  SaaS Contracts  | 
| --- | --- | --- | 
|  Also called  |  Metering, pay\-as\-you\-go, consumption\-based monetization  |  provisioning\-based monetization  | 
|  How customers use the application  |  Similar to using an AWS service\. Customers subscribe to the listing, get provisioned in seller’s environment, and are charged based on usage\.  |  Similar to a classic SaaS application\. Customers sign up for capacity up front, and then use the application within the limits of that capacity and duration\.  | 
|   |   |   | 
|  Time granularity of usage  |  Hourly  |  1\-, 12\-, 24\-, 36\-months options  | 
|  How sellers communicate with AWS  |  Sellers send AWS metering records: “Customer X used Y for Z hour”  |  AWS stores duration, dimension and \# of units purchased in dimension, payment, and access details and provides entitlement records to sellers: “Customer X is allowed to use Y dimension until Z date”  | 
|  When customers are charged  |  Monthly, within the normal AWS billing cycle\.  |  When the customer purchases an initial contract, upgrades to using more capacity or their capacity is auto\-renewed\.  | 
|  Traditional way to realize discounts  |  Tiered usage plans; pay less per unit for increased usage\.  |  Discounts are incorporated into prices for longer\-term commitments or bundles of higher quantities\.  | 
|  Example application  |   [https://aws\.amazon\.com/marketplace/pp/B074CQY6KB](https://aws.amazon.com/marketplace/pp/B074CQY6KB)   [https://aws\.amazon\.com/marketplace/pp/B075MWZVBM](https://aws.amazon.com/marketplace/pp/B075MWZVBM)   [https://aws\.amazon\.com/marketplace/pp/B0722D4QRN](https://aws.amazon.com/marketplace/pp/B0722D4QRN)   |   [https://aws\.amazon\.com/marketplace/pp/B075CRJXNK](https://aws.amazon.com/marketplace/pp/B075CRJXNK)   [https://aws\.amazon\.com/marketplace/pp/B06XXM7JJT](https://aws.amazon.com/marketplace/pp/B06XXM7JJT)   [https://aws\.amazon\.com/marketplace/pp/B076J22YD8](https://aws.amazon.com/marketplace/pp/B076J22YD8)   | 

### SaaS Subscriptions Pricing<a name="saas-subscriptions-pricing"></a>

 For SaaS Subscriptions, AWS Marketplace will bill your customers based on the metering records received by us\. Products utilizing SaaS Subscriptions must qualify under one of our seven pricing categories: Users, Hosts, Data, Bandwidth, Requests, Tiers and Units\. You will then select the unit of measure for the category selected\. You define at least one dimension to offer up to 24 variants for the single listing\. All charges must be measured and reported every hour from the software deployed in the customer's account\. All usage is then calculated and billed monthly using the same mechanism as AMI based AWS Marketplace offerings\. **AWS’ ability to bill customers for usage of your product is dependent upon receiving metering records from you\. You are responsible for ensuring that your product’s metering records are successfully transmitted and received\.** 

### SaaS Contracts Pricing<a name="saas-contracts-pricing"></a>

 Products utilizing SaaS Subscriptions must qualify under one of our *five* six pricing categories: Users, Hosts, Data, Bandwidth, Requests, and Units\. You will then select the unit of measure for the category selected\. You define at least one dimension to offer up to 24 variants for the single listing, as well as the lenth options of the contract\. Under the agreement, the customer is entitled to a specified quantity of use of your SaaS product\. AWS Marketplace communicates these entitlements to your SaaS application through the AWS Marketplace Entitlement Service\. When using SaaS Contracts, your application never sends metering records\. Instead, it verifies entitlement by calling the AWS Marketplace Entitlement Service\. You are responsible for calling the AWS Marketplace Entitlement Service to determine if a customer is operating within their paid entitlement\. 

#### Modeling Contracts Pricing<a name="modeling-contracts-pricing"></a>
+  Pick a category – Only 1 category per product\. 
  +  Units is intentionally ambiguous and can act as a catch\-all if the ISV does not bill by any other category available\. 
+  Determine dimensions per product \(up to 24 supported\)\. 
  +  Ex: Category = Users\. Dimensions = admin, power, read\-only, etc\. 
+  Determine contract duration option for the product\. Has to be the same across all dimensions\. 
  +  Month, 1 year, 2 year, 3 year available\. Can pick any combination\. 
+  Determine per unit pricing per dimension for the lowest contract duration term \(monthly\)\. 
  +  Ex: Admin user = $4/month, Power User = $3/month, Read Only = $1/month\. 
+  If offering longer terms, multiply the monthly price by 12, 24, or 36\. 
+  For Sellers who would like to offer a tier/package pricing, we also support radio buttons\. This means the customer can only purchase one tier, instead of multiple\. For example, a customer would select 1 tier of up to 100 GB, and pay a set amount for this contract\. 
+  We do not support validation rules when buying a contract: no minimum, maximum\. 
+  At this time AWS Marketplace does not support charging overage fees, where the Seller can send metering records for units that a customer goes over their contract\. 

## SaaS Subscriptions<a name="saas-subscriptions"></a>

 ***Subscription Flow* ** 

 With SaaS Subscriptions and SaaS Contracts, customers subscribe to products through AWS Marketplace, but access the product in the seller’s environment\. When a customer subscribes to a product, AWS Marketplace passes a billing identifier to the seller\. All of the remaining steps \(customer account creation, resource provisioning, and account management\) occur on the seller’s website or with the seller’s APIs\. 

 Figure : AWS SaaS billing customer flow\. 

![\[Software as a service billing flow for customers\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-image-1.png)

 **Metering** 

 Your application will report usage information to AWS, and customers will pay for their use of your SaaS application through their AWS bill based on the metering records you provide\. This is an extension of the [AWS Marketplace Metering Service](https://aws.amazon.com/documentation/marketplace/) \(MMS\)\. When your application **meters usage** for a customer, your application is providing AWS with a quantity of usage accrued for a given hour\. Your application meters for real units of value, such as gigabytes transferred or hosts scanned in a given hour\. AWS uses this information to calculate a customer’s bill based on rates that you provide when you create a SaaS listing\. Collected transaction proceeds are disbursed to you as an AWS Marketplace seller\. It is your responsibility to confirm that your metering is being delivered to AWS Marketplace in a manner that permits AWS to correctly bill your customers for use of your product\. 

### Customer Experience<a name="customer-experience"></a>

 Under subscribe to products directly on the AWS Marketplace website based on the consumption price displayed on the detail page and recorded in the end user licensing agreement\. After subscribing to the product, the customer is directed to the seller’s website to register their account and configure the product\. 

#### Registering an Account in the SaaS Application<a name="registering-an-account-in-the-saas-application"></a>

 After the customer has subscribed in AWS Marketplace, the customer will register an account in your SaaS application on a website that you host\. The registration landing page accepts a token from AWS Marketplace with the customer’s identifier for billing\. 

#### Using the SaaS Application<a name="using-the-saas-application"></a>

 Customers access your SaaS application directly through your website or portal using credentials you manage and provide\. Customers can find all of the products for which they have active subscriptions under **Your Marketplace Software** in AWS Marketplace when they are signed in to their account\. This page contains a link to the page that customers use to sign in to your SaaS application\. 

#### Capturing the Amount of Usage<a name="capturing-the-amount-of-usage"></a>

 You record and calculate the usage of your software product\. As a customer’s usage increases or decreases, you send a metering record to AWS Marketplace\. These changes can be triggered automatically \(by observed customer usage\) or manually \(as the customer selects a different setting in your application\)\. For example, if you charge based on the amount of data sent into your application, you can measure the amount of data and send a corresponding metering record once an hour\. Or you might choose to have customers select a tier of data usage\. In this case, you can send a metering record that corresponds to the customer’s selection\. You can use AWS CloudTrail to verify the record\(s\) you sent are accurate, and can also use the information to perform audits over time\. For more information about the CloudTrail feature, see **Verify Records Using AWS CloudTrail**\. 

#### Cancellations<a name="cancellations"></a>

 Subscription cancellation must occur through the **Your Marketplace Software** page on the AWS Marketplace website\. You will receive notification when a customer cancels a subscription, and you will have one hour to send a final metering record for the customer\. You should send a notification from your application that is the cancellation is in progress\. If a customer deletes the account or cancels through your application, direct the customer to AWS Marketplace\. To guarantee there will be no future charges, customers should confirm cancellation with AWS Marketplace\. 

### Modeling and Listing Your SaaS Product<a name="modeling-and-listing-your-saas-product"></a>

 Before you can list your product on the AWS Marketplace, you need to decide how the product will be priced\. Categories and dimensions are used to define your pricing model\. 

#### Modeling Your Prices<a name="modeling-your-prices"></a>

 When pricing your software for SaaS Subscriptions or SaaS Contracts listing, you must first decide on *dimension* category, unit, and dimension\(s\) and how it will be consumed\. 

 What is a Category? 

 **Category** \- The type of unit on which customers will be billed\. For example, Users, Hosts, Data, or Bandwidth\. The category determines how products will be sorted on the AWS Marketplace search page\. 

 What is a Unit? 
+  **Unit** \- The unit of measurement by which customers will be charged for paid products\. Options will appear in the drop\-down list based on the category you selected\. The unit determines how the customer’s bill will be presented, and is shown on the pricing box on your product’s detail page\. 

#### Categories and Units<a name="categories-and-units"></a>

 Currently, AWS supports seven categories for SaaS Subscription and six catagoried for SaaS Contracts\. 

 Seller must pick one category and one matching unit before listing the product through AWS Marketplace\. The category and unit cannot be changed once the listing goes public\. 

 Table 1: Categories and Units available for **SaaS Subscriptions** listing\. 


|  Category  |  Valid Unit  | 
| --- | --- | 
|  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  | 
|  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  | 
|  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  | 
|  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  | 
|  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  | 
|  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  | 
|  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  | 

 Table 2: Categories and Units available for **SaaS Contracts** listing\. 


|  Category  |  Valid Unit  | 
| --- | --- | 
|  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  | 
|  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  | 
|  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  | 
|  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  | 
|  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  | 
|  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/saas-products.html)  | 
+  **Users** – One AWS customer can represent an organization with many internal users\. Your SaaS application can meter for the number of users signed in or provisioned at a given hour\. This category is appropriate for software in which a customer’s users connect to the software directly \(for example, with customer\-relationship management or business intelligence reporting\)\. 
+  **Hosts** – Any server, node, instance, endpoint, or other part of a computing system\. This category is appropriate for software that monitors or scans many customer\-owned instances \(for example, with performance or security monitoring\)\. Your application can meter for the number of hosts scanned or provisioned in a given hour\. 
+  **Data** – Storage or information, measured in MB, GB, or TB\. This category is appropriate for software that manages stored data or processes data in batches\. Your application can meter for the amount of data processed in a given hour or how much data is stored in a given hour\. 
+  **Bandwidth** – Your application can bill customers for an allocation of bandwidth that your application provides, measured in Mbps or Gbps\. This category is appropriate for content distribution or network interfaces\. Your application can meter for the amount of bandwidth provisioned for a given hour or the highest amount of bandwidth consumed in a given hour\. 
+  **Request** – Your application can bill customers for the number of requests they make\. This category is appropriate for query\-based or API\-based solutions\. Your application can meter for the number of requests made in a given hour\. 
+  **Tiers** – Your application can bill customers for a bundle of features or for providing a suite of dimensions below a certain threshold\. This is sometimes referred to as a feature pack\. For example, you can bundle multiple features into a single tier of service, such as up to 30 days of data retention, 100 GB of storage, and 50 users\. Any usage below this threshold is assigned a lower price as the **standard tier**\. Any usage above this threshold is charged a higher price as the **professional tier**\. Tier is always represented as an amount of time within the tier\. This category is appropriate for products with multiple dimensions or support components\. Your application should meter for the current quantity of usage in the given tier\. This could be a single metering record \(1\) for the currently selected tier or feature pack\. 
+  **Units** – Whereas each of the above is designed to be specific, the dimension of Unit is intended to be generic to permit greater flexibility in how you price your software\. For example, an IoT product which integrates with device sensors can interpret dimension “Units” as “sensors”\. Your application can also use units to make multiple dimensions available in a single product\. For example, you could price by data and by hosts using Units as your dimension\. 

#### **Examples**<a name="examples"></a>

 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-image-2.png)

 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-image-3.png)

#### Dimensions<a name="dimensions"></a>

 What is a Dimension? 

 **Dimension** \- Specific aspects of your product that you will bill for\. These may be individual tiers, types of hosts scanned, etc\. Each of these dimensions will be listed in the pricing box, and can either be metered for using AWS Marketplace Metering Service, or read from AWS Marketplace Entitlement Service, depending on which pricing strategy you’ve chosen\. 

 With dimensions, any SaaS product must specify either a single dimension or define up to 24 dimensions, each with their own price\. 
+  **Single Dimension** \- This is the simplest pricing option\. Customers pay a single price per resource unit per hour, regardless of size or volume \(for example, $0\.014 per user per hour, or $0\.070 per host per hour\)\. 
+  **Multiple Dimensions** – Use this pricing option for resources that vary by size or capacity\. For example, for host monitoring, a different price could be set depending on the size of the host\. Or, for user\-based pricing, a different price could be set based on the type of user \(admin, power user, and read\-only user\)\. If you are using tier\-based pricing, you should use one dimension for each tier\. 

 **Host Scanning Example** 

 Your application analyzes computing hardware for known security vulnerabilities\. Customers manually initiate or schedule these scans of their Amazon Elastic Compute Cloud \(EC2\) instances\. As your application performs these scans, it tallies the number of unique hosts scanned every hour\. Your application uses the Hosts category\. You can declare multiple dimensions for the types of hosts scanned\. For example, you can charge different prices for small, medium, and large hosts\. Or, if your application is agnostic to the type of hardware scanned, you would use a single dimension\. 

 **Log Analysis Example** 

 Your SaaS application digests logs generated by customer applications, reporting trends, and anomalies\. As customers upload logs to your application, you measure the quantity of data received in megabytes, gigabytes, or terabytes\. Every hour, your application meters for the data uploaded during that hour\. Your application uses the Data category\. Your application can also meter for the amount of log data stored for any given hour\. In this case, your application can meter along two dimensions: data received in the hour and total data stored in the hour\. You can continue to meter for data stored until the customer deletes this data or it expires\. 

#### Listing Your Product in AWS Marketplace<a name="listing-your-product-in-aws-marketplace"></a>

 As an AWS Marketplace seller you can list your products in AWS Marketplace\. To list a SaaS product in AWS Marketplace, log into the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/) and navigate to the **Listings** tab\. To create a new SaaS listing, in the **Create a New Product** menu, choose either **SaaS Subscriptions** or **SaaS Contracts**\. You must provide: 

 For SaaS Subscriptions: 
+  Software by, product title, product description, product logo, EULA, highlights, product category, search keywords, resources, support, refund policy 
+  The SaaS URL on your details page you want users redirected to \(registration landing page owned by the seller that will be used for accepting new customers coming from AWS Marketplace\) 
+  Category and unit of measurement 
+  Dimension API name, dimension description, dimension rate 
+  **Accounts to Whitelist** \- The account ID\(s\) you will use for testing your product integration\. If you own multiple AWS Accounts that you would like to whitelist to preview this listing, please enter any additional AWS Account IDs in the box below, as a comma\-separated list\. The account that you are using to create this listing request will be whitelisted by default\. 
+  **SaaS URL** \- This is the URL that customers will land on when they enter a billing agreement with your application, and then create an account\. This guide covers how you configure this website to retrieve customer billing information automatically\. 

 Dimensions for SaaS Subscriptions have the following: 
+  **Dimension API Name** \- The name used when sending metering records by calling MeterUsage API\. This name is visible in billing reports, but because the reports are not external\-facing, the name does not have to be user\-friendly\. The name can be no more than 15 characters and can only include alphanumeric and underscore characters\. After you set the name, you will not be able to change it\. 
+  **Dimension Description** \- The customer\-facing statement that describes the dimension for the product\. The description \(administrators per hour, per Mbps bandwidth provisioned, etc\.\) can be no more than 70 characters and should be user\-friendly\. After the product is published, you will not be able to change this description\. 
+  **Dimension Rate** \- The software charge per unit per hour for this product\. This field supports three decimal places\. 

### Integration Assistance<a name="integration-assistance"></a>

 This section assumes you have access to the AWS CLI, and have the requisite privileges required to carry forward the integration\. This document also assumes that you are registered as a seller in AWS Marketplace, and have submitted a SaaS Subscriptions or SaaS Contracts product that has been published to limited\. 

 Before we begin, we’ll want to make sure you have a couple things setup\. 

 **Note**: Information on setting up the AWS CLI, along with credentials, can be found [here](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)\. If you are new to the AWS Python SDK, there is a quick start guide [here](https://boto3.readthedocs.io/en/latest/guide/quickstart.html)\. 

#### IAM USER Policy For AWS Marketplace Actions<a name="iam-user-policy-for-aws-marketplace-actions"></a>

 In order to enable the service account under which the integration is running, we’ll need to define a very constrained IAM policy for that user\. Attach this to the IAM user or role you’ll use for the integration\. 

 **NOTE**: The first permission is required for all SaaS integrations\. The second and third are only needed for subscriptions and contracts, respectively\. 

 For more information about creating IAM users, see the documentation [here](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html)\. For more information about creating and assigning policies, see the documentation [here](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_change-permissions.html)\. 

 This policy grants access to the APIs for the role or IAM user to which the role is attached\. For brevity, this document provides code samples that assume the code is running with the permissions of that user or role\. For additional information on how to enable role assumption by another account for these API calls, see the documentation [here](https://aws.amazon.com/blogs/apn/how-to-best-architect-your-aws-marketplace-saas-subscription-across-multiple-aws-accounts/)\. 

### Registration<a name="registration"></a>

 When a customer chooses **Subscribe** on your SaaS listing in the AWS Marketplace, their browser will be redirected to a page designated by you at product listing using HTTPS\. This page should look for the ‘x\-amzn\-marketplace\-token’ in the form data and pass the registration token value to our API to resolve for the unique customer identifier and corresponding product code\. These values will be used to interact with the metering and entitlements APIs, so store them with the associated record\. 

 **NOTE**: The customer identifier is not the customer’s AWS account ID, but it is universal between products\. 

### Configuring Your SaaS Application to Accept New Customers<a name="configuring-your-saas-application-to-accept-new-customers"></a>

 With SaaS Subscriptions and SaaS Contracts, customers will still have independent accounts registered in your application\. You must maintain a website that allows new customers to register an account using billing identifiers provided by AWS\. During account creation or sign\-in, capture the customer billing identifier and store it along with that customer’s other account information\. 

 If your SaaS application will use AWS SaaS Billing with the AWS Marketplace Metering Service, you must: 
+  Create a registration page or modify the existing one to accept a token from AWS Marketplace that contains a customer identifier that can be stored along with the account registration process\. 
+  Create a process to run every hour that will call a RESTful AWS Marketplace service with the usage for all of your AWS Marketplace customers\. 

#### Concepts<a name="concepts"></a>
+  **Customer identifier** – This string represents a customer who is subscribed to your product\. It’s provided to you by AWS when the customer enters a billing agreement through the AWS Marketplace\. 
+  **Registration token** – Your application receives a registration token from the customer’s browser when the customer lands on your registration website\. Your application will redeem this registration token for a customer identifier\. The registration token is an opaque string\. 
+  **Product code** – This is a unique string for your SaaS application provided to you by AWS\. Each AWS listing has one unique product code\. It is assigned to you during registration\. \(Example: a290sds6en72spp3ph4q890es is a product code, b53a9230\-6767\-4735\-a3d9\-d5c41caa24c4 is a product id\) 
+  **Subscription notification** – An SNS notification in the following JSON format that informs you when a customer subscribes or unsubscribes to your product\. AWS will whitelist your seller AWS account to listen to these notifications on an SNS topic\. 

 The subscription notification can have four actions: subscribe\-success, subscribe\-fail, unsubscribe\-pending, and unsubscribe\-success\. 

#### Registration Process<a name="registration-process"></a>

 The following process takes place when customers purchase your application\. 

 **In AWS:** 

1.  When a customer visits your product listing page on the AWS Marketplace website, they choose to subscribe to your product by clicking **Agree to Terms and Register**\. 

1.  The customer’s AWS account is **subscribed** to your product\. This means metering records sent from your application will become part of the customer’s AWS bill\. 

1.  A registration token is generated for the customer that will contain the customer’s customer identifier to your website\. 

1.  The customer is redirected to your registration page\. This page must be able to accept the token with the customer’s identifier\. 

 **In your application:** 

1.  The customer’s browser sends a POST request to your SaaS registration URL\. The request contains one POST parameter, “x\-amzn\-marketplace\-token”, containing the customer’s registration token\. From the perspective of your registration website, the customer has submitted a form with this parameter\. 

1.  Your website must call the **ResolveCustomer** operation on AWS Marketplace Metering Service to redeem this token for a customer identifier and a product code\. 

1.  Your website validates the product code matches your SaaS application identity\. 

1.  Your website must keep this customer identifier in the customer’s session\. It can be stored temporarily on your server, or it can be part of a signed session cookie on the customer’s browser\. 

1.  The customer is instructed to either create an account in your application or sign in to an existing account\. 

1.  The customer is now signed in to your website using credentials specific to that SaaS application\. In your accounts database, you can have a row for each customer\. Your accounts database must have a column for AWS Customer Identifier, which you’ll now populate with the customer identifier you obtained in step 4\. **Verify that no other accounts in your system share this customer identifier\. Otherwise, you might send conflicting metering records\.** 

1.  During your seller registration process, you will be assigned an SNS topic that will notify you when customers subscribe or unsubscribe to your system\. **We recommend that you use SQS to capture these messages**\. After you receive a subscription notification with “subscribe\-success”, the customer account is ready for metering\. **Records you send before this notification will not be metered\.** Your accounts database should have an extra column for subscription state\. 

1.  Subsequent usage on that account will be metered using the customer identifier stored in your database\. 

#### Security and Ordering<a name="security-and-ordering"></a>

 **As a seller, it’s your responsibility to trust only customer identifiers that are immediately returned from AWS or those that are signed by your system\.** We recommend that you resolve the registration token immediately, because it will expire after one hour\. After you resolve the registration token, store the customer identifier as a signed attribute on the customer’s browser session until the registration is complete\. 

#### Disable Customers Who Unsubscribe<a name="disable-customers-who-unsubscribe"></a>

 A customer can unsubscribe to your Saas Subscription product through the AWS Management Console\. When a customer unsubscribes, the following events occur: 

1.  Your SaaS application is sent an “unsubscribe\-pending” notification through the SNS topic for that customer\. 

1.  You will have one hour to meter any remaining usage for the customer\. 

1.  After this hour, you will receive an “unsubscribe\-success” notification\. At this point, you can no longer send metering records for this customer\. 

 It’s up to you to decide how you want to disable functionality in your SaaS application for unsubscribed customers\. For example, your application might complete existing work, but prevent the customer from creating new work\. You might want to display a message to the customer that their usage has been disabled\. Customers can resubscribe to your product through the AWS Marketplace\. 

### Subscription Notifications<a name="subscription-notifications"></a>

 Secondly, we’ll need to subscribe to the AWS Marketplace SNS topic that was provided to you during product listing\. This topic will provide notifications about changes to customers’ subscription and entitlement statuses, allowing you to know when to provide and revoke access for specific customers\. 

#### Subscribing an SQS Queue to the SNS Topic<a name="subscribing-an-sqs-queue-to-the-sns-topic"></a>

 As is mentioned in the [AWS SaaS Billing Seller Integration Guide](https://s3.amazonaws.com/awsmp-loadforms/SaaS+Seller+Integration+Guide.pdf), we recommend subscribing an AWS SQS queue to the provided SNS topic\. Detailed instructions on creating an SQS queue can be found [here](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-create-queue.html); instructions for subscribing that queue to the provided topic can be found [here](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-subscribe-queue-sns-topic.html)\. 

#### Granting Permissions to Access the Queue<a name="granting-permissions-to-access-the-queue"></a>

 When you subscribe the SQS queue to the provided SNS topic, permissions will automatically be added to allow the SNS topic to publish messages to the queue\. However, we still need a policy for granting the API user access to the queue\. This can be applied to the same user, if the services will run with the same credentials\. Create a policy with the following contents, and attach it to your IAM user \(or associated role\)\. 

 **Note**: The ‘Resource’ field will be your SQS Queue ARN\. 

 For more information regarding cross\-account SNS and SQS subscription, please see Appendix A at the end of this document\. 

 Polling the SQS Queue for Notifications 

 Finally, you need to define a service that continually polls the queue, looking for messages and handling them accordingly\. 

 **Note**: As a **SaaS Subscriptions** seller, you need to handle four actions: **‘unsbscibe\-success’, ‘subscribe\-fail’, ‘unsubscribe\-pending’ and ‘unsubscribe\-success’\.** The only message action you need to handle as a **SaaS Contracts** seller is the **‘entitlement\-updated’** action\. All other actions are required by SaaS Subscription integrations only\. 

##### Updating SaaS Products<a name="updating-saas-products"></a>

 Once your product is listed on AWS Marketplace, you are responsible for keeping the pricing and product information up\-to\-date\. You make changes to your listing from the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/)\. To make changes, from the **Listings** tab, under **Current Listings** submit the updated information\. 

## AWS Marketplace Contract Service<a name="aws-marketplace-contract-service"></a>

 In SaaS Contracts model, customers are invoiced up\-front for quantity of usage purchased\. From that point forward, they are **entitled** to use those resources\. For example, a customer might purchase a quantity of users who can use your application for a one\-month time period, or for one\-year, two\-year, or three\-year time periods\. 

 When the customer buys your software, the customer enters an agreement with you\. Under the agreement, the customer is entitled to a specified quantity of use of your SaaS product\. AWS Marketplace communicates these entitlements to your SaaS application through the new AWS Marketplace Entitlement Service\. Under the SaaS Contract model, your application never sends metering records\. Instead, it verifies entitlement by calling the AWS Marketplace Entitlement Service\. 

### Customer Experience<a name="customer-experience-1"></a>

 Under the SaaS entitlement model, customers purchase quantities of usage directly on the AWS Marketplace website\. The buyer will be able to select specific quantities of varying dimensions or pick a dimension that will have a quantity of 1 in it\. 

 Example of regular drop down \(selection of specifc quantities for varying domesnions\) 

 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-image-5.png)

 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-image-6.png)

 Example of duration selection 

 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-image-7.png)

 For example, a customer might purchase 10 Users and 20 GB of Data or pick one dimension only, for example: US \-5GB/Day\. They can purchase units for the duration offered \(1\-, 12\-, 24, 36\-moths options\)\. All of these actions occur on the AWS Marketplace website during the subscription process\. 

#### Automatic Renewals<a name="automatic-renewals"></a>

 When a customer purchases your product through AWS Marketplace using SaaS contracts, they can agree to automatic renewal of these terms\. The customer will continue to pay for the entitlements every month, year, two years, or three years\. The customer always has the option to modify the renewal settings\. The renewal can be canceled, or the contract can be renewed for entirely different quantities or durations\. 

 The customer can disable renewal themselves or request a canellation and refund though AWS Customer Service\. The refund policy is the same as for annual AMI products\. Refunds can be granted within 48 hours through AWS Customer Service, or prorated after some duration with seller agreement\. 

#### Upgrades<a name="upgrades"></a>

 Customers can always upgrade a contract for one of a higher value \(for example, higher quantities, longer duration, or higher\-value entitlements\)\.Customers will be given a prorated credit for their existing contract\. 

 **Example**: A customer enters a contract for one user for 12 months for $100, paid every 12 months\. Six months into the contract, the customer requires additional users\. The customer expands the contract to 10 users for 12 months\. The new value is $1,000\. After $50 of credit is applied, the customer pays $950\. Customers are charged immediately after they make the change to the contract\. 

#### Registering an Account in the SaaS Application<a name="registering-an-account-in-the-saas-application-1"></a>

 After the customer has purchased your product using the entitlement feature, the customer will be directed to the site designated by you to set up an account in your SaaS application\. Under this model, the registration landing page for your application works just like the one described in “Configuring Your SaaS Application to Accept New Customers\.” 

#### Using the SaaS Application<a name="using-the-saas-application-1"></a>

 Your SaaS application is agnostic with respect to how your product is purchased or renewed\. The customer purchases the product through AWS Marketplace, then provisions or consumes the resources in your SaaS application\. 

 **Example**: A customer purchased a 1\-month contract on April 1st, 2018 for 1 unit priced $100\. Ten days into the contract, the customer requires additional units\. The customer expands the current contract to 4 units \(adding 3 more on April 11th, 2018\)\. The expiration date of contract remains the same: May 1, 2018\. 

 The price for upgrade is calculated on the prorated basis: 

 Used: 10 days out of 30 days in month of April used 1 unit priced at $100/unit/month = \(10/30\) x $100 x1 = $33\.33 

 Will use: 20 days remaining to use in a contract for 4 units priced at $100/unit/month = \(20/30\) x $100 x 4 = $266\.66 

 Since customer already paid $100 when purchased original contract for 1 unit April 1st, 2018, the price to upgrade to 4 units on April 11th, 2018 will be: $200, calculated from \($266\.66 \+ $33\.33\- $100\)\. 

 Entitlements are verified by your SaaS application, which makes calls to AWS Marketplace Contract Service, as described in this document\. 

### Modeling and Listing Your SaaS Contracts Product<a name="modeling-and-listing-your-saas-contracts-product"></a>

 Under the SaaS Contracts model, the concepts of **categories, units and** **dimensions** are the same as those in the SaaS Subscriptions pricing model\. You must choose a category \(Users, Bandwidth, Hosts, Data, Requests, or Units\) to represent your application, as well as unit from category selected\. 

 To understand how SaaS Subscriptions \(metering, consumption\) and SaaS Contracts \(entitlements\) differ for each category, let’s use Data as an example\. With SaaS Subscriptions model, your application reports some amount of data processed every hour\. With the SaaS Contracts model, a customer might have set aside some amount of storage in your SaaS application\. Depending on your choice as seller, the customer might not be allowed to breach this limit\. The contract modeled through AWS Marketplace does not include a concept of overage charges\. It is up to your SaaS application to prevent usage above the entitled quantity\. 

#### Modeling Your Prices for SaaS Contract<a name="modeling-your-prices-for-saas-contract"></a>

 After you select a category, unit and one or more dimensions, you must determine the unit costs for each dimension\. The unit costs can be for 1\-month, 12\-months, 24\-months, 36\-months duration length\. You can select to offer one, two, three, or all length options possible for you SaaS Contracts listing\. The durations must be the same across each dimension\. For example, in a case where you have ReadOnlyUsers and AdminUsers dimensions, if you offer a yearly price for ReadOnlyUsers, you must offer it for AdminUsers, too\. 

 **Example: User\-based application** 

 You offer an application that allows some number of accounts for a given customer\. 


|   |  Monthly Price  |  12\-month Price  | 
| --- | --- | --- | 
|  ReadOnlyUsers  |  $10/User  |  $100/User  | 
|  AdminUsers  |  $20/User  |  $200/User  | 

 **Important: 12\-month, 24\-month, 36\-month price is a one time charge, and NOT a rate charged customer every month\. If you offer $10 per unit for 1\-month, the price for 12\-month option should be $120 or less if you choose to offer a discount, etc\.** 

 **Example: Data storage application** 

 You offer an application that allows customers to store a certain amount of data in encrypted or unencrypted form\. If your application can perform encryption for the customer, you might charge a higher price for this service\. 


|   |  Monthly Price  |  12\-month Price  |  24\-month Price  | 
| --- | --- | --- | --- | 
|  Unencrypted Data \(GB\)  |  $1\.50/GB  |  $16\.00/GB  |  $30\.00/GB  | 
|  Encrypted Data \(GB\)  |  $1\.55/GB  |  $16\.60/GB  |  $31\.20/GB  | 

 **Example: Content distribution** 

 You offer an application that allows customer data to be distributed across several regions\. You allow the customer to allocate some dedicated network capacity \(bandwidth\)\. 


|   |  Monthly Price  |  12\-month Price  |  24\-month Price  |  36\-month Price  | 
| --- | --- | --- | --- | --- | 
|  Bandwidth \(100Mbs\)  |  $100/100Mbs  |  $1100/100Mbs  |  $2100/100Mbs  |  $3000/100Mbs  | 

#### Listing Your SaaS Contract Product in AWS Marketplace<a name="listing-your-saas-contract-product-in-aws-marketplace"></a>

 As an AWS Marketplace seller you can list your products in AWS Marketplace\. To list a SaaS product in AWS Marketplace, log into the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/) and navigate to the **Listings** tab\. To create a new SaaS listing, in the **Create a New Product** menu, choose either **SaaS Subscriptions** or **SaaS Contracts**\. Required information you must provide includes: 

 **For SaaS Contracts: ** 
+  Software by, Product title, product description, product logo, EULA, highlights, product category, search keywords, resources, support, refund policy 
+  The SaaS URL on your details page you want users redirected to \(registration landing page owned by the seller that will be used for accepting new customers coming from AWS Marketplace\) 
+  Contract Duration \(1\-, 12\-, 24, 36\- months\) 
+  Category and unit of measurement 
+  Enable Tiered Dimensions option 
+  Dimension API Name, Dimension Display Name, Dimension Description, Dimension price for durations selected 
+  Dimension Quantity \(optional if you select YES to enable Tiered Dimensions\) 
+  **Accounts to Whitelist**:\- The account ID\(s\) you will use for testing your product integration\. If you own multiple AWS Accounts that you would like to whitelist to preview this listing, please enter any additional AWS Account IDs in the box below, as a comma\-separated list\. The account that you are using to create this listing request will be whitelisted by default\. 
+  **SaaS URL** \- This is the URL that customers will land on when they enter a billing agreement with your application, and then create an account\. This guide covers how you configure this website to retrieve customer billing information automatically\. 
+  **Enable Tiered Dimensions –** Tiered Dimensions are used for volume tiers or bundles/packages\. This also allows you to specify pro\-rated pricing with the Dimension Quantity fileds below if desired\. Note: It cannot be changed one the listing goes live\. 
+  **Dimension Quantity** – The Quanitity field first compyutes the price per unit for each dimensions, For upgrades to the next tier, it charges for customer additional units based on the per\-unit price of the higher tier\. 
+  **Dimension API Name** – The name used when calling Entitlements API\. This name is visible in billing reports, but because the reports are not external\-facing, the name does not have to be user\-friendly\. The name can be no more than 15 characters and can only include alphanumeric and underscore characters\. After you set the name, you will not be able to change it\. 
+  **Dimension Display Name**: The customer\-facing name of a dimension that describes the dimension for the product\. The display name which will be visible on AWS Marketplace lsiting to customers \(AdminUsers, Silver Tier, Premier Bundle, etc\.\) can be no more than 24 characters and should be user\-friendly\. After the product is published, you will be able to change this display name\. 
+  **Dimension Description**: The customer\-facing desciption of a dimension that provides additional information about the dimension for the product\. The description \(Up to 10 Endpoints, 100\-250 API calls, etc\.\) can be no more than 70 characters and should be user\-friendly\. After the product is published, you will be able to change this description\. 
+  **Dimension \- Monthly Price**: The software charge per unit for 1\-month option for this dimension\. This field supports three decimal places\. 
+  **Dimension \- 1 Year Price**: The software charge per unit for 12\-month option for this dimension\. This field supports three decimal places\. It is not a monthly or yearly charge, the price must reflect 12\-month one time charge price\. 
+  **Dimension \- 2 Years Price:** The software charge per unit for 24\-month option for this dimension\. This field supports three decimal places\. It is not a monthly or yearly charge, the price must reflect 24\-month one time charge price\. 
+  **Dimension \- 3 Years Price:** The software charge per unit for 36\-month option for this dimension\. This field supports three decimal places\. It is not a monthly or yearly charge, the price must reflect 36\-month one time charge price\. 

### Configuring Your SaaS Application to Accept New Customers<a name="configuring-your-saas-application-to-accept-new-customers-1"></a>

 Just like SaaS Subscription products that use the consumption model, customers will still have independent accounts registered in your application\. You must maintain a website that allows new customers to register an account using billing identifiers provided by AWS\. This website can also allow customers to couple an existing account with AWS billing information\. During account creation or sign\-in, capture the customer billing identifier and store it along with the customer’s other account information\. 

 Rather than metering every hour, with SaaS Contracts, your application will periodically verify entitlement \(generally, when the customer provisions more resources\)\. The verification can also run periodically, or when the customer visits a dashboard on your SaaS application to provision more capacity\. The concepts of **Customer, Registration Token**, and **Product Code** are the same with SaaS Subscriptions \(consumption\-based\) products\. 

 After registering your product, you will have the option to sign up for an SNS topic that will provide notifications about contract creation and modification\. Your application should call **GetEntitlements** on AWS Marketplace Entitlement Service to retrieve the customer’s entitlement\. 

#### Registration Process<a name="registration-process-1"></a>

 The registration process is similar to consumption\-based products, with some minor differences\. 

 **In AWS:** 

1.  When a customer visits your product listing page on AWS Marketplace, they click **Purchase Users** \(or **Purchase Data**, or **Purchase Hosts, etc\.**\)\. 

1.  On the product’s fulfillment page, the customer can select quantities of entitlements or select one dimension only with one unit in it \(if seller enabled tiers\)\. 

1.  The customer finalizes the purchase\. 

1.  A registration token is generated that will convey the customer’s customer identifier to your website\. 

1.  The customer is redirected to your registration page\. This page must be able to accept the token with the customer identifier\. 

 **In your application:** 

1.  The customer’s browser sends a POST request to your SaaS registration URL\. The request contains one POST parameter, x\-amzn\-marketplace\-token, that contains the customer’s registration token\. 

1.  Your website must call the **ResolveCustomer** operation on AWS Marketplace Metering Service to redeem this token for a customer identifier and product code\. 

1.  Your website verifies that this product code matches your SaaS application\. 

1.  Your website must keep this customer identifier in the customer’s session\. It can be stored temporarily on your server, or it can be part of a signed session cookie on the customer’s browser\. 

1.  The customer is instructed to either create a new account in your application, or sign in to an existing account\. 

1.  The customer is now signed in to your SaaS application’s website using a set of credentials specific to that application\. In your accounts database, you might have a row for each customer\. Your accounts database should have a column for AWS Customer Identifier, which you’ll now populate with the customer identifier you obtained in step 4\. **You should verify that no other accounts in your system share this customer identifier\. Otherwise, you might have multiple accounts that share entitlement\.** This could lead to customers using more capacity in your system by simply creating multiple accounts\. 

1.  Subsequent usage on that account should be verified against AWS Marketplace Entitlement Service\. For example, if the customer provisions 10 users on the account, your SaaS application should check AWS Marketplace Entitlement Service for entitlement to that capacity\. 