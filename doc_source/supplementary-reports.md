# Supplementary reports<a name="supplementary-reports"></a>

AWS Marketplace delivers supplementary reports through the [Seller Delivery Data Feeds Service](data-feed-service.md) to seller\-owned Amazon S3 accounts that are connected to the AWS Marketplace Seller Account ID associated with the AWS Marketplace listings for sellers\. For more information, refer to [Create a destination Amazon S3 bucket](https://docs.aws.amazon.com/marketplace/latest/userguide/data-feed-service.html#data-feed-accessing)\. 

The supplementary reports are published daily at 16:00 UTC if there were new subscribers in the day prior\. These reports cover the previous day from 13:59 UTC through 16:01 UTC of the following day\.

## Agreement details report<a name="agreement-details-report"></a>

The agreement details report helps you support the customers that are on a software as a service \(SaaS\) contract free trial\. The report includes agreement details such as the subscriber name, subscriber ID, offer ID, agreement start, and agreement end date\. 

You only receive this report if relevant information is available\. If you don't receive this report on an occasion when you think that you should, contact the [AWS Marketplace Seller Operations team](https://aws.amazon.com/marketplace/management/contact-us/)\.

You can access this report through Amazon S3 bucket associated with the AWS Marketplace Seller Account ID\.

The following table lists the column names and descriptions for the agreement details report\.


**SaaS contract free trial report data**  

| Name | Description | 
| --- | --- | 
| vendor\_display\_name | The name of the vendor that sold the product\. | 
| vendor\_aws\_account\_id | The identification associated with the vendor that sold the product\. | 
| subscriber\_aws\_account\_id | The identification associated with the AWS account that is subscribed to the product\. | 
| customer\_id | The unique identifier for the software product\. | 
| product\_title | The title of the product\. | 
| offer\_id | The identifier for the offer that the buyer signed\. | 
| offer\_visibility | Indication of whether the offer is a public, private, or enterprise contract offer\. | 
| reseller\_name | The name of the consulting partner reseller\. | 
| reseller\_aws\_account\_id | The unique identifier for the consulting partner reseller\. | 
| agreement\_id | A unique agreement data feed reference for the agreement signed between a proposer and an accepter to start using a product\. | 
| agreement\_acceptance\_date | The date the agreement was accepted\. | 
| agreement\_start\_date | The start date of the agreement\. | 
| agreement\_end\_date | The end date of the agreement\. For metered/pay as go/subscriptions, this is set to 1\-JAN\-9999\. | 
| is\_free\_trial\_offer | A flag indicates if the offer was upgraded to a paid contract\. | 
| total\_contract\_value | The total value of the contract\. | 