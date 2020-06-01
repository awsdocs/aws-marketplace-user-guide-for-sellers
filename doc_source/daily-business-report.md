# Daily business report<a name="daily-business-report"></a>

The daily business report helps you understand how AWS customers are using your products on a daily basis and the estimated revenue from that usage\. You only receive this report if relevant information is available\. If you don't receive this report and think that you should have received it, contact the [AWS Marketplace Seller Operations](https://aws.amazon.com/marketplace/management/contact-us/) team\.

You can access this report at the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/reports/)\. If you are registered for the [AWS Marketplace Commerce Analytics Service](commerce-analytics-service.md), you can also access your reports using the AWS SDK\.

You can use a unique identifier for each customer to identify customers over time and across reports\. The identifier enables you to track customer usage patterns so that you can estimate customer spend, gain insights into free trial usage, and annual usage trends\.

## Publication schedule<a name="publication-schedule"></a>

 This report is published daily at 00:00 UTC and covers from 00:00 UTC through 23:59 UTC of the previous day\. Any exceptions to the schedule are noted at the introduction of the daily business report section\.

**Topics**
+ [Publication schedule](#publication-schedule)
+ [Section 1: Usage by instance type](#section-1-usage-by-instance-type)
+ [Section 2: Fees](#section-2-fees)
+ [Section 3: Free trial conversions](#section-3-free-trial-conversions)
+ [Section 4: New instances](#section-4-new-instances)
+ [Section 5: New product subscribers](#section-5-new-product-subscribers)
+ [Section 6: Canceled product subscribers](#section-6-canceled-product-subscribers)

## Section 1: Usage by instance type<a name="section-1-usage-by-instance-type"></a>

 This section lists data with a row for each instance type that the customer uses\. For instance, when the customer uses a product on one instance type and the same product on a different instance type, the report includes a row for each of the two instance types\. 


|  Column name  |  Description  | 
| --- | --- | 
|  Customer Reference ID  |  A unique identifier that isn't the account ID\. It helps track usage, revenue, and subscriptions by customers\.  | 
|  User’s State  |  The billing address state that is associated with the account that is subscribed to the product\.  | 
|  User’s Country  |  The two\-character country code that is associated with the account that is subscribed to the product\. This report uses ISO 3166\-1 alpha\-2 standard\.  | 
|  Product Title  |  The title of the product\.  | 
|  Product Code  |  The unique identifier for the product\.  | 
|  Instance Type  |  The instance type associated with the product usage: for example, t2\.micro\.  | 
|  Usage Units  |  The number of units of usage that the customer used during the reporting period\.  | 
|  Usage Unit Type  |  The unit of measurement that meters the customer's usage\. For example, hours or days\.  | 
|  Offering Description  |  The description for product offering\. For example, the product is offered for hourly usage, free trial usage, or annual usage\.  | 
|  Estimated Revenue  |  The estimated revenue from the product usage\. The billing is finalized at the end of the month\.  | 
|  Currency  |  The currency of the transaction\. For example, if the transaction is in US dollars, the entry is USD\.  | 
|  Offer ID  |  The identifier for the offer that the buyer signed\.  | 
|  Offer Visibility  |  Whether the offer is a public, private, or enterprise contract offer\.  | 
|  Customer AWS Account Number  |  The ID of the account that the charges are billed to\.  | 
|  Customer Country  |  The two\-character country code that is associated with the account that the charges are billed to\.  | 
|  Customer State  |  The billing address state that is associated with the account that the charges are billed to\. This report uses ISO 3166\-1 alpha\-2 standard\.  | 
|  Customer City  |  The billing address city that is associated with the account that charges are billed to\. | 
|  Customer Zip Code  | The billing address zip code that is associated with the account that the charges are billed to\.  | 
|  Customer Email Domain  |  The email domain that is associated with the account that the charges are billed to\. For example, if the email address is liu\-jie@example\.com, the entry is example\.com\. | 
|  Solution Title  |  The name of the solution\.  | 
|  Solution ID  |  The unique identifier for the solution\.  | 
|  Payer Reference ID  |  A unique identifier that isn't the account ID\. It's associated with the account that fees are billed to\. It helps with tracking usage, revenue, and subscriptions by customers across all of the AWS Marketplace financial reports\.  | 
|  Payer Address ID  |  A unique identifier that represents the customer's address\. | 

## Section 2: Fees<a name="section-2-fees"></a>

 This section includes fee\-based transactions that are associated with products: for example, annual, monthly, SaaS contracts product fees, and data product subscription fees\. The data in this section covers the 24\-hour period 72 hours before the time that the report is generated\. For example, if the report is generated on May 24, the data covers the 24\-hour period for May 21\. 


|  Column name  |  Description  | 
| --- | --- | 
|  Customer Reference ID  |  A unique identifier that isn't the account ID\. It helps track usage, revenue, and subscriptions by customers\. | 
|  User’s State  |  The billing address state that is associated with the account that is subscribed to the product\. | 
|  User’s Country  |  The two\-character country code that is associated with the account that is subscribed to the product\. This report uses ISO 3166\-1 alpha\-2 standard\. | 
|  Product Title  |  The title of the product\.  | 
|  Product Code  |  The unique identifier for the product\.  | 
|  Amount  |  The usage fee\. If there is a refund, this value is negative\. If this entry is for an AWS Marketplace SaaS contract, the amount represents the fee for the dimension, not the entire contract\.  | 
|  Currency  |  The currency of the transaction\. For example, if the transaction is in US dollars, the entry is USD\.  | 
|  Fee Description  |  The reason for the fee: for example, monthly fee, annual fee, or refund\.  | 
|  Customer AWS Account Number  |  The ID of the account that the charges are billed to\.  | 
|  Customer Country  |  The two\-character country code that is associated with the account that the charges are billed to\. This report uses ISO 3166\-1 alpha\-2 standard\.  | 
|  Customer State  |  The billing address state that is associated with the account that the charges are billed to\. | 
|  Customer City  |  The billing address city that is associated with the account that charges are billed to\. | 
|  Customer Zip Code  |  The billing address zip code that is associated with the account that the charges are billed to\.  | 
|  Customer Email Domain  |  The email domain that is associated with the account that the charges are billed to\. For example, if the email address is liu\-jie@example\.com, the entry is example\.com\. | 
|  Start Date  |  The start date for an AWS Marketplace SaaS contract or data product subscription\.  | 
|  End Date  |  The end date for an AWS Marketplace SaaS contract or data product subscription\.  | 
|  Quantity  |  The number of units for a dimension that the contract specifies\.  | 
|  Dimension  |  The dimension that the contract specifies\.  | 
|  Solution Title  |  The name of the solution\.  | 
|  Solution ID  |  The unique identifier for the solution\. | 
|  Payer Reference ID  |  A unique identifier that isn't the account ID\. It's associated with the account that fees are billed to\. It helps with tracking usage, revenue, and subscriptions by customers across all of the AWS Marketplace financial reports\.  | 
|  Payer Address ID  |  A unique identifier that represents the customer's address\. | 

## Section 3: Free trial conversions<a name="section-3-free-trial-conversions"></a>

 This section lists data for free trial starts, conversions and cancellations, and covers the previous 24\-hour period\. 


|  Column name  |  Description  | 
| --- | --- | 
|  Product Title  |  The title of the product\.  | 
|  Product Code  |  The unique identifier representing the product\.  | 
|  New Free Trials  |  The number of new free trials that are initiated in the reporting period\.  | 
|  Total Current Free Trials  |  The total number of active free trial subscriptions\.  | 
|  Converted Free Trials  |  The total number of subscriptions that moved from free trial to paid usage during the reporting period\.  | 
|  Non\-Converted Free Trials  |  The total number of subscriptions that ended the free trial and didn't convert to paid usage\.  | 
|  Solution Title  |  The name of the solution\.  | 
|  Solution ID  |  The unique identifier for the solution\. | 

## Section 4: New instances<a name="section-4-new-instances"></a>

 This section lists data for new EC2 instance and instances types, and covers the previous 24\-hour period\. 


|  Column name  |  Description  | 
| --- | --- | 
|  Customer Reference ID  |  A unique identifier that isn't the account ID\. It helps track usage, revenue, and subscriptions by customers\. | 
|  User’s State  | The billing address state that is associated with the account that is subscribed to the product\. | 
|  User’s Country  |  The two\-character country code that is associated with the account that is subscribed to the product\. This report uses ISO 3166\-1 alpha\-2 standard\. | 
|  Product Title  |  The title of the product\.  | 
|  Product Code  |  The unique identifier for the product\.  | 
|  Type  |  The Amazon EC2 instance type\.  | 
|  Count  |  The number of EC2 instances\.  | 
|  Customer AWS Account Number  |  The ID of the account that the charges are billed to\.  | 
|  Customer Country  |  The two\-character country code that is associated with the account that the charges are billed to\. This report uses ISO 3166\-1 alpha\-2 standard\.  | 
|  Customer State  |  The billing address state that is associated with the account that the charges are billed to\. | 
|  Customer City  |  The billing address city that is associated with the account that charges are billed to\. | 
|  Customer Zip Code  | The billing address zip code that is associated with the account that the charges are billed to\.  | 
|  Customer Email Domain  |  The email domain that is associated with the account that the charges are billed to\. For example, if the email address is liu\-jie@example\.com, the entry is example\.com\. | 
|  Solution Title  |  The name of the solution\.  | 
|  Solution ID  |  The unique identifier for the solution\. | 
|  Payer Reference ID  |  A unique identifier that isn't the account ID\. It's associated with the account that fees are billed to\. It helps with tracking usage, revenue, and subscriptions by customers across all of the AWS Marketplace financial reports\.  | 
|  Payer Address ID  |  A unique identifier that represents the customer's address\. | 

## Section 5: New product subscribers<a name="section-5-new-product-subscribers"></a>

 This section lists data for new buyers, and covers the previous 24\-hour period\. 


|  Column name  |  Description  | 
| --- | --- | 
|  Customer Reference ID  |  A unique identifier that isn't the account ID\. It helps track usage, revenue, and subscriptions by customers\. | 
|  User’s State  |  The billing address state that is associated with the account that is subscribed to the product\. | 
|  User’s Country  |  The two\-character country code that is associated with the account subscribed to the product\. This report uses ISO 3166\-1 alpha\-2 standard\. | 
|  Product Title  |  The title of the product\.  | 
|  Product Code  |  The unique identifier for the product\.  | 
|  Offer ID  |  The identifier for the offer the buyer signed\. | 
|  Offer Visibility  |  Whether the offer is a public, private, or enterprise contract offer\. | 
|  Customer Country  |  The two\-character country code that is associated with the account that the charges are billed to\. This report uses ISO 3166\-1 alpha\-2 standard\.  | 
|  Customer State  |  The billing address state that is associated with the account that the charges are billed to\. | 
|  Customer City  | The billing address city that is associated with the account that charges are billed to\. | 
|  Customer Zip Code  |  The billing address zip code that is associated with the account that the charges are billed to\.  | 
|  Customer Email Domain  |  The email domain that is associated with the account that the charges are billed to\. For example, if the email address is liu\-jie@example\.com, the entry is example\.com\. | 
|  Solution Title  |  The name of the solution\.  | 
|  Solution ID  |  The unique identifier for the solution\. | 
|  Payer Reference ID  |  A unique identifier that isn't the account\. It's associated with the account that fees are billed to\. It helps with tracking usage, revenue, and subscriptions by customers across all of the AWS Marketplace financial reports\.  | 
|  Payer Address ID  |  A unique identifier that represents the customer's address\. | 

## Section 6: Canceled product subscribers<a name="section-6-canceled-product-subscribers"></a>

 This section lists data for buyer cancellations, and covers the previous 24\-hour period\. 


|  Column name  |  Description  | 
| --- | --- | 
|  Customer Reference ID  |  A unique identifier that isn't the account ID\. It helps track usage, revenue, and subscriptions by customers\. | 
|  User’s State  |  The billing address state that is associated with the account that is subscribed to the product\. | 
|  User’s Country  |  The two\-character country code that is associated with the account that is subscribed to the product\. This report uses ISO 3166\-1 alpha\-2 standard\. | 
|  Product Title  |  The title of the product\.  | 
|  Product Code  |  The unique identifier for the product\.  | 
|  Subscribed Date  |  The date when the subscription started\.  | 
|  Offer ID  |  The identifier for the offer that the buyer signed\. | 
|  Offer Visibility  | Whether the offer is a public, private, or enterprise contract offer\. | 
|  Customer AWS Account Number  |  The ID of the account that the charges are billed to\.  | 
|  Customer Country  |  The two\-character country code that is associated with the account that the charges are billed to\. This report uses ISO 3166\-1 alpha\-2 standard\.  | 
|  Customer State  |  The billing address state that is associated with the account that the charges are billed to\. | 
|  Customer City  |  The billing address city that is associated with the account that charges are billed to\. | 
|  Customer Zip Code  |  The billing address zip code that is associated with the account that the charges are billed to\.  | 
|  Customer Email Domain  |  The email domain that is associated with the account that the charges are billed to\. For example, if the email address is liu\-jie@example\.com, the entry is example\.com\. | 
|  Solution Title  |  The name of the solution\.  | 
|  Solution ID  |  The unique identifier for the solution\. | 
|  Payer Reference ID  |  A unique identifier that isn't the account ID\. It's associated with the account that fees are billed to\. It helps with tracking usage, revenue, and subscriptions by customers across all of the AWS Marketplace financial reports\.  | 
|  Payer Address ID  |  A unique identifier that represents the customer's address\. | 