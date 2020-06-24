# Monthly billed revenue report<a name="monthly-billed-revenue-report"></a>

 The monthly billed revenue report provides you authoritative information about billed revenue every month for accounting and other financial reporting purposes\. This report shows the total amounts that AWS bills to customers for hourly, annual, or monthly usage of your products\. The report has four sections: billed amounts for hourly usage and monthly fees, variable\-length subscriptions, field demonstration usage, and flexible payments\. 

**Important**  
The amounts in this report reflect only revenue that we billed to customers, not amounts that we collected\.

 This report is available on the AWS Marketplace Management Portal under the **Reports** tab\. If you're enrolled in the AWS Marketplace commerce analytics service, you can use API calls to pull down sections of this report\. For more information, see [AWS Marketplace Commerce Analytics Service](commerce-analytics-service.md)\. 

## Publication schedule<a name="publication-schedule-2"></a>

This report is published monthly on the fifteenth day of each month at 00:00 UTC\. The report covers the previous calendar month from the first day of the month at 00:00 UTC through the last day of the month at 23:59 UTC\. For example, the report that is published on May 15 covers from April 1 at 00:00 UTC through April 30 at 23:59 UTC\.

**Topics**
+ [Publication schedule](#publication-schedule-2)
+ [Section 1: Billing and revenue data](#section-1-billing-and-revenue-data)
+ [Section 2: Variable length subscriptions](#section-2-annual-subscriptions-1)
+ [Section 3: AWS field demonstration usage](#section-3-aws-field-demonstration-usage)
+ [Section 4: Contracts with flexible payment schedule](#section-4-contracts-with-flexible-payments)

## Section 1: Billing and revenue data<a name="section-1-billing-and-revenue-data"></a>

 This section lists data for usage billing, refunds, fees, and US sales and use tax that is collected\.


|  Column name  |  Description  | 
| --- | --- | 
|  Customer Reference ID  |  A unique identifier that isn't the account ID\. It helps track usage, revenue, and subscriptions by customers\. | 
|  Country  | The two\-character country code that is associated with the account that the charges are billed to\. This report uses ISO 3166\-1 alpha\-2 standard\.  | 
|  State  |  The billing address state that is associated with the account that the charges are billed to\. | 
|  City  |  The billing address city that is associated with the account that charges are billed to\. | 
|  Zip Code  |  The billing address postal code that is associated with the account that the charges are billed to\. | 
|  Product Title  |  The title of the product\.  | 
|  Product Code  |  The unique identifier for the product\.  | 
|  Customer Billed Amount  |  The amount that is billed to the customer for the usage or monthly fees of the product\.  | 
|  AWS Listing Fee  |  The AWS Marketplace fee amount to be deducted from the billed amount\.  | 
|  Refunds Amount  |  The total amount of the subscription cost refunded to customers if any refunds were processed during the data coverage period\.  | 
|  AWS Fee Refund  |  The portion of the AWS Marketplace fee refunded if any refunds were processed during the data coverage period\.  | 
|  Cost  |  The cost of goods to a reseller: for example, what a reseller pays you when they sell your product\.  | 
|  Partner Revenue Amount  | The total amount billed for the transaction, net of AWS Marketplace fees, refunds, and US sales and use tax\.  | 
|  Currency  |  The currency of the transaction\. For example, if the transaction is in US dollars, the entry is USD\.  | 
|  Transaction Reference ID  |  A unique identifier for the transaction that helps you correlate transactions across AWS Marketplace reports\.  | 
|  U\.S\. Sales Tax Customer Billed Amount  | The total amount of US sales and use tax that is billed for this transaction on behalf of the Seller\. \(That is, related records in US Sales and Tax reports show “tax liable party” == “SELLER”\.\)  | 
|  U\.S\. Sales Tax Refunds Amount  | The total amount of US sales and use tax that is refunded for this transaction if a refund was processed, when such taxes were collected on behalf of the Seller\. \(That is, related records in US Sales and Tax reports show “tax liable party” == “SELLER”\.\) | 
|  Offer ID  |  The identifier for the offer that the buyer signed\. | 
|  Offer Visibility  |  Whether the offer is a public, private, or enterprise contract offer\. | 
|  Customer AWS Account Number  | The ID of the account that the charges are billed to\.  | 
|  Customer Email Domain  |  The email domain that is associated with the account that the charges are billed to\. For example, if the email address is liu\-jie@example\.com, the entry is example\.com\. | 
|  Opportunity Name  |  The unique identifier for a registered opportunity\.  | 
|  Opportunity Description  |  The metadata for the registered opportunity\.  | 
|  Solution Title  |  The name of the solution\.  | 
|  Solution ID  |  The unique identifier for the solution\.  | 
|  Payer Reference ID  |  A unique identifier that isn't the account ID\. It's associated with the account that fees are billed to\. It helps with tracking usage, revenue, and subscriptions by customers across all of the AWS Marketplace financial reports\.  | 
|  Payer Address ID  |  A unique identifier that represents the customer's address\. | 

## Section 2: Variable length subscriptions<a name="section-2-annual-subscriptions-1"></a>

 This section lists data for fee\-based charges\.


|  Column name  |  Description  | 
| --- | --- | 
|  Customer Reference ID  |  A unique identifier that isn't the account ID\. It helps track usage, revenue, and subscriptions by customers\. | 
|  Country  |  The two\-character country code that is associated with the account that the charges are billed to\. This report uses ISO 3166\-1 alpha\-2 standard\.  | 
|  State  |  The billing address state that is associated with the account that the charges are billed to\. | 
|  City  |  The billing address city that is associated with the account that charges are billed to\. | 
|  Zip Code  | The billing address zip code that is associated with the account that the charges are billed to\. | 
|  Product Title  |  The title of the product\.  | 
|  Product Code  | The unique identifier for the product\.  | 
|  Subscription Quantity  |  The number of total licenses that is specified as part of the variable\-length subscription purchase\.  | 
|  Subscription Start Date  |  The start date of the variable\-length subscription purchase\.  | 
|  Subscription End Date  |  The end date of the variable\-length subscription purchase\.  | 
|  Subscription Instance Type  |  The instance type that is associated with the variable\-length subscription purchase\.  | 
|  Customer Billed Amount  |  The amount that is billed for the usage, monthly fees, or both\.  | 
|  AWS Listing Fee  |  The AWS Marketplace fee amount that is deducted from the billed amount\.  | 
|  Refunds Amount  |  The total amount refunded to customers if any refunds were processed during the data coverage period\.  | 
|  AWS Fee Refund  |  The portion of the AWS Marketplace fee refunded if any refunds were processed during the data coverage period\.  | 
|  Cost  |  The cost of goods to a reseller: for example, what a reseller pays you when they sell your product\. | 
|  Partner Revenue Amount  |  The total amount that is billed for this transaction, net of AWS Marketplace fees, refunds, and US sales and use tax\.  | 
|  Currency  |  The currency of the transaction\. For example, if the transaction is in US dollars, the entry is USD\. | 
|  Transaction Reference ID  |  A unique identifier for the transaction that helps you correlate transactions across AWS Marketplace reports\.  | 
|  U\.S\. Sales Tax Customer Billed Amount  |  The total amount of US sales and use tax that is billed for this transaction on behalf of the Seller\. \(That is, related records in US Sales and Tax reports show “tax liable party” == “SELLER”\.\) | 
|  U\.S\. Sales Tax Refunds Amount  |  The total amount of US sales and use tax that is refunded for this transaction if a refund was processed, when such taxes were collected on behalf of the Seller\. \(That is, related records in US Sales and Tax reports show “tax liable party” == “SELLER”\.\) | 
|  Customer AWS Account Number  | The ID of the account that the charges are billed to\.  | 
|  Customer Email Domain  |  The email domain that is associated with the account that the charges are billed to\. For example, if the email address is liu\-jie@example\.com, the entry is example\.com\. | 
|  Offer ID  |  The identifier for the offer that the buyer signed\. | 
|  Offer Visibility  |  Whether the offer is a public, private, or enterprise contract offer\. | 
|  Contract Start Date  |  The start date for an AWS Marketplace SaaS contract\.  | 
|  Contract End Date  |  The end date for an AWS Marketplace SaaS contract\.  | 
|  Opportunity Name  |  The unique identifier for a registered opportunity\.  | 
|  Opportunity Description  |  The metadata for the registered opportunity\.  | 
|  Solution Title  |  The name of the solution\.  | 
|  Solution ID  |  The unique identifier for the solution\.  | 
|  Payer Reference ID  |  A unique identifier that isn't the account ID\. It's associated with the account that fees are billed to\. It helps with tracking usage, revenue, and subscriptions by customers across all of the AWS Marketplace financial reports\. | 
|  Payer Address ID  |  A unique identifier that represents the customer's address\. | 

## Section 3: AWS field demonstration usage<a name="section-3-aws-field-demonstration-usage"></a>

 The section lists data for AWS [field demonstration usage](field-demonstration-program.md) of your product\. You can configure your product to allow us to demonstrate your product to potential customers\. Any usage from the demonstrations is listed here\.


|  Column name  |  Description  | 
| --- | --- | 
|  Product Title  |  The title of the product\.  | 
|  Product Code  |  The unique identifier for the product\.  | 
|  Instance Type  |  The Amazon EC2 instance type that is associated with the field demonstration\.  | 
|  Usage Units  |  The number of units of usage that is associated with the product\.  | 
|  Usage Unit Types  |  The usage units that are associated with the usage unit count: for example, hours\.  | 

## Section 4: Contracts with flexible payment schedule<a name="section-4-contracts-with-flexible-payments"></a>

 This section lists data for all contracts that you created with a flexible payment schedule in the previous reporting period\. 


|  Column name  |  Description  | 
| --- | --- | 
|  Customer AWS Account Number  |  The ID of the payer account that the charges are billed to\. | 
|  Customer Country  |  The two\-character country code that is associated with the payer account that the charges are billed to\. This report uses ISO 3166\-1 alpha\-2 standard\.  | 
|  Customer State  |  The billing address state that is associated with the payer account that the charges are billed to\. | 
|  Customer City  |  The billing address city that is associated with the payer account that charges are billed to\. | 
|  Customer ZIP Code  | The billing address zip code that is associated with the payer account that the charges are billed to\.  | 
|  Customer Email Domain  | The email domain that is associated with the payer account that the charges are billed to\. For example, if the email address is liu\-jie@example\.com, the entry is example\.com\. | 
|  User Reference ID  |  The account of the payer account that the charges are billed to\.  | 
|  User AWS Account Number  |  The ID of the account that subscribed to the product\.  | 
|  Product ID  |  The unique identifier for the product\.  | 
|  Product Title  |  The title of the product\.  | 
|  Product Type  |  The type of product\.  | 
|  AWS Marketplace Offer ID  | The identifier for the offer that the buyer signed\. | 
|  Contract Create Date  |  The contract creation date, which is the date that an account subscribes to the offer\.  | 
|  Contract Expiration Date  |  The date when the contract expires\.  | 
|  Total Contract Value \(USD\)  |  The total value of the contract in USD\.  | 
|  \# of Payments  |  The number of payments that are scheduled for the contract\.  | 
|  Invoice Date  |  The date the invoice is created\.  | 
|  Invoice Amount \(USD\)  |  The amount that is billed on the invoice in USD\.  | 
|  Payer Reference ID  |  A unique identifier that isn't the account ID\. It's associated with the account that fees are billed to\. It helps with tracking usage, revenue, and subscriptions by customers across all of the AWS Marketplace financial reports\.  | 