# Daily Customer Subscriber Report<a name="daily-customer-subscriber-report"></a>

 This report gives sellers a list of AWS Account IDs for all customers currently subscribed to their products\. 

## Publication Schedule<a name="publication-schedule-1"></a>

 Daily, by 5:00 PM Pacific Time\. 

## Section 1: Hourly/Monthly subscriptions<a name="section-1-hourlymonthly-subscriptions"></a>

### Data Coverage Period<a name="data-coverage-period-6"></a>

 Includes all usage\-based subscriptions as of the previous day at 23:59:59 UTC\. 


|  **Column Name**  |  **Description**  | 
| --- | --- | 
|  Customer AWS Account Number  |  The AWS account number­­ associated with the AWS account which is subscribed to the to the listing\. This is a 12\-digit number, represented by 3 sets of 4 numbers, separated by hyphens, e\.g\. 1234\-5678\-9012  | 
|  Product Title  |  The title of the product  | 
|  Product Id  |  A unique identifier representing the individual software product  | 
|  Product Code  |  A unique identifier representing the individual software product, which is also available in EC2 Instance Metadata  | 
|  Subscription Start Date  |  The date when the customer subscribed to the listing, formatted as YYYY\-MM\-DD  | 
|  Offer ID  |  The identifier for the offer the subscriber signed  | 
|  Offer Visibility  |  Indicates the offer to be a public, private, or enterprise contract offer  | 
|  Solution Title  |  The name of the solution  | 
|  Solution ID  |  The unique identifier for the solution  | 
|  Payer Reference ID  |  A unique identifier \(not an AWS account number\) associated with the AWS account to which fees are billed\. These help with tracking usage, revenue, and subscriptions by customers\.  | 

## Section 2: Annual subscriptions<a name="section-2-annual-subscriptions"></a>

### Data Coverage Period<a name="data-coverage-period-7"></a>

 Includes all fee\-based subscriptions as of the previous day at 23:59:59 UTC\. 


|  **Column Name**  |  **Description**  | 
| --- | --- | 
|  Customer AWS Account Number  |  The AWS account number­­ associated with the AWS account which is subscribed to the to the listing\. This is a 12\-digit number, represented by 3 sets of 4 numbers, separated by hyphens, e\.g\. 1234\-5678\-9012  | 
|  Product Title  |  The title of the product  | 
|  Product Id  |  A unique identifier representing the individual software product  | 
|  Product Code  |  A unique identifier representing the individual software product, which is also available in EC2 Instance Metadata  | 
|  Annual Subscription Id  |  The ID of the annual subscription  | 
|  Annual Subscription Quantity  |  The total number of licenses the customer specified as part of the annual purchase  | 
|  Annual Subscription Type  |  The type of annual subscription  | 
|  Subscription Start Date  |  The date when the customer subscribed to the listing, formatted as YYYY\-MM\-DD  | 
|  Offer ID  |  The identifier for the offer the subscriber signed  | 
|  Offer Visibility  |  Indicates the offer to be a public, private, or enterprise contract offer  | 
|  Solution Title  |  The name of the solution  | 
|  Solution ID  |  The unique identifier for the solution  | 
|  Payer Reference ID  |  A unique identifier \(not an AWS account number\) associated with the AWS account to which fees are billed\. These help with tracking usage, revenue, and subscriptions by customers\.  | 