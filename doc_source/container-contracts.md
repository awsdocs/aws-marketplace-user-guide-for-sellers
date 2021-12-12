# Contract pricing for container products<a name="container-contracts"></a>

For container\-based products with contract pricing, AWS Marketplace bills your customers upfront or by the payment schedule that you define, based on the contract between you and your customer\. After that point, they're entitled to use those resources\. 

To set your pricing, choose one or more contract durations that you offer customers\. You can enter different prices for each contract duration\. Your options are 1\-month, 12\-months, 24\-month, and 36\-month durations\. For private offers, you can specify a custom duration in months \(up to 60 months\)\. 

Choose the category that best describes your product’s pricing\. The pricing category appears to customers on the AWS Marketplace website\. You can choose from **Bandwidth** \(GB/s, MB/s\), **Data** \(GB, MB, TB\), **Hosts**, **Requests**, **Tiers**, or **Users**\. If none of the predefined categories fit your needs, you can choose the more generic **Units** category\. 

For **Contracts Dimension Allow Multiple Purchases**, choose from the following options: 
+  **True** – Configurable pricing
+  **False** – Feature\-based pricing

For each pricing dimension that you add to your contract, you can choose to let customers pay as they go for additional usage of that dimension above their contract\. You can also add additional dimensions without contract prices that customers only consume by paying as they go\.

The offer allows for up to 24 dimensions to be added to it\. Each dimension requires the following data:
+ **Contracts Category** – The contract category is used to measure or meter your product if the product supports consumption based metering on top of contract pricing\. For contract products with no consumption based pricing, you can choose a category which most closely resembles the category of dimension in the contract\. If no values resemble the units for the dimension in the contract, choose `Units`\. 
+ **Contracts Unit** – The contract unit is used along with category for metering if the product supports consumption based metering\. Choose one of the available values for the units that closely matches your dimensions based on the category selected\.
+ **Contracts Dimension Allow Multiple Purchases** – This field is used to indicate whether an offer is a tiered pricing offer or a non\-tiered offer which allows for purchase of multiple dimensions\. 

  **Tiered offer** – Allows the buyer to subscribe to only one of the available dimensions in the offer\. Dimensions in a tiered offer don't have the concept of quantities\. Signing a contract with a specific dimension essentially indicates that the buyer has chosen the specific feature indicated by that dimension\.

  **Non\-tiered offer** – Allows the customer to procure more than one dimensions as part of the contract and allows them to procure multiple units of each such dimension\.

  Setting a value of *true* for this field indicates that the offer is a non\-tiered offer\. Setting a value of *false* for this field indicates that the offer is a tiered offer\.

When using the Product Load Form \(PLF\) to create the contracts for your Container product, you must define the following fields for your pricing dimensions:
+  **Contracts DimensionX API Name** – The name that should appear in the license generated in the buyer’s AWS License Manager account\.
+  **Contracts DimensionX Display Name** – The customer\-facing name of the dimension that will be displayed on the product detail and procurement pages of the AWS Marketplace website\. This name is also used as the value for `Name` in `Entitlement` in the `Checkoutlicense` API call\. Create a name that is user\-friendly The name's maximum length is 24 characters\. After the listing is public, the value of `Name` can't be changed\.
+  **Contracts DimensionX Description** – The customer\-facing description of a dimension that provides additional information about the dimension for the product, such as the capabilities that the specific dimension provides\. The maximum length for the description is 70 characters\.
+  **Contracts DimensionX Quantity** – This is used to calculate proration in cases of agreement amendments to a product\. This value of this field should be set to 1 for all contract offers\. It should not be edited\. 
+  **Contracts DimensionX **1\-Month Rate**** – The contract rate to be charged for 1\-month of entitlements against this dimension\. For non\-tiered offers, this rate is charged for each unit of the dimension that is procured\. This ﬁeld supports three decimal places\.
+  **Contracts DimensionX **12\-Month Rate**** – The contract rate to be charged for 12 months of entitlements against the dimension\. For non\-tiered offers, this rate is charged for each unit of the dimension that is procured\. This ﬁeld supports three decimal places\. 
+  **Contracts DimensionX **24\-Month Rate**** – The contract rate to be charged for 24 months of entitlements against the dimension\. For non\-tiered offers, this rate is charged for each unit of the dimension that is procured\. This ﬁeld supports three decimal places\.
+  **Contracts DimensionX **36\-Month Rate**** – The contract rate to be charged for 36 months of entitlements against the dimension\. For non\-tiered offers, this rate is charged for each unit of the dimension that is procured\. This ﬁeld supports three decimal places\.


**Example: Data storage application**  

|   | 1\-month price | 12\-month price  | 24\-month price  | P36\-month price  | 
| --- | --- | --- | --- | --- | 
|  Unencrypted data \(GB\)  |  $1\.50/GB  |  $16\.00/GB  |  $30\.00/GB  |  $60\.00/GB  | 
|  Encrypted data \(GB\)  |  $1\.55/GB  |  $16\.60/GB  |  $31\.20/GB  |  $61\.20/GB  | 


**Example: Log monitoring product**  

|   | 1\-month price | 12\-month price  | 24\-month price | 36\-month price | 
| --- | --- | --- | --- | --- | 
|  Basic \(10 hosts monitored, 5 containers monitored\)  |  $100  |  $1000  | $2000  | $4000 | 
|  Standard \(20 hosts monitored, 10 containers monitored\)  |  $200  |  $2000  | $4000  | $8000 | 
|  Pro \(40 hosts monitored, 20 containers monitored\)  |  $400  |  $4000  | $8000  | $16,000 | 
|  Additional hosts monitored per hour  | $10  | $100  |  $200 | $400 | 
|  Additional containers monitored per hour  | $10  | $100  |  $200 | $400 | 

**Note**  
The prices can be for the following durations: 1 month, 12 months, 24 months, or 36 months\. You can choose to offer one or more of these options for your product\. The durations must be the same across each dimension\.   

**Example**  
For example, in a case where you have `ReadOnlyUsers` and `AdminUsers` dimensions, if you offer a yearly price for ReadOnlyUsers, you must offer a yearly price for `AdminUsers`, too\.


## Automatic renewals<a name="ami-contracts-automatic-renewals"></a>

 When a customer purchases your product through AWS Marketplace using Container contracts, they can agree to automatic renewal of the contract terms\. The customer continues to pay for the entitlements every month or for 1, 2, or 3 years\. The customer always has the option to modify the renewal settings\. They can cancel the renewal or renew the contract different quantities and durations\. 

## When a container contract ends<a name="ami-contract-ends"></a>

A container contract product has a contract expiry\. When a contract ends, the following events occur: 

1.  Your container product receives an `entitlement-updated` notification indicating that the buyer's entitlement has changed, and the AWS Marketplace Entitlement Service returns an empty response\. 

1.  You have one hour to meter any remaining usage for the customer\. After this you can no longer send metering records for this customer\. 