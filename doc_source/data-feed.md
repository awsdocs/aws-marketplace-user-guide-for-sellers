# Data Feed<a name="data-feed"></a>

 The data feed collects and delivers a CSV\-formatted file each day to an encrypted Amazon S3 bucket that you provide\. The data feed includes detailed information about your customer and a unique identifier for each entry\. The name of the unique identifier is address\_id and is the same as the Payer Address ID column in the [Sales Compensation Report](sales-compensation-report.md)\. You use that field to map the details in the reports with the detailed customer information provided in the data feed\.

**Important**  
 Use of the information from the data feed is subject to the terms and conditions of participating in the [AWS Marketplace Enhanced Data Sharing Program](enhanced-data-sharing-program.md)\.

 To receive the data feed information, you must: 
+  Be enrolled in the [AWS Marketplace Enhanced Data Sharing Program](enhanced-data-sharing-program.md) 
+  Provide the Amazon Resource Name \(ARN\) for an encrypted S3 bucket 
+  Provide the ARN for an AWS KMS key used to encrypt your S3 bucket 

 Optionally, you can provide the ARN for an Amazon SNS topic\. Providing this ARN enables you to receive a notification when we deliver a new file to your S3 bucket\. 

## Configuring Your Environment<a name="data-feed-configuring"></a>

 To configure your environment, we recommend that you use this [AWS CloudFormation template](https://aws-marketplace-reports-resources.s3.amazonaws.com/DataFeedsResources.yaml)\. The template sets up the AWS resources required to receive the data feed\. Specifically, the template helps to set up an encrypted S3 bucket, AWS KMS key, and optionally an SNS topic under your AWS account ID\. You add the ARNs for these services to the data feed configuration page for the data feed feature\. To configure the data feed feature, from [Setup customer data storage](https://aws.amazon.com/marketplace/management/reports/data-feed-configuration), enter the resource ARNs and choose **Submit**\. If you choose to use existing resources, you must create an IAM role that grants access to AWS Marketplace services\.

## Data Fields<a name="data-feed-data-fields"></a>

 There are several data feed columns\. The address\_id column lists the same information as the Payer Address ID column in the sales compensation report\. The data in this field is key to finding the address of your customer at the time of the transaction\. 

The data feed is delivered daily and contains all of the information that is collected for your customers\. Each time a new transaction occurs, the customer address for the transaction is scanned, and if it's not in your data feed, a new entry is added to your data feed file\. The following table explains the names and descriptions of the data feed's columns\. 


|  Column Name  |  Description  | 
| --- | --- | 
|  address\_id  |  The unique key of the address\.  | 
|  aws\_account\_id  |  The account number of this address\.  | 
|  email\_domain  |  The domain for the email address on file for this account\.  | 
|  company\_name  |  The company name on file for this account\.  | 
|  country  |  The ISO 3166 alpha\-2 country code on file for this address\.  | 
|  state\_or\_region  |  The state or region on file for this address\.  | 
|  city  |  The city on file for this address\.  | 
|  postal\_code  |  The postal code on file for this address\.  | 
|  address\_line\_1  |  The first line of the address on file for this address\.  | 
|  address\_line\_2  |  The second line of the address on file for this address\.  | 
|  address\_line\_3  |  The third line of the address on file for this address\.  | 
|  valid\_from  |  The date when the address is valid from\.  | 
|  valid\_to  |  This column is always blank\.  | 
|  insert\_date  |  The date when the address became visible to you\.  | 
|  update\_date  |  The date when the address was last updated\. It's typically the same as the date in the insert\_date column\. However, there are scenarios where the customer might change the address associated with their account\.  | 
|  delete\_date  |  This column is always blank\.  | 

 Address information is immutable, so the valid\_to and delete\_date columns are always blank\. 

## Sample Data<a name="data-feed-sample-data"></a>

 The address data feed is a \.csv file that follows [4180 standards](https://tools.ietf.org/html/rfc4180) and is delivered to the encrypted S3 bucket that you provide the ARN for\. The file has the following characteristics:
+  It's formatted as a UTF\-8 file that isn't BOM encoded 
+  It uses commas as the separator 
+  Fields are escaped by double quotation marks 
+  The line feed is \\n 
+  Dates are in ISO 8601 date and time format 

 View the following three tables as one contiguous table\. The first row contains the headers in the \.csv file\. The remaining three rows contain sample information for the addresses\. Refer to the example file, PII\_Addresse\.csv, in [AWS Marketplace \- Seller Reporting Examples\.zip](https://s3.amazonaws.com/awsmp-loadforms/AWS+Marketplace+-+Seller+Reporting+Examples.zip)\. 


|  address\_id  |  aws\_account\_id  |  email\_domain  |  company\_name  |  country  |  state\_or\_region  |  city  |  postal\_code  | 
| --- | --- | --- | --- | --- | --- | --- | --- | 
|  fs4rwaassf332df  |  111122223333 |  example\.org  |  Example Corp\.  |  US  |  GA  |  Anytown  |  3XXXX  | 
|  dskd933mks32ds  | 777788889999  |  example\.net  |  Example Corp\.  |  US  |  WA  |  Anytown  |  9XXXX  | 
|  dsdghhf93993sds  |  123456789012  |  example\.com  |  Example Corp\.  |  US |  FL |  Anytown  |  3XXXX  | 


|  address\_line\_1  |  address\_line\_2  |  address\_line\_3  | 
| --- | --- | --- | 
|  123 Any Street  |  unit 100  |   | 
|   |  100 Main Street  |   | 
|   |   |  123 Any Street  | 


|  valid\_from  |  valid\_to  |  insert\_date  |  update\_date  |  delete\_date  | 
| --- | --- | --- | --- | --- | 
|  2018\-12\-12T02:32:00Z  |   |  2019\-03\-29T02:00:00Z  |  2019\-03\-29T02:00:00Z  |   | 
|  2018\-12\-20T02:32:00Z  |   |  2019\-03\-29T02:00:00Z  |  2019\-03\-29T02:00:00Z  |   | 
|  2019\-01\-12T02:32:00Z  |   |  2019\-03\-28T03:00:00Z  |  2019\-03\-28T03:00:00Z  |   | 

 The last five columns document the history of the data\. Addresses in the data feed are immutable, so you don't need to process the information in those fields\. They're included as a common history schema and will accompany all future data feeds\. 

## Amazon SNS Topic Notifications<a name="data-feed-sns-notification"></a>

 If you provided the ARN for an Amazon SNS topic, you receive a notification that the file transfer to your Amazon S3 bucket succeeded, was skipped, or failed\. The details of the notification provide additional information you can use to troubleshoot a failure\. 