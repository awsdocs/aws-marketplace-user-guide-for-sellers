# Pricing for SaaS contracts<a name="saas-contracts"></a>

 For SaaS contracts, AWS Marketplace bills your customers upfront or by the payment schedule that you define, based on the contract between you and your customer\. After that point, they're entitled to use those resources\. For additional usage above their contract, AWS Marketplace bills your customers based on the metering records received by us through the AWS Marketplace Metering Service\. 

1. Create a new SaaS product in the AWS Marketplace Management Portal, and make a note of its product code\.

1. Complete the wizard with the necessary information\.

To set your pricing, choose one or more contract durations you offer customers\. You can enter different prices for each contract duration\. Your options are monthly, 1\-year, 2\-year, and 3\-year durations\. 

 Choose the category that best describes your product’s pricing\. The pricing category appears to customers on the AWS Marketplace website\. You can choose from bandwidth \(GB/s, MB/s\), data \(GB, MB, TB\), hosts, requests, tiers, or users\. If none of the predefined categories fit your needs, you can choose the more generic **units** category\. 

For **Enable Tiered Dimensions**, choose how you want you customers to be able to purchase your product from the following options: 
+  **Buyer can choose only one tier offered** – Customers choose a tier from options that include different sets of features, services, and usage amounts\. 
+  **Buyer can choose one or more options offered** – Customers can select a quantity for each pricing dimension you offer\.

After you choose a category, define your pricing dimensions\. Each pricing dimension represents a feature or service that you can set a per unit price for\. Examples of dimensions are users, hosts scanned, and GB of logs ingested\. For each dimension you define, you add a name, a description, a price, and an API name\. The name, price, and description are displayed to customers\. You use the API name for tracking and reporting with AWS Marketplace as follows:
+ When calling the [AWS Marketplace Entitlement Service](https://docs.aws.amazon.com/marketplaceentitlement/latest/APIReference/Welcome.html) to retrieve the dimensions your customers have purchased\.
+ When calling the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) to indicate which dimensions customers used\.

 For each pricing dimension that you add to your contract, you can choose to let customers pay as they go for additional usage of that dimension above their contract\. You can also add additional dimensions without contract prices that customers only consume by paying as they go\.

When using the wizard to create the contracts for your SaaS product, you must define the following fields for your pricing dimensions:
+  **Dimension API Name** – The name used when calling the Entitlements API\. This name is visible in billing reports and reports are not external\-facing\. The maximum length for the API name is 15 characters, and after you set the name it can't be changed\. 
+  **Dimension Display Name**: – The customer\-facing name of a dimension\. This name should help the customer understand the dimension for the product\. The name should be user\-friendly and the maximum length is 24 characters\. This value can be changed\.
+  **Dimension Description**: – The customer\-facing description of a dimension that provides additional information about the dimension for the product\. The maximum length for the description is 70 characters\.
+  **Dimension \- Monthly Price** – The software charge per unit for the 1\-month option for this dimension\. This ﬁeld supports three decimal places\.
+  **Dimension \- 1 Year Price** – The software charge per unit for the 12\-month option for this dimension\. This ﬁeld supports three decimal places\. It's not a monthly charge\. The price must reﬂect the 12\-month one\-time charge price\. 
+  **Dimension \- 2 Years Price** – The software charge per unit for the 24\-month option for this dimension\. This ﬁeld supports three decimal places\.
+  **Dimension \- 3 Years Price** – The software charge per unit for the 36\-month option for this dimension\. This ﬁeld supports three decimal places\.


**Example: Data storage application**  

|   | Monthly price  | 12\-month price  | 24\-month price  | Pay\-as\-you\-go price for additional usage  | 
| --- | --- | --- | --- | --- | 
|  Unencrypted data \(GB\)  |  $1\.50/GB  |  $16\.00/GB  |  $30\.00/GB  |  $0\.1/GB per hour  | 
|  Encrypted data \(GB\)  |  $1\.55/GB  |  $16\.60/GB  |  $31\.20/GB  |  $0\.11/GB per hour  | 


**Example: Log monitoring product**  

|   | Monthly price  | 12\-month price  | Pay\-as\-you\-go price for additional usage  | 
| --- | --- | --- | --- | 
|  Basic \(10 hosts monitored, 5 containers monitored\)  |  $100  |  $1000  |   | 
|  Standard \(20 hosts monitored, 10 containers monitored\)  |  $200  |  $2000  |   | 
|  Pro \(40 hosts monitored, 20 containers monitored\)  |  $400  |  $4000  |   | 
|  Additional hosts monitored per hour  |   |   |  $0\.1  | 
|  Additional containers monitored per hour  |   |   |  $0\.2  | 

**Note**  
The prices can be for the following durations: 1 month, 12 months, 24 months, or 36 months\. You can choose to offer one or more of these options for your product\. The durations must be the same across each dimension\. For example, in a case where you have `ReadOnlyUsers` and `AdminUsers` dimensions, if you offer a yearly price for ReadOnlyUsers, you must offer a yearly price for `AdminUsers`, too\.

## Upgrades<a name="upgrades"></a>

 Customers can upgrade a contract to one of a higher value except for longer durations\. For example, they can upgrade to higher quantities or higher\-value entitlements\. Customers are given a prorated credit for their existing contract\. Customers can't decrease the size of their existing contract\. They can only decrease the size at renewal, or cancel their renewal\.

 Entitlements are veriﬁed by your SaaS product, which makes calls to the AWS Marketplace Entitlement Service\. 

## Automatic renewals<a name="automatic-renewals"></a>

 When a customer purchases your product through AWS Marketplace using SaaS contracts, they can agree to automatic renewal of the contract terms\. The customer continues to pay for the entitlements every month or for 1, 2, or 3 years\. The customer always has the option to modify the renewal settings\. They can cancel the renewal or renew the contract different quantities and durations\. 

## When a SaaS contract ends<a name="saas-contract-ends"></a>

A SaaS contract product has a contract expiry\. When a contract ends, the following events occur: 

1.  Your SaaS product receives an `entitlement-updated` notification indicating their entitlement has changed, and the AWS Marketplace Entitlement Service returns an empty response\. 

1.  You have one hour to meter any remaining usage for the customer\. 

1.  After this you can no longer send metering records for this customer\. 