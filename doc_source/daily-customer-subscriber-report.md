# Daily customer subscriber report<a name="daily-customer-subscriber-report"></a>

 This report lists data for customers who purchased your products\. This report doesn't specify current or past usage, only that a customer is subscribed to your product\. You only receive this report if relevant information is available\. If you don't receive this report and think that you should have, contact the [AWS Marketplace Seller Operations](https://aws.amazon.com/marketplace/management/contact-us/) team\.

You can access this report at the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/reports/)\. If you are registered for the [AWS Marketplace Commerce Analytics Service](commerce-analytics-service.md), you can also access your reports using the AWS SDK\.

The report has two sections: one for hourly and monthly subscriptions and one for annual subscriptions\. The report includes the list of AWS account IDs for all customers who are subscribed to your products\. 

## Publication schedule<a name="daily-customer-subscriber-report-publication-schedule"></a>

 This report is published daily at 00:00 UTC and covers from 00:00 UTC through 23:59 UTC of the previous day\.

**Topics**
+ [Publication schedule](#daily-customer-subscriber-report-publication-schedule)
+ [Section 1: Hourly and monthly subscriptions](#section-1-hourlymonthly-subscriptions)
+ [Section 2: Variable length subscriptions](#section-2-annual-subscriptions)

## Section 1: Hourly and monthly subscriptions<a name="section-1-hourlymonthly-subscriptions"></a>

 This section lists data for all usage\-based subscriptions as of the previous day at 23:59:59 UTC\. 


|  Column name  |  Description  | 
| --- | --- | 
|  Customer AWS Account Number  |  The account that is subscribed to the product\.  | 
|  Product Title  |  The title of the product\.  | 
|  Product Id  |  A unique identifier for the software product\.  | 
|  Product Code  |  The unique identifier for the software product\. | 
|  Subscription Start Date  |  The start date for the subscription, formatted as YYYY\-MM\-DD\.  | 
|  Offer ID  |  The identifier for the offer that the buyer signed\.  | 
|  Offer Visibility  | Whether the offer is a public, private, or enterprise contract offer\. | 
|  Solution Title  |  The name of the solution\.  | 
|  Solution ID  |  The unique identifier for the solution\.  | 
|  Payer Reference ID  |  A unique identifier that isn't the account ID\. It's associated with the account that fees are billed to\. It helps with tracking usage, revenue, and subscriptions by customers across all of the AWS Marketplace financial reports\.  | 
| Reseller account ID | The unique identifier for the consulting partner reseller\. | 
| Reseller account name | The name of the consulting partner reseller\.  | 

## Section 2: Variable length subscriptions<a name="section-2-annual-subscriptions"></a>

 This section lists data for all fee\-based subscriptions as of the previous day at 23:59:59 UTC\. 


|  Column name  |  Description  | 
| --- | --- | 
|  Customer AWS Account Number  |  The ID of the account that is subscribed to the product\.  | 
|  Product Title  |  The title of the product\.  | 
|  Product Id  |  The unique identifier for the software product\.  | 
|  Product Code  |  A unique identifier for the software product\. This information is also available as part of the Amazon EC2 instance metadata\.  | 
|  Subscription Id  |  The ID for the subscription\.  | 
|  Subscription Quantity  |  The total number of licenses that the customer purchased\.  | 
|  Subscription Type  |  The type of subscription\.  | 
| Subscription Intent | Whether this offer is an upgrade or renewal of an earlier offer\. | 
|  Offer ID  |  The identifier for the offer that the buyer signed\.  | 
|  Subscription Start Date  |  The date when the customer subscribed to the product, formatted as YYYY\-MM\-DD\.  | 
| Previous Offer ID | The ID of the offer that preceded the upgrade or renewal offer, if one exists\.  | 
|  Offer Visibility  |  Whether the offer is a public, private, or enterprise contract offer\.  | 
|  Solution Title  |  The name of the solution\.  | 
|  Solution ID  |  The unique identifier for the solution\.  | 
|  Payer Reference ID  |  A unique identifier that isn't the account ID\. It's associated with the account that fees are billed to\. It helps with tracking usage, revenue, and subscriptions by customers across all of the AWS Marketplace financial reports\. | 
| Reseller account ID | The unique identifier for the consulting partner reseller\. | 
| Reseller account name | The name of the consulting partner reseller\. | 