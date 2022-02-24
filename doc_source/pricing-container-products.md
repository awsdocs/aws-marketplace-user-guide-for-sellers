# Container product pricing<a name="pricing-container-products"></a>

This section outlines the available pricing models for container products\. You can list free products, Bring Your Own License model \(BYOL\) products, and paid products for Amazon Elastic Container Service \(Amazon ECS\), Amazon Elastic Kubernetes Service Amazon EKS, and AWS Fargate\. You can set only one price per product\.

**Note**  
You use the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) to enforce entitlement and meter usage for your paid products\. For per task or per pod pricing, usage is metered automatically by AWS\.

The price you set for a container product applies to all AWS Regions\. Whenever you lower the price for a container product, the new price is implemented for your buyers immediately\. For price increases, existing buyers are notified about the change 90 days before it impacts their billing\. New buyers are billed the new amount\.

## Container pricing models<a name="pricing-models-for-server-products"></a>

AWS Marketplace has multiple pricing models for container products\. 

The following table provides general information about pricing models for container\-based products\.


**Pricing models for container products**  

| Pricing model | Description | 
| --- | --- | 
| Bring Your Own License \(BYOL\) | BYOL is managed outside of AWS Marketplace through an external billing relationship that you maintain with the buyer\. | 
| Monthly | **Fixed monthly price**A fixed monthly price that provides users with unlimited product usage during the following month\.Example: You set the price for your product at $99 per month\. Your product includes three different container images that are deployed using an Amazon ECS task definition\.After a buyer subscribes to your product, they're immediately charged $99, which repeats each month until they cancel the subscription\. The buyer also gets unlimited usage of the product\. The buyer also pays separately for any infrastructure that the tasks run on\. While subscribed, they can access your container images\. They can launch and run any number of containers from those images on Amazon ECS or Amazon EKS in any configuration\.If the buyer cancels their subscription in the middle of a month, they lose access to the Amazon ECR repository where AWS Marketplace stores the container images\. The buyer might have pulled and stored the original images\. However, they can no longer pull new container image versions that you make available through AWS Marketplace\. The buyer is refunded for the unused portion of the final month\. You're paid based on the buyer's usage minus the agreed\-to AWS Marketplace fee\. | 
| Custom metric pricing dimensions |  Custom metered prices based off of dimensions you define \(for example users, nodes, repositories, or GB\), up to 24 dimensions per product\.  Example: Your product charges by users\. You have admin users and regular users, and you define the pricing as $2 for admin users and $1 for regular users\. You can set them up as separate dimensions when listing your product\. You charge by users logged in per day and you meter that usage per day\.  | 
| Per task or per pod hourly price |  **ECS Task or EKS Pod** Per Amazon ECS task or Amazon EKS pod pricing that we measure to the second with the price set per hour\. Example: Your product includes three different container images: a controller node, a worker node, and an analytics node\. Because your product isn't functional or useful without the controller node, you decide that is the image that you want to charge usage for\. You set a price of $6 per hour\. You modify the software in the container image for the controller node to integrate with the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) `RegisterUsage` operation\. This ensures that only buyers with an active subscription can launch and run that container image and that its usage is metered based on how long it runs\. The buyer is charged $6 per hour of usage for each Amazon EKS controller pod running\. If the buyer launches five Amazon EKS controller pods that include the controller node container, they're charged $30 per hour \($6 per pod\)\. The buyer also pays separately for any infrastructure that the pods run on\. For hourly pricing, billing is per\-second with a 1\-minute minimum\. If the customer runs this controller container for 20 minutes and 30 seconds, they're charged `20 x ($6/60) + 30 x ($6/60/60) = $2 + $0.05 = $2.05`\. You're paid based on the buyer's usage minus the agreed\-to AWS Marketplace fee\.  | 
| Hourly/usage with long\-term contract |  A long\-term contract, at a reduced price, paid up front or in regular installments\. A long\-term contract can be added to an existing product that has custom metered pricing, or per task and per pod pricing\. Buyers pay the metered prices when they consume more than what they purchased in the long term contract\. Example: For metered pricing models, you can add a long\-term contract price for buyers to get a discount for committing upfront\. Say that you normally charge $1 per some unit consumed\. A buyer using 1 unit per hour would pay $8760 per year \(`365 days x 24 hours x $1 per hour`\)\. You could enable a contract that enables the buyer to use 1 unit per hour for those 365 days at half that price \($4380\)\. In this case, the buyer commits to pay upfront for the one\-year contract, and the price drops from $1 per unit to $0\.5 per unit\. You could also enable the buyer to purchase multiple of these contracts\. If the quantity that is metered showed that the buyer consumed 10 units in an hour, and they had two contracts, then 2 units will be included in the 2 contracts\. The 8 additional units would be billed at the regular $1 per hour, for a total of $8 in that hour\. For the per task or per pod example, you can also add a long\-term contract price for buyers to get a discount for committing upfront\. If you normally charge $6 per pod, you could set a long\-term contract duration of 365 days with a price of $13,140 \(`365 days x 24 hours x $3 per pod per hour`\)\. One contract would then entitle the customer to 1 pod per hour during those 365 days\. Customers can choose to purchase multiple contracts\. For example, a customer can purchase two contracts which entitles them to 2 pods per hour\. If the customer runs more pods per hour than the entitled contracts, then excess pods will be billed at your normal hourly price\. In both cases, buyers that purchase long\-term contracts will be billed upfront, either as a one\-time payment or regularly scheduled future payments\. Buyers will also be billed for any additional usage above their contract at the metered rate\.   | 
| Container contract pricing |  **AMI with contract pricing** – A Container\-based product that the buyer pays an upfront fee for\.  | 

## Contract pricing for container products<a name="container-contracts"></a>

For container\-based products with contract pricing, AWS Marketplace bills your customers upfront or by the payment schedule that you define, based on the contract between you and your customer\. After that point, they're entitled to use those resources\. 

To set your pricing, choose one or more contract durations that you offer customers\. You can enter different prices for each contract duration\. Your options are 1\-month, 12\-months, 24\-month, and 36\-month durations\. For private offers, you can specify a custom duration in months \(up to 60 months\)\. 

Choose the category that best describes your product’s pricing\. The pricing category appears to customers on the AWS Marketplace website\. You can choose from **Bandwidth** \(GB/s, MB/s\), **Data** \(GB, MB, TB\), **Hosts**, **Requests**, **Tiers**, or **Users**\. If none of the predefined categories fit your needs, you can choose the more generic **Units** category\. 

The offer allows for up to 24 dimensions to be added to it\. Each dimension requires the following data:
+ **Contracts Category** – The contract category is used to measure or meter your product if the product supports consumption based metering on top of contract pricing\. For contract products with no consumption based pricing, you can choose a category which most closely resembles the category of dimension in the contract\. If no values resemble the units for the dimension in the contract, choose `Units`\. 
+ **Contracts Unit** – The contract unit is used along with category for metering if the product supports consumption based metering\. Choose one of the available values for the units that closely matches your dimensions based on the category selected\.
+ **Contracts Dimension Allow Multiple Purchases** – This field is used to indicate whether an offer is a tiered pricing offer or a non\-tiered offer which allows for purchase of multiple dimensions\. 

  **Tiered offer** – Allows the buyer to subscribe to only one of the available dimensions in the offer\. Dimensions in a tiered offer don't have the concept of quantities\. Signing a contract with a specific dimension essentially indicates that the buyer has chosen the specific feature indicated by that dimension\.

  **Non\-tiered offer** – Allows the customer to procure more than one dimensions as part of the contract and allows them to procure multiple units of each such dimension\.

  Setting a value of *true* for this field indicates that the offer is a non\-tiered offer\. Setting a value of *false* for this field indicates that the offer is a tiered offer\.

When using the Product Load Form \(PLF\) to create the contracts for your Container product, you must define the following fields for your pricing dimensions:
+  **Contracts DimensionX API Name** – The name that should appear in the license generated in the buyer’s AWS License Manager account\. This name is also used as the value for `Name` in `Entitlement` in the `Checkoutlicense` API call\.
+  **Contracts DimensionX Display Name** – The customer\-facing name of the dimension that will be displayed on the product detail and procurement pages of the AWS Marketplace website\. Create a name that is user\-friendly The name's maximum length is 24 characters\. After the listing is public, the value of `Name` can't be changed\.
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


### Automatic renewals<a name="ami-contracts-automatic-renewals"></a>

 When a customer purchases your product through AWS Marketplace using Container contracts, they can agree to automatic renewal of the contract terms\. The customer continues to pay for the entitlements every month or for 1, 2, or 3 years\. The customer always has the option to modify the renewal settings\. They can cancel the renewal or renew the contract different quantities and durations\. 

### When a container contract ends<a name="ami-contract-ends"></a>

A container contract product has a contract expiry\. When a contract ends, the following events occur: 

1.  Your container product receives an `entitlement-updated` notification indicating that the buyer's entitlement has changed, and the AWS Marketplace Entitlement Service returns an empty response\. 

1.  You have one hour to meter any remaining usage for the customer\. After this you can no longer send metering records for this customer\. 