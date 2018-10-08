# SaaS Contracts<a name="saas-contract"></a>

 In the SaaS Contracts model, customers are invoiced up\-front for quantity of usage purchased\. From that point forward, they are **entitled** to use those resources\. For example, a customer might purchase a quantity of users who can use your application for a one\-month time period, or for one\-year, two\-year, or three\-year time periods\. 

 When the customer buys your software, the customer enters an agreement with you\. Under the agreement, the customer is entitled to a specified quantity of use of your SaaS product\. AWS Marketplace communicates these entitlements to your SaaS application through the new AWS Marketplace Entitlement Service\. Under the SaaS Contract model, your application never sends metering records\. Instead, it verifies entitlement by calling the AWS Marketplace Entitlement Service\. 

## Customer Experience<a name="customer-experience-1"></a>

 Under the SaaS entitlement model, customers purchase quantities of usage directly on the AWS Marketplace website\. The buyer will be able to select specific quantities of varying dimensions or pick a dimension that will have a quantity of 1 in it\. 

 Example of regular drop down \(selection of specific quantities for varying dimensions\) 

 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-image-5.png)

 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-image-6.png)

 Example of a duration selection 

 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-image-7.png)

 A customer might purchase 10 Users and 20 GB of Data or pick one dimension only, for example: US \-5GB/Day\. They can purchase units for the duration offered \(1,12, 24 or 36 month options\)\. All of these actions occur on the AWS Marketplace website during the subscription process\. 

### Automatic Renewals<a name="automatic-renewals"></a>

 When a customer purchases your product through AWS Marketplace using SaaS contracts, they can agree to automatic renewal of these terms\. The customer will continue to pay for the entitlements every month, year, two years, or three years\. The customer always has the option to modify the renewal settings\. The renewal can be canceled, or the contract can be renewed for entirely different quantities or durations\. 

 The customer can disable the renewal themselves or request a cancellation and refund though AWS Customer Service\. The refund policy is the same as for annual AMI products\. Refunds must be requested within 48 hours through AWS Customer Service\. The full or prorated refund \( after some duration with the seller agreement\) will typically be granted in 3 to 5 working days\. 

### Upgrades<a name="upgrades"></a>

 Customers can always upgrade a contract for one of a higher value \(for example, higher quantities, longer duration, or higher\-value entitlements\)\. Customers will be given a prorated credit for their existing contract\. 

 **Example**: A customer enters a contract for one user for 12 months for $100, paid every 12 months\. Six months into the contract, the customer requires additional users\. The customer expands the contract to 10 users for 12 months\. The new value is $1,000\. After $50 of credit is applied, the customer pays $950\. Customers are charged immediately after they make the change to the contract\. 

### Registering an Account in the SaaS Application<a name="registering-an-account-in-the-saas-application-1"></a>

 After the customer has purchased your product using the entitlement feature, the customer will be directed to the site designated by you to set up an account in your SaaS application\. Under this model, the registration landing page for your application works just like the one described in “Configuring Your SaaS Application to Accept New Customers\.” 

### Using the SaaS Application<a name="using-the-saas-application-1"></a>

 Your SaaS application is agnostic with respect to how your product is purchased or renewed\. The customer purchases the product through AWS Marketplace, then provisions or consumes the resources in your SaaS application\. 

 **Example**: A customer purchased a 1\-month contract on April 1st, 2018 for 1unit priced $100\. Ten days into the contract, the customer requires additional units\. The customer expands the current contract to 4 units \(adding 3 more on April 11th, 2018\)\. The expiration date of the contract remains the same: May 1, 2018\. 

 The price for the upgrade is calculated on a prorated basis: 

 Used: 10 days out of 30 days in the month of April, used 1 unit priced at $100/unit/month = \(10/30\) x $100 x1 = $33\.33 

 Will use: 20 days remaining in a contract for 4 units priced at $100/unit/month = \(20/30\) x $100 x 4 = $266\.66 

 Since the customer already paid $100 when you purchased the original contract for 1 unit on April 1st, 2018, the price to upgrade to 4 units on April 11th, 2018 will be $200, calculated from \($266\.66 \+ $33\.33\- $100\)\. 

 Entitlements are verified by your SaaS application, which makes calls to the AWS Marketplace Contract Service, as described in this document\. 

## Modeling and Listing Your SaaS Contracts Product<a name="modeling-and-listing-your-saas-contracts-product"></a>

 Under the SaaS Contracts model, the concepts of **categories, units and** **dimensions** are the same as those in the SaaS Subscriptions pricing model\. You must choose a category \(Users, Bandwidth, Hosts, Data, Requests, or Units\) to represent your application, as well as the unit from the category selected\. 

 To understand how SaaS Subscriptions \(metering, consumption\) and SaaS Contracts \(entitlements\) differ for each category, let’s use Data as an example\. With the SaaS Subscriptions model, your application reports the amount of data processed every hour\. With the SaaS Contracts model, a customer might have set aside an amount of storage in your SaaS application\. Depending on your choice as seller, the customer might not be allowed to breach this limit\. The contract modeled through AWS Marketplace does not include the concept of overage charges\. 

### Modeling Your Prices for SaaS Contracts<a name="modeling-your-prices-for-saas-contract"></a>

 After you select a category, unit and one or more dimensions, you must determine the unit costs for each dimension\. The unit costs can be for 1 month, 12 months, 24 months or 36 months duration length\. You can select to offer one, two, three, or all four options for your SaaS Contracts listing\. The durations must be the same across each dimension\. For example, in a case where you have ReadOnlyUsers and AdminUsers dimensions, if you offer a yearly price for ReadOnlyUsers, you must offer it for AdminUsers, too\. 

 **Example: User\-based application** 

 You offer an application that allows for a certain number of accounts for a given customer\. 


|   |  Monthly Price  |  12\-month Price  | 
| --- | --- | --- | 
|  ReadOnlyUsers  |  $10/User  |  $100/User  | 
|  AdminUsers  |  $20/User  |  $200/User  | 

**Note**  
 The 12 month, 24 month and the 36 month price is a one\-time charge and NOT a rate charged to the customer every month\. If you offer $10 per unit for 1 month, the price for the 12 month option should be $120 or less if you choose to offer a discount, etc\. 

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

### Listing Your SaaS Contract Product in AWS Marketplace<a name="listing-your-saas-contract-product-in-aws-marketplace"></a>

 As an AWS Marketplace seller you can list your products in AWS Marketplace\. To list a SaaS product in AWS Marketplace, log into the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/) and navigate to the **Listings** tab\. To create a new SaaS listing, in the **Create a New Product** menu, choose either **SaaS Subscriptions** or **SaaS Contracts**\. Required information you must provide includes: 

 **For SaaS Contracts: ** 
+  Software by, Product title, product description, product logo, EULA, highlights, product category, search keywords, resources, support, refund policy 
+  The SaaS URL on your details page you want users redirected to \(registration landing page owned by the seller that will be used for accepting new customers coming from AWS Marketplace\) 
+  Contract Duration \(1 month, 12 months, 24 months, 36 months\) 
+  Category and unit of measurement 
+  Enable Tiered Dimensions option 
+  Dimension API Name, Dimension Display Name, Dimension Description, Dimension price for durations selected 
+  Dimension Quantity \(optional if you select YES to enable Tiered Dimensions\) 
+  **Accounts to White list**:\- The account ID\(s\) you will use for testing your product integration\. If you own multiple AWS Accounts that you would like to white list to preview this listing, enter these as a comma\-separated list\. The account that you are using to create this listing request will be white listed by default\. 
+  **SaaS URL** \- This is the URL that customers will land on when they enter a billing agreement with your application, and then create an account\. This guide covers how you configure this website to retrieve customer billing information automatically\. 
+  **Enable Tiered Dimensions –** Tiered Dimensions are used for volume tiers or bundles/packages\. This also allows you to specify pro\-rated pricing with the Dimension Quantity fields below if desired\. This cannot be changed once the listing goes live\. 
+  **Dimension Quantity** – The Quantity field computes the price per unit for each dimensions\. For upgrades to the next tier, it charges for customer additional units based on the per\-unit price of the higher tier\. 
+  **Dimension API Name** – The name used when calling the Entitlements API\. This name is visible in billing reports, but because the reports are not external\-facing, the name does not have to be user\-friendly\. The name can be no more than 15 characters and can only include alphanumeric and underscore characters\. After you set the name, you will not be able to change it\. 
+  **Dimension Display Name**: The customer\-facing name of a dimension that describes the dimension for the product\. The display name which will be visible on the AWS Marketplace listing to customers \(AdminUsers, Silver Tier, Premier Bundle, etc\.\) must be user\- friendly and can be no more than 24 characters\. After the product is published, you will be able to change this display name\. 
+  **Dimension Description**: The customer\-facing description of a dimension that provides additional information about the dimension for the product\. The description \(up to 10 Endpoints, 100\-250 API calls, etc\.\) can be no more than 70 characters and should be user\-friendly\. 
+  **Dimension \- Monthly Price**: The software charge per unit for the 1 month option for this dimension\. This field supports three decimals\. places\. 
+  **Dimension \- 1 Year Price**: The software charge per unit for the 12 month option for this dimension\. This field supports three decimal places\. This is not a monthly or yearly charge, the price must reflect the12 month one\-time charge price\. 
+  **Dimension \- 2 Years Price:** The software charge per unit for the 24 month option for this dimension\. This field supports three decimal places\. It is not a monthly or yearly charge, the price must reflect 24 month one\-time charge price\. 
+  **Dimension \- 3 Years Price:** The software charge per unit for the 36\-month option for this dimension\. This field supports three decimal places\. This is not a monthly or yearly charge, the price must reflect the 36 month one\-time charge price\. 

## Configuring Your SaaS Application to Accept New Customers<a name="configuring-your-saas-application-to-accept-new-customers-1"></a>

 Just like SaaS Subscription products that use the consumption model, customers will still have independent accounts registered in your application\. You must maintain a website that allows new customers to register an account using billing identifiers provided by AWS\. This website must also allow customers to couple an existing account with AWS billing information\. During account creation or sign\-in, capture the customer billing identifier and store it along with the customer’s other account information\. 

 Rather than metering every hour, with SaaS Contracts, your application will periodically verify entitlement \(generally, when the customer provisions more resources\)\. The verification can also run periodically, or when the customer visits a dashboard on your SaaS application to provision more capacity\. The concepts of Customer, Registration Token and Product Code are the same as SaaS Subscriptions \(consumption\-based\) products\. 

**Note**  
 If a customer notifies you that they tried to subscribe to one of your SaaS Contracts listing and are having trouble, and you cannot find the API results for their attempt, the most probable cause is that the customer inadvertantly cancelled their subscription within 24 hours of subscription\. Because there is no entitlement, there is no entry in the report\. 

 After registering your product, you will have the option to sign up for an SNS topic that will provide notifications about contract creation and modification\. Your application should call `GetEntitlements` on the AWS Marketplace Entitlement Service to retrieve the customer’s entitlement\. 

 **The AWS Marketplace Entitlement Service is currently available in the us-east-1 region.**
### Registration Process<a name="registration-process-1"></a>

 The registration process is similar to consumption\-based products, with some minor differences\. 

 **In AWS:** 

1.  When a customer visits your product listing page on AWS Marketplace, they choose **Purchase Users**, **Purchase Data**, **Purchase Hosts, etc\.**\. 

1.  On the product’s fulfillment page, the customer can select the quantities of entitlements or select one dimension only with one unit in it \(if you enabled tiers\)\. 

1.  The customer finalizes the purchase\. 

1.  A registration token is generated that will convey the customer’s customer identifier to your website\. 

1.  The customer is redirected to your registration page\. This page must be able to accept the token with the customer identifier\. 

 **In your application:** 

1.  The customer’s browser sends a POST request to your SaaS registration URL\. The request contains one POST parameter, x\-amzn\-marketplace\-token, that contains the customer’s registration token\. 

1.  Your website must call the `ResolveCustomer` operation on the AWS Marketplace Metering Service to redeem this token for a customer identifier and product code\. 

1.  Your website verifies that this product code matches your SaaS application\. 

1.  Your website must keep this customer identifier in the customer’s session\. It can be stored temporarily on your server, or it can be part of a signed session cookie on the customer’s browser\. 

1.  The customer is instructed to either create a new account in your application, or sign in to an existing account\. 

1.  The customer is now signed in to your SaaS application’s website using a set of credentials specific to that application\. In your accounts database, you might have a row for each customer\. Your accounts database should have a column for the AWS Customer Identifier, which you’ll now populate with the customer identifier you obtained in step 4\. **You should verify that no other accounts in your system share this customer identifier\. Otherwise, you might have multiple accounts that share entitlement\.** This could lead to customers using more capacity in your system by simply creating multiple accounts\. 

1.  Subsequent usage on that account should be verified against the AWS Marketplace Entitlement Service\. For example, if the customer provisions 10 users on the account, your SaaS application should check the AWS Marketplace Entitlement Service for entitlement to that capacity\. 