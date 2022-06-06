# Pricing for SaaS contracts<a name="saas-contracts"></a>

For software as a service \(SaaS\) contracts, the customer initiates a purchase of your software and enters into an agreement with you\. Under the agreement, the customer is entitled to a specified quantity of use of your SaaS product\. AWS Marketplace communicates these entitlements to your SaaS application\. This is done through the AWS Marketplace Entitlement Service\. When using the SaaS Contract pricing model, your application never sends metering records\. Instead, it verifies entitlement by calling the AWS Marketplace Entitlement Service\. You define the usage categories, dimensions, and the length of the contract\. 

AWS Marketplace bills your customers upfront or by the payment schedule that you define, based on the contract between you and your customer\. After that point, they're entitled to use those resources\. For additional usage above their contract, AWS Marketplace bills your customers based on the metering records received by us through the AWS Marketplace Entitlement Service\. 

Before you can publish a SaaS product with contract pricing, you must do the following:

1. Create a new SaaS product in the AWS Marketplace Management Portal, and choose **New SaaS Contract**\.

1. Complete the fields in the **General** tab with the necessary information\. Make a note of the product code\.

1. On the **Pricing** tab:

   1. For **Set Pricing**, choose the **Contract Duration** you want offer customers\. You can enter different prices for each contract duration\. You can select one or more of the following options: **Monthly**, **1 year**, **2 Years**, and **3 Years**\. If you are creating a private offer, you can choose a custom duration in months \(up to 60 months\)\. 

   1. For **Choose the contract type you want to offer**, choose how you want customers to be able to purchase your product from the following options: 
      +  **Buyer can choose one or more options offered** – Customers can select a quantity for each pricing dimension you offer\.
      +  **Buyer can choose one tier from multiple tiers offered** – Customers choose a tier from options that include different sets of features, services, and usage amounts\. 

   1.  Choose the usage unit category that describes your product’s pricing most accurately\. The pricing category appears to customers on the AWS Marketplace website\. You can choose from **Bandwidth** \(GBps, MBps\), **Data** \(GB, MB, TB\), **Hosts** \(hours\), **Requests**, **Tiers** \(hours\), or **Users** \(hours\)\. If none of the predefined categories fit your needs, you can choose the more generic **Units** category\.

1. After you choose a category, define your Pricing Dimensions\. Each Pricing Dimension represents a feature or service that you can set a per unit price for\. Examples of dimensions are users, hosts scanned, and GB of logs ingested\. For each dimension you define, you add a name, a description, a price, and an API name\. The name, price, and description are displayed to customers\. You use the API name for tracking and reporting with AWS Marketplace as follows:
   + Calling the [AWS Marketplace Entitlement Service](https://docs.aws.amazon.com/marketplaceentitlement/latest/APIReference/Welcome.html) to retrieve the dimensions your customers have purchased\.
   + Calling the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) to indicate which dimensions customers used\.

    For each pricing dimension in your contract, you can choose to let customers pay as they go for additional usage of that dimension above their contract\. You can also add additional dimensions without contract prices that customers only consume by paying as they go\.

   When using the wizard to create the contracts for your SaaS product, you must define the following fields for your pricing dimensions:
   +  **Dimension API Name** – The name used when calling the Entitlements API\. This name is visible in billing reports and reports that aren't external\-facing\. The maximum length for the API name is 15 characters\. After you set the name, it can't be changed\. 
   +  **Dimension Display Name**: – The customer\-facing name of a dimension\. This name should help the customer understand the dimension for the product\. The name should be user\-friendly, and its maximum length is 24 characters\. This value can be changed\.
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
The prices can be for the following durations: 1 month, 12 months, 24 months, or 36 months\. You can choose to offer one or more of these options for your product\. The durations must be the same across each dimension\. For example, assume that you have `ReadOnlyUsers` and `AdminUsers` dimensions\. If you offer a yearly price for `ReadOnlyUsers`, you must offer a yearly price for `AdminUsers`, too\.

## SaaS contract upgrades<a name="upgrades"></a>

 Customers can upgrade a contract to one of a higher value except for longer durations\. For example, they can upgrade to higher quantities or higher\-value entitlements\. Customers are given a prorated credit for their existing contract\. Customers can't decrease the size of their existing contract\. They can only decrease the size at renewal, or cancel their renewal\.

 Entitlements are veriﬁed by your SaaS product, which makes calls to the AWS Marketplace Entitlement Service\. 

## Automatic renewals<a name="automatic-renewals"></a>

 When a customer purchases your product through AWS Marketplace using SaaS contracts, they can agree to automatic renewal of the contract terms\. The customer continues to pay for the entitlements every month or for 1, 2, or 3 years\. The customer always has the option to modify the renewal settings\. They can cancel the renewal or renew the contract for different quantities and durations\. 

## When a SaaS contract ends<a name="saas-contract-ends"></a>

A SaaS contract product has a contract expiry\. When a contract ends, the following events occur: 

1.  Your SaaS product receives an `entitlement-updated` notification indicating the buyer's entitlement has changed\. The AWS Marketplace Entitlement Service returns an empty response\. 

1.  You have 1 hour to meter any remaining usage for the customer\. After this time has elapsed, you can no longer send metering records for this customer\. 

## When a SaaS contract is canceled<a name="saas-contract-cancellations"></a>

Key points of the SaaS contract cancellation process include the following: 

1. Customers can request a cancellation and refund for SaaS contract products though AWS Support\.

   Customers must request refunds within 48 hours through AWS Support\. 

   The full or prorated refund is typically granted in 3–5 business days\. 

1. Your SaaS product is sent notiﬁcation through the Amazon SNS topic for that customer\.

1. You have one hour to send a ﬁnal metering record for the customer for any additional usage charges\. 

1. You notify the customer from your product that the cancellation is in progress\. If a customer indicates that they want to cancel through your product, direct the customer to AWS Marketplace\. To guarantee that there will be no future charges, customers should conﬁrm the cancellation with AWS Marketplace\. 

## Creating a SaaS free trial offer<a name="creating-a-saas-free-trial-offer"></a>

Sellers can create and manage SaaS free trial offers in the AWS Marketplace Management Portal \(AMMP\)\. Customers can evaluate software products before making large purchase decisions by using the SaaS free trial option\. After a customer subscribes to your product, your product performs entitlement checks the same way it does for paid customers\.

If you use Seller Data Delivery Service \(SDDS\), a new supplemental SaaS free trial report, 'agreement\_detail\_report', will be delivered daily to your S3 bucket\. The report includes agreement details such as `is_free_trial_offer`, subscriber name and id, `offer_id`, agreement start and end date, etc\. As a seller, you also receive SNS notifications when new subscriptions are created\. SNS notifications include a` isFreeTrialTermPresent` flag to help identify free trial agreements\.

Each AWS account can only use a free trial for a SaaS product once\. The free usage amount granted during a free trial is not shared across linked accounts in an AWS organization\. Different linked accounts within a single main payer account can create their own individual free trials\.

**To create and manage SaaS free trial offers as a seller**

1. Sign in to the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management), and choose **Create or manage offers** from **Offers** on the navigation bar\.

1. Choose the **Public free trials** tab to review all SaaS free trials and then choose **Create free trial offer**\. Sellers can create one SaaS free trial offer per each public SaaS contract\.

1. For **Offer fundamentals**, select your **Product** and then choose **Next**\.

1. In **Free trial settings**, enter the number of days for your **Free trial length**, enter the dimensions from your existing public offer, and set the quantity limits per each dimension\. The duration of free trials range from 7\-90 days\. You also have the option to **Remove** or **Add dimensions**\.

1. For **Service agreement**, select your contract type or **Custom EULA** and then choose **Review offer**\.

1. Verify and review all information for the offer, and then choose **Create offer**\.

## Cancelling a SaaS free trial offer<a name="cancel-saas-free-trial-offer"></a>

Sellers can cancel free trial offers at any time from the AWS Marketplace Management Portal by selecting the offer, choosing **View details**, and choosing **Cancel offer**\. Once an offer is canceled, active agreements for this offer will be active until expiration\. New agreements for a canceled offer can't be created\.