# Seller reports<a name="Reporting"></a>

AWS Marketplace provides reports that include information about product usage, buyers, billing, and payment information\. Reports are available to all registered AWS Marketplace sellers\. 

Here are some key points about report generation: 
+ Reports are generated daily, weekly, or monthly, depending on the report\. 
+ Reports are generated at 00:00 UTC and cover through 24:00 UTC of the previous day\. 
+ Reports are generated as \.csv files\. 
+ You can configure Amazon SNS to notify you when data is delivered to your encrypted S3 bucket\. After you configure notifications, AWS sends notifications to the email address that is associated with the AWS account that you egistered with on AWS Marketplace\.

  For information on how to configure notifications, see [Getting started with Amazon SNS](https://docs.aws.amazon.com/sns/latest/dg/sns-getting-started.html) in the *Amazon Simple Notification Service Developer Guide\.*

  To cancel getting notification emails, contact the [AWS Marketplace Seller Operations](https://aws.amazon.com/marketplace/management/contact-us/) team\. 
+ To learn about each report, you can download [sample reports](https://s3.amazonaws.com/awsmp-loadforms/AWS+Marketplace+-+Seller+Reporting+Examples.zip)\.

## Accessing reports<a name="reports-accessing"></a>

 AWS Marketplace provides two ways to access your reports:
+ Using an API interface\. The [AWS Marketplace Commerce Analytics Service](commerce-analytics-service.md) enables you to automatically access the data in your reports through an API interface\. You can automate ingesting your information and download a portion of a report instead of the whole report\. The service returns data asynchronously to a file in Amazon Simple Storage Service \(Amazon S3\) rather than directly as with a traditional API\. The data is delivered in a machine\-readable format so that you can import or incorporate the data into your systems\.
+ Using the reports dashboard in the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/reports/)\. This dashboard provides reports for previous reporting periods\. 

 You can control access to reports by using AWS Identity and Access Management \(IAM\) permissions\. 