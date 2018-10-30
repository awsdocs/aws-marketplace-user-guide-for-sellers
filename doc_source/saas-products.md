# Software\-as\-a\-Service\-Based Products<a name="saas-products"></a>

 As a software as a service \(SaaS\) seller, you deploy software hosted on AWS infrastructure and are responsible for granting AWS Marketplace customers access to the software\. There are no AMIs to configure and your customers do not have to run your software on their own EC2 instances\. With SaaS, customers subscribe to products through AWS Marketplace, but access the product in your environment\. AWS Marketplace offers 2 different pricing models for SaaS listings: 
+  SaaS Subscriptions 
+  SaaS Contracts 

 With **SaaS Subscriptions**, you use the AWS Marketplace Metering Service to report metering usage to AWS\. The usage data is used to bill customers for SaaS application use\. All charges must be measured and reported every hour from the software deployed in the customer's account\. 

 With **SaaS Contracts**, you use the AWS Marketplace Contract Service to bill customers in advance for the use of your software\. Customers pay upfront for a time\-bound entitlement to use your SaaS software\. Under SaaS Contracts, the customer is entitled to a specified quantity and duration of use of the SaaS product\. 

 With SaaS Subscriptions and SaaS Contracts, customers subscribe to your SaaS listings through AWS Marketplace\. After a customer finds and subscribes to your SaaS product on AWS Marketplace, AWS Marketplace passes a billing identifier to your website\. Customer account creation, resource provisioning and account management is done through your website or APIs\. Customers then access the product in your AWS environment, or through a VPC endpoint service connection you create\. 

 For both SaaS Subscriptions and SaaS Contracts listings, you can use AWS PrivateLink technology, to configure your service as an Amazon Virtual Private Cloud \(VPC\) endpoint service and your customers can create a VPC endpoint and access your software across the Amazon network\. Alternatively, you can provide access to your software product through your website, with customers creating a connection across the Internet\. 

## Requirements for SaaS Subscriptions and SaaS Contracts listings<a name="requirements-for-saas-subscriptions-and-saas-contracts-listings"></a>

### SaaS Subscriptions and SaaS Contracts Comparison<a name="saas-subscriptions-and-saas-contracts-comparison"></a>

 As a SaaS application owner offering through AWS Marketplace, you must pick one of two options available for listing and billing your software: 
+  SaaS Subscriptions \(also known as: pay as you go, consumption monetization model\) 
+  SaaS Contracts \(also known as: entitlement monetization model\) 

 **With SaaS Subscriptions**, you use the AWS Marketplace Metering Service to report metering usage to AWS which will be used to bill customers for SaaS application use\. 

 AWS Marketplace Metering Service provides a *consumption* monetization model in which customers are charged only for the number of resources they use in your application\. The consumption model is similar to that for most AWS services\. Customers pay as they go\. 

 **With SaaS Contracts**, you use the AWS Marketplace Contract Service to bill customers in advance for the use of your software\. The AWS Marketplace Contract Service provides an *entitlement* monetization model in which customers are invoiced in advance for a certain amount of usage of your software, and AWS communicates this *entitlement* to your application\. For example, you might sell your customer a certain amount of storage per month for a year, or a certain amount of end\-user licenses for 2 years\. The customer makes a payment as part of their standard billing cycle\. 

 Table 1: Comparison chart for SaaS Subscription and SaaS Contract models\. 


|   |  SaaS Subscriptions  |  SaaS Contracts  | 
| --- | --- | --- | 
|  Also called  |  Metering, pay\-as\-you\-go, consumption\-based monetization  |  Provisioning\-based monetization  | 
|  How customers use the application  |  Similar to using an AWS service\. Customers subscribe to the listing, get provisioned in seller’s environment, and are charged based on usage\.  |  Similar to a classic SaaS application\. Customers sign up for capacity up front, and then use the application within the limits of that capacity and duration\.  | 
|   |   |   | 
|  Time granularity of usage  |  Hourly  |  1, 12, 24, 36\-months options  | 
|  How sellers communicate with AWS  |  Sellers send AWS metering records: “Customer X used Y for Z hour”  |  AWS stores duration, dimension and \# of units purchased in dimension, payment, and access details and provides entitlement records to sellers: “Customer X is allowed to use Y dimension until Z date”  | 
|  When customers are charged  |  Monthly, within the normal AWS billing cycle\.  |  When the customer purchases an initial contract, upgrades to using more capacity or their capacity is auto\-renewed\.  | 
|  Traditional way to realize discounts  |  Tiered usage plans; pay less per unit for increased usage\.  |  Discounts are incorporated into prices for longer\-term commitments or bundles of higher quantities\.  | 
|  Example application  |   [https://aws\.amazon\.com/marketplace/pp/B074CQY6KB](https://aws.amazon.com/marketplace/pp/B074CQY6KB)   [https://aws\.amazon\.com/marketplace/pp/B075MWZVBM](https://aws.amazon.com/marketplace/pp/B075MWZVBM)   [https://aws\.amazon\.com/marketplace/pp/B0722D4QRN](https://aws.amazon.com/marketplace/pp/B0722D4QRN)   |   [https://aws\.amazon\.com/marketplace/pp/B075CRJXNK](https://aws.amazon.com/marketplace/pp/B075CRJXNK)   [https://aws\.amazon\.com/marketplace/pp/B06XXM7JJT](https://aws.amazon.com/marketplace/pp/B06XXM7JJT)   [https://aws\.amazon\.com/marketplace/pp/B076J22YD8](https://aws.amazon.com/marketplace/pp/B076J22YD8)   | 

### SaaS Subscriptions Pricing<a name="saas-subscriptions-pricing"></a>

 For SaaS Subscriptions, AWS Marketplace will bill your customers based on the metering records received by us\. Products utilizing SaaS Subscriptions must qualify under one of our seven pricing categories: Users, Hosts, Data, Bandwidth, Requests, Tiers and Units\. You will then select the unit of measure for the category selected\. You define at least one dimension to offer up to 24 variants for the single listing\. All charges must be measured and reported every hour from the software deployed in the customer's account\. All usage is then calculated and billed monthly using the same mechanism as AMI based AWS Marketplace offerings\. **AWS’ ability to bill customers for usage of your product is dependent upon receiving metering records from you\. You are responsible for ensuring that your product’s metering records are successfully transmitted and received\.** 

### SaaS Contracts Pricing<a name="saas-contracts-pricing"></a>

 Products utilizing SaaS Subscriptions must qualify under one of our six pricing categories: Users, Hosts, Data, Bandwidth, Requests, and Units\. You will then select the unit of measure for the category selected\. You define at least one dimension to offer up to 24 variants for the single listing, as well as the length options of the contract\. Under the agreement, the customer is entitled to a specified quantity of use of your SaaS product\. AWS Marketplace communicates these entitlements to your SaaS application through the AWS Marketplace Entitlement Service\. When using SaaS Contracts, your application never sends metering records, instead it verifies entitlement by calling the AWS Marketplace Entitlement Service\. You are responsible for calling the AWS Marketplace Entitlement Service to determine if a customer is operating within their paid entitlement\. 

#### Modeling Contracts Pricing<a name="modeling-contracts-pricing"></a>
+  Pick a category – Only 1 category per product\. 
+  Determine dimensions per product \(up to 24 supported\)\. 
  +  Ex: Category = admins, users; Dimensions = power, read\-only, etc\. 
+  Determine contract duration options for the product\. This must be the same across all dimensions\. 
  +  1, 12,24,36 month options available\. You can pick any combination\. 
+  Determine per unit pricing per dimension for the lowest contract duration term \(monthly\)\. 
  +  Ex: Admin user = $4/month, Power User = $3/month, Read Only = $1/month\. 
+  If offering longer terms, multiply the monthly price by 12, 24, or 36\. 
+  If you would like to offer tier/package pricing, we also support radio buttons\. This means the customer can only purchase one tier, instead of multiple\. For example, a customer would select 1 tier of up to 100 GB, and pay a set amount for this contract\. 
+  We do not support validation rules when buying a contract \- No minimum, maximum,exclusivity, aggregation, mix of radio buttons and drop downs, etc\. 
+  AWS Marketplace does not support charging overage fees\. 

## SaaS Subscriptions<a name="saas-subscriptions"></a>

 ***Subscription Flow* ** 

 With SaaS Subscriptions and SaaS Contracts, customers subscribe to products through AWS Marketplace, but access the product in the seller’s environment\. When a customer subscribes to a product, AWS Marketplace passes a billing identifier to the seller\. All of the remaining steps \(customer account creation, resource provisioning, and account management\) occur on the seller’s website or with the seller’s APIs\. 

 Figure : AWS SaaS billing customer flow\. 

![\[Software as a service billing flow for customers\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-image-1.png)

 **Metering** 

 Your application will report usage information to AWS, and customers will pay for their use of your SaaS application through their AWS bill based on the metering records you provide\. This is an extension of the [AWS Marketplace Metering Service](https://aws.amazon.com/documentation/marketplace/) \(MMS\)\. When your application **meters usage** for a customer, your application is providing AWS with a quantity of usage accrued for a given hour\. Your application meters for real units of value, such as gigabytes transferred or hosts scanned in a given hour\. AWS uses this information to calculate a customer’s bill based on rates that you provide when you create a SaaS listing\. Collected transaction proceeds are disbursed to you as an AWS Marketplace seller\. It is your responsibility to confirm that your metering is being delivered to AWS Marketplace in a manner that permits AWS to correctly bill your customers for use of your product\. 

### Customer Experience<a name="customer-experience"></a>

 A customer discovers your software by browsing or searching AWS Marketplace\. If interested, the customer clicks a link that redirects immediately to the your site to purchase and obtain access to the software\. After subscribing to the product, the customer is directed to the your website to register their account and configure the product\. 

#### Registering an Account in the SaaS Application<a name="registering-an-account-in-the-saas-application"></a>

 After the customer has subscribed in AWS Marketplace, the customer will register an account in your SaaS application on a website that you host\. The registration landing page accepts a token from AWS Marketplace with the customer’s identifier for billing\. 

#### Using the SaaS Application<a name="using-the-saas-application"></a>

 Customers access your SaaS application directly through your website or portal using credentials you manage and provide\. Customers can find all of the products for which they have active subscriptions under **Your Marketplace Software** in AWS Marketplace when they are signed in to their account\. This page contains a link to the page that customers use to sign in to your SaaS application\. 

#### Capturing the Amount of Usage<a name="capturing-the-amount-of-usage"></a>

 You record and calculate the usage of your software product\. As a customer’s usage increases or decreases, you send a metering record to AWS Marketplace\. These changes can be triggered automatically \(by observed customer usage\) or manually \(as the customer selects a different setting in your application\)\. For example, if you charge based on the amount of data sent into your application, you can measure the amount of data and send a corresponding metering record once an hour\. Or you might choose to have customers select a tier of data usage\. In this case, you can send a metering record that corresponds to the customer’s selection\. You can use AWS CloudTrail to verify the record\(s\) you sent are accurate, and can also use the information to perform audits over time\. For more information about the CloudTrail feature, see **Verify Records Using http://docs\.aws\.amazon\.com/awscloudtrail/latest/userguide/**\. 

#### Cancellations<a name="cancellations"></a>

 Subscription cancellation must occur through the **Your Marketplace Software** page on the AWS Marketplace website\. You will receive a notification when a customer cancels a subscription, and you will have one hour to send a final metering record for the customer\. You should send a notification from your application that the cancellation is in progress\. If a customer deletes the account or cancels through your application, direct the customer to AWS Marketplace\. To guarantee there will be no future charges, customers should confirm the cancellation with AWS Marketplace\. 

### Modeling and Listing Your SaaS Product<a name="modeling-and-listing-your-saas-product"></a>

 Before you can list your product on the AWS Marketplace, you need to decide how the product will be priced\. Categories and dimensions are used to define your pricing model\. 

#### Modeling Your Prices<a name="modeling-your-prices"></a>

 When pricing your software for a SaaS Subscriptions or a SaaS Contracts listing, you must first decide on a dimension category, unit, dimension\(s\) and how it will be consumed\. 

 What is a Category? 

 **Category** \- "The type of unit customers will be billed on, for example, Users, Hosts, Data, or Bandwidth\. The category also determines how products will be sorted on the AWS Marketplace search page\. 

 What is a Unit? 
+  **Unit** \- The unit of measurement for paid products that customers will be charged for\. Options will appear in the drop\-down list based on the category you selected\. The unit determines how the customer’s bill will be presented, and is shown on the pricing box on your product’s detail page\. 

#### Categories and Units<a name="categories-and-units"></a>

 AWS Marketplace supports seven categories for SaaS Subscriptions and six categories for SaaS Contracts\. 

 You must pick one category and one matching unit before listing the product through AWS Marketplace\. The category and unit cannot be changed once the listing goes public\. 

 Table 1: Categories and Units available for **SaaS Subscriptions** listings\. 


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
+  **Tiers** – Your application can bill customers for a bundle of features or for providing a suite of dimensions below a certain threshold\. This is sometimes referred to as a feature pack\. For example, you can bundle multiple features into a single tier of service, such as up to 30 days of data retention, 100 GB of storage, and 50 users\. Any usage below this threshold is assigned a lower price as the **standard tier**\. Any usage above this threshold is charged a higher price as the **professional tier**\. A tier is always represented as an amount of time within the tier\. This category is appropriate for products with multiple dimensions or support components\. Your application should meter for the current quantity of usage in the given tier\. This could be a single metering record \(1\) for the currently selected tier or feature pack\. 
+  **Units** – Whereas each of the above is designed to be specific, the dimension of a Unit is intended to be generic to permit greater flexibility in how you price your software\. For example, an IoT product which integrates with device sensors can interpret dimension “Units” as “sensors”\. Your application can also use units to make multiple dimensions available in a single product\. For example, you could price by data and by hosts using Units as your dimension\. 

#### **Examples**<a name="examples"></a>

 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-image-2.png)

 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-image-3.png)

#### Dimensions<a name="dimensions"></a>

 What is a Dimension? 

 **Dimension** \- Specific aspects of your product that you will bill for\. These may be individual tiers, types of hosts scanned, etc\. Each of these dimensions will be listed in the pricing box, and can either be metered by using the AWS Marketplace Metering Service, or read from the AWS Marketplace Entitlement Service, depending on which pricing strategy you’ve chosen\. 

 With dimensions, any SaaS product must specify either a single dimension or define up to 24 dimensions, each with their own price\. 
+  **Single Dimension** \- This is the simplest pricing option\. Customers pay a single price per resource unit per hour, regardless of size or volume \(for example, $0\.014 per user per hour, or $0\.070 per host per hour\)\. 
+  **Multiple Dimensions** – Use this pricing option for resources that vary by size or capacity\. For example, for host monitoring, a different price could be set depending on the size of the host\. Or, for user\-based pricing, a different price could be set based on the type of user \(admin, power user, and read\-only user\)\. If you are using tier\-based pricing, you should use one dimension for each tier\. 

 **Host Scanning Example** 

 Your application analyzes computing hardware for known security vulnerabilities\. Customers manually initiate or schedule these scans of their Amazon Elastic Compute Cloud \(EC2\) instances\. As your application performs these scans, it tallies the number of unique hosts scanned every hour\. In this example, your application uses the Hosts category\. You can declare multiple dimensions for the types of hosts scanned\. For example, you can charge different prices for small, medium, and large hosts\. Or, if your application is agnostic to the type of hardware scanned, you would use a single dimension\. 

 **Log Analysis Example** 

 Your SaaS application digests logs generated by customer applications, reporting trends, and anomalies\. As customers upload logs to your application, you measure the quantity of data received in megabytes, gigabytes, or terabytes\. Every hour, your application meters for the data uploaded during that hour\. In this example, your application uses the Data category\. Your application can also meter for the amount of log data stored for any given hour\. In this case, your application can meter along two dimensions: data received in the hour and total data stored in the hour\. You can continue to meter for data stored until the customer deletes this data or it expires\. 

#### Listing Your Product in AWS Marketplace<a name="listing-your-product-in-aws-marketplace"></a>

 As an AWS Marketplace seller you can list your products in AWS Marketplace\. To list a SaaS product in AWS Marketplace, log into the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/) and navigate to the **Listings** tab\. To create a new SaaS listing, in the **Create a New Product** menu, choose either **SaaS Subscriptions** or **SaaS Contracts**\. You must provide: 

 For SaaS Subscriptions: 
+  Software by, product title, product description, product logo, EULA, highlights, product category, search keywords, resources, support, refund policy 
+  The SaaS URL on your details page you want users redirected to \(this is the registration landing page owned by the seller that will be used for accepting new customers coming from AWS Marketplace\)\. 
+  Category and unit of measurement 
+  Dimension API name, dimension description, dimension rate 
+  **Accounts to White list** \- The account ID\(s\) you will use for testing your product integration\. If you own multiple AWS Accounts that you would like to whitelist to preview this listing, enter all of these as a comma\-separated list\. The account that you are using to create this listing request will be white listed by default\. 
+  **SaaS URL** \- This is the URL that customers will land on when they enter a billing agreement with your application, and create an account\.

 Dimensions for SaaS Subscriptions have the following: 
+  **Dimension API Name** \- The name used when sending metering records by calling a MeterUsage API\. This name is visible in billing reports, but because the reports are not external\-facing, the name does not have to be user\-friendly\. The name can be no more than 15 characters and can only include alphanumeric and underscore characters\. After you set the name, you will not be able to change it\. 
+  **Dimension Description** \- The customer\-facing statement that describes the dimension for the product\. The description \(administrators per hour, per Mbps bandwidth provisioned, etc\.\) can be no more than 70 characters and should be user\-friendly\. After the product is published, you will not be able to change this description\. 
+  **Dimension Rate** \- The software charge per unit per hour for this product\. This field supports three decimal places\. 

### Integration Assistance<a name="integration-assistance"></a>

 This section assumes you have access to the AWS CLI, and have the requisite privileges required to carry forward the integration\. This document also assumes that you are registered as a seller in AWS Marketplace, and have submitted a SaaS Subscriptions or SaaS Contracts product that has been published to limited\. 

 Before you begin, we want to make sure you have a couple things setup\. 

 **Note**: Information on setting up the AWS CLI, along with credentials, can be found [here](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)\. If you are new to the AWS Python SDK, there is a quick start guide [here](https://boto3.readthedocs.io/en/latest/guide/quickstart.html)\. 

#### IAM USER Policy For AWS Marketplace Actions<a name="iam-user-policy-for-aws-marketplace-actions"></a>

 In order to enable the service account under which the integration is running, you need to define a very constrained IAM policy for that user\. Attach this to the IAM user or role you’ll use for the integration\. 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
            "iam:Generate*",
            "iam:Get*",
            "iam:List*",
            iam:Simulate*"
            ],
            "Resource":arn:aws:iam::123456789123:user/goldmine-test-seller-with-customer-support-policy"
            }
            ]
        }
```

 **NOTE**: The first permission is required for all SaaS integrations\. The second and third are only needed for subscriptions and contracts, respectively\. 

 For more information about creating IAM users, see the documentation [here](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html)\. For more information about creating and assigning policies, see the documentation [here](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_change-permissions.html)\. 

 This policy grants access to the APIs for the role or IAM user to which the role is attached\. For brevity, this document provides code samples that assume the code is running with the permissions of that user or role\. For additional information on how to enable role assumption by another account for these API calls, see the documentation [here](https://aws.amazon.com/blogs/apn/how-to-best-architect-your-aws-marketplace-saas-subscription-across-multiple-aws-accounts/)\. 

### Registration<a name="registration"></a>

 When a customer chooses **Subscribe** on your SaaS listing in the AWS Marketplace, their browser will be redirected to a page designated by you at product listing using HTTPS\. This page should look for the `x-amzn-marketplace-token` in the form data\. It should then pass the registration token value to our API to resolve for the unique customer identifier and corresponding product code\. These values will be used to interact with the metering and entitlements APIs, so store them with the associated record\. 

```
    ##### Resolving Customer Registration Token #####
    formFields = urlparse.parse_qs(postBody):
    if formFields.has_key('x-amzn-marketplace-token'):
    marketplaceClient = boto3.client('meteringmarketplace')
    customerData = marketplaceClient.resolve_customer(
    RegistrationToken=formFields['x-amzn-marketplace-token'])
    productCode = customerData['ProductCode']
    customerId = customerData['CustomerIdentifier']
    # TODO: Store information away with your customer record
    # TODO: Validate no other accounts share this identifier
```

 **NOTE**: The customer identifier is not the customer’s AWS account ID, but it is universal between products\. 

### Configuring Your SaaS Application to Accept New Customers<a name="configuring-your-saas-application-to-accept-new-customers"></a>

 With SaaS Subscriptions and SaaS Contracts, customers will still have independent accounts registered in your application\. You must maintain a website that allows new customers to register an account using billing identifiers provided by AWS\. During account creation or sign\-in, capture the customer billing identifier and store it along with that customer’s other account information\. 

 If your SaaS application will use AWS SaaS Billing with the AWS Marketplace Metering Service, you must: 
+  Create a registration page or modify the existing one to accept a token from AWS Marketplace that contains a customer identifier\. This can be stored along with the account registration process\. 
+  Create a process to run every hour that will call a RESTful AWS Marketplace service with the usage for all of your AWS Marketplace customers\. 

#### Concepts<a name="concepts"></a>
+  **Customer identifier** – This string represents a customer who is subscribed to your product\. It’s provided to you by AWS when the customer enters a billing agreement through the AWS Marketplace\. 
+  **Registration token** – Your application receives a registration token from the customer’s browser when the customer lands on your registration website\. Your application will redeem this registration token for a customer identifier\. The registration token is an opaque string\. 
+  **Product code** – This is a unique string for your SaaS application provided to you by AWS\. Each AWS listing has one unique product code\. It is assigned to you during registration\. \(Example: a290sds6en72spp3ph4q890es is a product code, b53a9230\-6767\-4735\-a3d9\-d5c41caa24c4 is a product id\) 
+  **Subscription notification** An SNS notification in JSON format that informs you when a customer subscribes or unsubscribes to your product\. AWS will white list your seller AWS account to listen to these notifications on an SNS topic\. 

```
      {
      "action": "subscribe-success",
      "customer-identifier": "T1VJRC0xMjM0MTIzNDEyMzQtNTY3ODU2ODc1Nj",
      "product-code": "72m8mmj6t2dgb8dfscnpsbfmn"
      }
```

 The subscription notification can have four actions: subscribe\-success, subscribe\-fail, unsubscribe\-pending, and unsubscribe\-success\. 

#### Registration Process<a name="registration-process"></a>

 The following process takes place when customers purchase your application\. 

 **In AWS:** 

1.  When a customer visits your product listing page on the AWS Marketplace website, they choose to subscribe to your product by clicking **Agree to Terms and Register**\. 

1.  The customer’s AWS account is **subscribed** to your product\. This means metering records sent from your application will become part of the customer’s AWS bill\. 

1.  A registration token is generated for the customer that will contain their customer identifier to your website\. 

1.  The customer is redirected to your registration page\. This page must be able to accept the token with the customer’s identifier\. 

 **In your application:** 

1.  The customer’s browser sends a POST request to your SaaS registration URL\. The request contains one POST parameter, “x\-amzn\-marketplace\-token”, containing the customer’s registration token\. From the perspective of your registration website, the customer has submitted a form with this parameter\. 

1.  Your website must call the **ResolveCustomer** operation on AWS Marketplace Metering Service to redeem this token for a customer identifier and a product code\. 

1.  Your website validates that the product code matches your SaaS application identity\. 

1.  Your website must keep this customer identifier in the customer’s session\. It can be stored temporarily on your server, or it can be part of a signed session cookie on the customer’s browser\. 

1.  The customer is instructed to either create an account in your application or sign in to an existing account\. 

1.  The customer is now signed in to your website using credentials specific to that SaaS application\. In your accounts database, you can have a row for each customer\. Your accounts database must have a column for the AWS Customer Identifier, which you’ll populate with the customer identifier you obtained in step 4\. Verify that no other accounts in your system share this customer identifier otherwise, you might send conflicting metering records\.

1.  During your seller registration process, you will be assigned an SNS topic that will notify you when customers subscribe or unsubscribe to your system\. **We recommend that you use SQS to capture these messages**\. After you receive a subscription notification with “subscribe\-success”, the customer account is ready for metering\. **Records you send before this notification will not be metered\.** Your accounts database should have an extra column for the subscription state\. 

1.  Subsequent usage on that account will be metered using the customer identifier stored in your database\. 

#### Security and Ordering<a name="security-and-ordering"></a>

 **As a seller, it’s your responsibility to trust only customer identifiers that are immediately returned from AWS or those that are signed by your system\.** We recommend that you resolve the registration token immediately, because it will expire after one hour\. After you resolve the registration token, store the customer identifier as a signed attribute on the customer’s browser session until the registration is complete\. 

#### Disable Customers Who Unsubscribe<a name="disable-customers-who-unsubscribe"></a>

 A customer can unsubscribe to your SaaS Subscription product through the AWS Management Console\. When a customer unsubscribes, the following events occur: 

1.  Your SaaS application is sent an “unsubscribe\-pending” notification through the SNS topic for that customer\. 

1.  You will have one hour to meter any remaining usage for the customer\. 

1.  After this hour, you will receive an “unsubscribe\-success” notification\. At this point, you can no longer send metering records for this customer\. 

 It’s up to you to decide how you want to disable functionality in your SaaS application for unsubscribed customers\. For example, your application might complete existing work, but prevent the customer from creating new work\. You might want to display a message to the customer that their usage has been disabled\. Customers can resubscribe to your product through the AWS Marketplace\. 

### Subscription Notifications<a name="subscription-notifications"></a>

 You will need to subscribe to the AWS Marketplace SNS topic that was provided to you during the product listing\. This topic will provide notifications about changes to customers’ subscription and entitlement statuses\. This will allow you to know when to provide and revoke access for specific customers\. 

#### Subscribing an SQS Queue to the SNS Topic<a name="subscribing-an-sqs-queue-to-the-sns-topic"></a>

 We recommend subscribing an AWS SQS queue to the provided SNS topic\. Detailed instructions on creating an SQS queue can be found [here](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-create-queue.html); instructions for subscribing that queue to the provided topic can be found [here](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-subscribe-queue-sns-topic.html)\. 

#### Granting Permissions to Access the Queue<a name="granting-permissions-to-access-the-queue"></a>

 When you subscribe the SQS queue to the provided SNS topic, permissions will automatically be added to allow the SNS topic to publish messages to the queue\. However, you still need a policy for granting the API user access to the queue\. This can be applied to the same user, if the services will run with the same credentials\. Create a policy with the following contents, and attach it to your IAM user \(or associated role\)\. 

```
        {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "sqs:ReceiveMessage",
                "sqs:DeleteMessage",
                "sqs:GetQueueAttributes",
                "sqs:GetQueueUrl"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:sqs:REGION_HERE:XXXXXXXXXXXX:NAME_HERE"
        }
    ]
}
```

 **Note**: The ‘Resource’ field will be your SQS Queue ARN\. 

 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-image-9.png)

#### Polling the SQS Queue for Notifications<a name="polling-the-sqs-queue-for-notifications"></a>

 Finally, you need to define a service that continually polls the queue, looking for messages and handling them accordingly\. 

 **Note**: As a **SaaS Subscriptions** seller, you need to handle four actions: **‘unsubscibe\-success’, ‘subscribe\-fail’, ‘unsubscribe\-pending’ and ‘unsubscribe\-success’\.** The only message action you need to handle as a **SaaS Contracts** seller is the **‘entitlement\-updated’** action\. All other actions are required by SaaS Subscription integrations only\. 

##### Updating SaaS Products<a name="updating-saas-products"></a>

 Once your product is listed on AWS Marketplace, you are responsible for keeping the pricing and product information up\-to\-date\. You make changes to your listing from the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/)\. To make changes, from the **Listings** tab, under **Current Listings** submit the updated information\. 