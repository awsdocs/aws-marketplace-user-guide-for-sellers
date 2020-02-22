# Seller Reports and Data Feed<a name="reports-and-data-feed"></a>

 AWS Marketplace gives you three tools to gather information about your product sales, customers, financials, and customer usage\.
+  A group of reports that are automatically created and available through the AWS Marketplace Management Portal 
+  An API that enables you to pull down sections of those reports 
+  A data feed that provides additional customer information and can be used to identify customer information for transactions listed in the reports 

 Reports are available to all registered AWS Marketplace sellers\. To access the API, you must enroll in the [AWS Marketplace Commerce Analytics Service](commerce-analytics-service.md)\. To have access to the data feed, you must enroll in the [AWS Marketplace Enhanced Data Sharing Program](enhanced-data-sharing-program.md) and add additional configuration information to your account\. 

 The reports are released on a regular cadence \(daily, weekly, or monthly\) with each report having fixed data fields\. The reports are delivered as CSV\-formatted files, and you receive email notification when new reports are available\. You can use key fields to track entries across the various reports from purchase to payment\. You can also use API calls to retrieve sections of reports as a data set that is delivered to an Amazon S3 bucket that you configure\. Notification of data delivery into your S3 bucket comes as an Amazon SNS notification\. The data feed function enables you to receive a CSV\-formatted file each day with more detailed information about your customer\. The information is potentially sensitive, so the S3 bucket that the file is delivered to must be encrypted\. Amazon SNS is also used to notify you when data is delivered to your encrypted S3 bucket\.

Here are some key points about reports: 
+  There are seven reports \(eight if you're participating in the [AWS Marketplace Enhanced Data Sharing Program](enhanced-data-sharing-program.md)\)\. 
+  The reports are generated daily, weekly, or monthly, depending on the report\. 
+  All reports are generated at 00:00 UTC and cover through 24:00 UTC of the previous day\. 
+  All reports are generated as \.csv files\. 
+  You can download a set of sample reports: [AWS Marketplace \- Seller Reporting Examples\.zip](https://s3.amazonaws.com/awsmp-loadforms/AWS+Marketplace+-+Seller+Reporting+Examples.zip)\. 

 AWS Marketplace provides as much data as possible while adhering to the Amazon standards and tenets for protecting customer data\. To protect customer privacy and trust, in most cases we don't share personally identifiable information \(PII\)\. 

## AWS Marketplace Enhanced Data Sharing<a name="reporting-enhanced-data-sharing"></a>

 If you participate in the [AWS Marketplace Enhanced Data Sharing Program](enhanced-data-sharing-program.md), we share certain entity\-level information about your customers\. This information enables you to match specific sales to customers so that you can compensate your staff\. You can also configure your account in AWS Marketplace Management Portal to receive the data feed\. The data feed provides additional details about your customers\. 

 If you participate in the [AWS Marketplace Enhanced Data Sharing Program](enhanced-data-sharing-program.md), you also have access to the AWS Marketplace sales compensation report\. This report lists customer information so that you can match sales of your product to the salesperson responsible for the sale\. You can use this information only to help compensate your field sales team\. Here is some of the data included in the report: 
+  The customer's email domain 
+  The customer's account ID 
+  The customer's location 

**Important**  
By participating in the enhanced data sharing program, you agree to use enhanced data sharing program data according to the terms outlined in[Use of the Data](enhanced-data-sharing-program.md#use-of-the-data)\. 

## List of Reports<a name="report-list"></a>

 The following is a list of reports and their purpose\. We recommend that you download and view the [sample reports](https://s3.amazonaws.com/awsmp-loadforms/AWS+Marketplace+-+Seller+Reporting+Examples.zip) to become more familiar with each report\. 

Daily customer subscriber report  
 Lists the account ID of every customer who is subscribed to your products, including the number of current and new annual subscriptions for each day\. 

Daily business report  
 Lists the daily usage by AWS customers and projects the estimated revenue that is expected from customer usage\. 

Monthly billed revenue report  
 Lists the revenue that has been billed to customers for usage of your software product, based on hourly usage\. The report also lists any annual and monthly fees that are billed to customers\. 

Sales compensation report  
 Lists monthly billed revenue with additional customer information that isn't in the standard monthly billed revenue report\. This report is available only if you're enrolled in the [AWS Marketplace Enhanced Data Sharing Program](enhanced-data-sharing-program.md)\.

Monthly disbursement report  
Lists the money that was collected and disbursed to you for usage of your software product since your previous disbursement\.

US sales and use tax report  
 Reports on US sales and use tax that are calculated for your products\. It's part of the AWS Marketplace tax calculation service\.

Daily ref tag  
Provides the same information as on the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/marketing/) marketing tab, product pageclicks, and conversions for your ref tag links\.

Weekly ref tag  
 Provides the same information as on the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/marketing/) marketing tab, product pageclicks, and conversions for your ref tag links\. 