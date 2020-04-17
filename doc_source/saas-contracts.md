# Pricing for SaaS contracts<a name="saas-contracts"></a>

 For SaaS contracts, AWS Marketplace bills your customers upfront or by the payment schedule that you define, based on the contract between you and your customer\. After that point, they're entitled to use those resources\. For example, a customer might purchase a quantity of users who can use your application for a 1\-month time period or for 1\-year, 2\-year, or 3\-year time periods\. For additional usage above their contract, AWS Marketplace bills your customers based on the metering records received by us through the AWS Marketplace Metering Service\. 

 To add a product using the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour/), select the **Products** tab and choose **SaaS**\. Then, from **Create SaaS Product** choose **SaaS Contracts** from the dropdown menu\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-pricing-contracts-screenshot.png)

 To describe your product and pricing model, complete the following views:
+  **Onboarding** – Banking and tax information for your product
+  **General** – Product name, URL, and other metadata to make your product discoverable in AWS Marketplace 
+  **Pricing** – How you will price your product
+  **Notes** – \(Optional\) Specific notes or instructions to the AWS Marketplace team for publishing your product

 To set your pricing, choose one or more contract durations you offer customers\. You can enter different prices for each contract duration\. Your options are monthly, 1\-year, 2\-year, and 3\-year durations\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-pricing-contract-duration-example.png)

 Choose the category that best describes your product’s pricing\. The pricing category appears to customers on the AWS Marketplace website\. You can choose from bandwidth \(GBps, MBps\), data \(GB, MB, TB\), hosts, requests, tiers, or users\. If none of the predefined categories fit your needs, you can choose the more generic **units** category\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-pricing-tiered-pricing-example.png)

For **Enable Tiered Dimensions**, choose how you want you customers to be able to purchase your product: 
+  **Buyer can choose only one tier offered** – Customers choose a tier from options that include different sets of features, services, and usage amounts\. For example, a *gold* tier for a monitoring product might include access to XYZ features, 100 hosts/hr monitored, and 50 containers/hr monitored\. A customer might purchase 10 users and 20 GB of data or pick one dimension only: for example, 5 GB per day\. They can purchase units for the duration oﬀered \(1,12, 24 or 36 months\)\. 
+  **Buyer can choose one or more options offered** – Customers can select a quantity for each pricing dimension you offer\. For example, a monitoring product can offer hosts per hour and containers per hour as pricing dimensions, and customers choose the number of hosts or containers that they want to monitor in their contract\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-pricing-dimension-example.png)

 Choose the category that best describes your product’s pricing\. The pricing category appears to customers on the AWS Marketplace website\. You can pick from bandwidth, data, hosts, requests, tiers, or users\. If none of the predefined categories fit your needs, you can choose the generic **units** category\. After you choose a category, define your pricing dimensions\. Each pricing dimension represents a feature or service that you can set a per unit price for\. Examples of dimensions are users, hosts scanned, and GB of logs ingested\. For each dimension you define, you add a name, a description, a price, and an API name\. The name, price, and description are displayed to customers\. You use the API name when calling [AWS Marketplace Entitlement Service](https://docs.aws.amazon.com/marketplaceentitlement/latest/APIReference/Welcome.html) to retrieve the dimensions customers purchased, and when sending metering records to the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) to indicate which dimensions customers used\.

 For each pricing dimension that you add to your contract, you can choose to let customers pay as they go for additional usage of that dimension above their contract\. You can also add additional dimensions without contract prices that customers only consume by paying as they go\. For example, these may be add\-on features that customers use infrequently \(e\.g\., custom reports generated\)\. Another example is if you have a pricing model where the contract dimensions are tiers that include bundles of services \(e\.g\., 50 hosts and 20 containers\), and the additional pay\-as\-you\-go dimensions represent the use of individual services \(per host and per container\)\. Define the following fields:
+  **Dimension API Name** – The name used when calling the Entitlements API\. This name is visible in billing reports, but because the reports are not external\-facing, the name does not have to be user\-friendly\. The name can be no more than 15 characters and can only include alphanumeric and underscore characters\. After you set the name, you will not be able to change it\. 
+  **Dimension Display Name**: – The customer\-facing name of a dimension\. This name should help the customer understand the dimension for the product\. The display name is visible on the AWS Marketplace product page to customers \(e\.g\., AdminUsers, Silver Tier, Premier Bundle\)\. The name should be user\-friendly and can be no more than 24 characters\. After the product is published, you will be able to change this display name\. 
+  **Dimension Description**: – The customer\-facing description of a dimension that provides additional information about the dimension for the product\. The description \(up to 10 endpoints, 100–250 API calls, etc\.\) can be no more than 70 characters and should be user\-friendly\. 
+  **Dimension \- Monthly Price** – The software charge per unit for the 1\-month option for this dimension\. This ﬁeld supports three decimal places\. 
+  **Dimension \- 1 Year Price** – The software charge per unit for the 12\-month option for this dimension\. This ﬁeld supports three decimal places\. It's not a monthly charge\. The price must reﬂect the 12\-month one\-time charge price\. 
+  **Dimension \- 2 Years Price** – The software charge per unit for the 24\-month option for this dimension\. This ﬁeld supports three decimal places\. It's not a monthly or yearly charge\. The price must reﬂect the 24\-month one\-time charge price\. 
+  **Dimension \- 3 Years Price** – The software charge per unit for the 36\-month option for this dimension\. This ﬁeld supports three decimal places\. It's not a monthly or yearly charge\. The price must reﬂect the 36\-month one\-time charge price\. 


**Example: Data storage application**  

|   | Monthly price  | 12\-month price  | 24\-month price  | Pay\-as\-you\-go price for additional usage  | 
| --- | --- | --- | --- | --- | 
|  Unencrypted data \(GB\)  |  $1\.50/GB  |  $16\.00/GB  |  $30\.00/GB  |  $0\.1/GB per day  | 
|  Encrypted data \(GB\)  |  $1\.55/GB  |  $16\.60/GB  |  $31\.20/GB  |  $0\.11/GB per day  | 


**Example: Log monitoring product**  

|   | Monthly price  | 12\-month price  | Pay\-as\-you\-go price for additional usage  | 
| --- | --- | --- | --- | 
|  Basic \(10 hosts monitored, 5 containers monitored\)  |  $100  |  $1000  |   | 
|  Standard \(20 hosts monitored, 10 containers monitored\)  |  $200  |  $2000  |   | 
|  Pro \(40 hosts monitored, 20 containers monitored\)  |  $400  |  $4000  |   | 
|  Additional hosts monitored per hour  |   |   |  $0\.1  | 
|  Additional containers monitored per hour  |   |   |  $0\.2  | 

 After you select a category, unit, and one or more dimensions, you must define the prices for each dimension, as shown in the following image\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-pricing-contract-options-example.png)

The prices can be for the following durations: 1 month, 12 months, 24 months, or 36 months\. You can choose to oﬀer one, two, three, or all four options for your product\. The durations must be the same across each dimension\. For example, in a case where you have ReadOnlyUsers and AdminUsers dimensions, if you oﬀer a yearly price for ReadOnlyUsers, you must oﬀer it for AdminUsers, too\.