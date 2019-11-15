# Seller Reports<a name="Reporting"></a>

## Accessing Your Reports<a name="accessing-your-reports"></a>

 AWS Marketplace provides two ways to access your reports:
+ [AWS Marketplace Commerce Analytics Service](commerce-analytics-service.md), which enables you to automatically access the data in your reports through an API interface\. You can automate ingesting your information and download a portion of a report instead of the whole report\. We highly recommend this method for accessing the data in your reports\. 
+ The [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/reports/), which includes reports for previous reporting periods\. 

**Important**  
 We send report notifications to the email address that is associated with the AWS account that you registered with on AWS Marketplace\. 

 You can control access to reports by using AWS Identity and Access Management \(IAM\) permissions\. You automatically receive email notification when new reports are available\. To cancel getting notification emails, contact the [AWS Marketplace Seller Operations](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

 If you use the AWS Commerce Analytics Service to pull report information, you can programmatically access your data\. Available data includes product usage, subscribers, disbursement, and payment information\. The service returns data asynchronously to a file in Amazon Simple Storage Service \(Amazon S3\) rather than directly as with a traditional API\. This is because the data might be large and unbounded\. After the data has been delivered to your Amazon S3 bucket, we send you a notification through Amazon Simple Notification Service \(Amazon SNS\)\. You use the AWS SDKs to communicate with the service\. The SDKs support multiple programming platforms such as \.NET, Java, Ruby, and AWS CLI\. The data comes in a machine\-readable format so that you can import or incorporate the data into your systems\. 

## Report Terms<a name="report-terms"></a>

To read the reports, be familiar with the following terminology\. 

Billed  
AWS customers are billed at the beginning of every month for the metered usage incurred in the previous month\. Customers are also billed immediately when they purchase annual Amazon Machine Image \(AMI\) subscriptions, software as a service \(SaaS\) contracts, or data product subscriptions\.

Payment  
Payment is due immediately for AWS customers who pay with a credit card\. Some customers have other payment arrangements with AWS billing that can change when their payment is due: for instance, customers who are invoiced\.

Disbursement  
Payments from AWS customers are disbursed to you every month of a regular cycle, and the reporting for disbursements is available to you a few days later\.