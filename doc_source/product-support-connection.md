# Product Support Connection<a name="product-support-connection"></a>

 AWS Marketplace Product Support Connection \(PSC\) is a feature that allows AWS Marketplace customers to provide contact information in the AWS Marketplace website for the purposes of obtaining and accessing product support from AWS Marketplace Sellers\. AWS Marketplace shares the provided data with participating Sellers via an API to enable a better support experience\. Customers can choose to add contact details during or after a purchase of PSC\-enabled AWS Marketplace products, and Sellers can retrieve the Customer contact data, along with relevant product subscription details, by calling a pull\-based API\. 

 Your staff can use the Customer Support Eligibility tool to access near\-real\-time information about a customer's subscription to your products and provide fast, personalized service\. AWS Marketplace Management Portal makes it easy to get started: enter a customer's AWS account ID to retrieve subscription and usage information from their account\. 

 You also have the option to enroll your products in AWS Marketplace Product Support Connection \(PSC\)\. For products that are enrolled in PSC, AWS Marketplace customers can choose to provide contact information \(including name, organization, email address, and phone number\) via the AWS Marketplace web site for the purposes of obtaining and accessing product support\. If you enroll in PSC, AWS Marketplace will share the provided data with you via an API to help enable a more seamless support experience\. 

## How does AWS Marketplace Product Support Connection benefit me as a Seller?<a name="how-does-aws-marketplace-product-support-connection-benefit-me-as-a-seller"></a>

 Participating in PSC can make it easier for you to provide support to customers that subscribe to your products on AWS Marketplace\. The data available through the program lets you keep customer contact information up to date in your support or CRM system\(s\)\. If an AWS Marketplace customer shares contact information through PSC and then contacts you for support, you will be able to quickly access and verify the customer’s identity and product subscription details\. 

## What information will AWS Marketplace Product Support Connection collect from customers?<a name="what-information-will-aws-marketplace-product-support-connection-collect-from-customers"></a>

 We collect first and last name, job title, company name, email address, telephone number, country, and zip code\. Providing contact details is optional, but if a customer chooses to provide contact details, then organization, first and last name, email, and telephone number are required fields\. All provided details, along with the customer’s AWS account number, product ID, product code, and subscription start date, are available to participating Sellers via a pull\-based API\. Customers can add information for up to 5 contacts per product subscription, and they can also edit or delete their contact details later\. 

## Will I receive contact details for every customer subscribed to my product?<a name="will-i-receive-contact-details-for-every-customer-subscribed-to-my-product"></a>

 Not necessarily\. Entering and sharing contact information is optional for customers, although we recommend that customers share at least one contact for supported products in order to receive a better product support experience\. 

## At what point in the purchase process does a customer become eligible for PSC?<a name="at-what-point-in-the-purchase-process-does-a-customer-become-eligible-for-psc"></a>

 Customers have the option to provide contact details for PSC during or after a subscription to a PSC\-enabled product\. For AMI\-based products, customers that choose Annual or Monthly subscription options are charged for the product when they subscribe; customers that choose hourly subscriptions are charged when they launch an instance\. For more information about what it means for customers to subscribe to a product, visit the [AWS Marketplace Help Pages](https://aws.amazon.com/marketplace/help/200799470)\. 

## Will I receive data about a customer’s product usage?<a name="will-i-receive-data-about-a-customers-product-usage"></a>

 No; at this time, PSC collects contact details and subscription information only\. Usage data is not currently collected as part of this program\. 

## Seller Requirements<a name="seller-requirements"></a>

### What do I need to do to qualify to participate in AWS Marketplace Product Support Connection?<a name="what-do-i-need-to-do-to-qualify-to-participate-in-aws-marketplace-product-support-connection"></a>

 To participate, there are specific policies you must follow: 
+  You must list commercially supported, enterprise production versions of your software with a dedicated support email address \(or equivalent contact method\) that is usable by customers and AWS Customer Support\. 
+  You must compensate your sales force for all AWS Marketplace transactions that occur in a sales territory or named account segment\. Communication on AWS Marketplace compensation must be sent to your Global Field, and AWS must receive a copy of that communication\. 
+  Your Customer Support teams must outline a policy regarding how you plan to provide support for AWS Marketplace customers, and should provide AWS Marketplace with a copy of your policy\. This guidance must be provided to your Customer Support teams in order for AWS Marketplace to engage with your Customer Support\. 
+  Any customer information provided to you through the API should be added to your systems within one business day\. In addition, customers must have the ability to opt out of the program at any time\. The data available through the PSC API will indicate when a customer has deleted contact details and wishes to be removed from the program\. 

 If you have any questions about these program requirements, contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

### What steps do I need to complete in order to participate in Product Support Connection?<a name="what-steps-do-i-need-to-complete-in-order-to-participate-in-product-support-connection"></a>

 You must complete the following steps in order to participate: 

1.  Using the static test dataset that is available, integrate with the PSC API so that data provided through the API will be added to your backend CRM or support system\(s\) within no more than one business day\. See “Integrating with the Seller API” and “Handling Customer Data” below for more details\. 

1.  Provide a list of the product\(s\) you would like to enroll in the program to the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. This will ensure that your products are flagged for enrollment in PSC\. See “Enrolling Your Products” below for more details\. 

1.  Work with the AWS Marketplace team to ensure that your product detail pages contain a valid support email address or equivalent contact method\. 

1.  Provide a description \(about 1 page\) of the support processes you plan to follow for AWS Marketplace customers, and submit your description to the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. This description should outline your planned support processes in a few paragraphs and should be provided to AWS Marketplace in addition to being communicated to your internal support team\. This document is for AWS Marketplace internal use and helps us track the customer experience across products that are enrolled in PSC\. See below for a list of questions your writeup should address\. 

1.  You can optionally customize your Welcome email, which customers receive after subscribing to your product, to describe your PSC support processes or give your customers more information about product support\. Contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team if you wish to customize your welcome email content\. 

### What information should I include in my description of support processes?<a name="what-information-should-i-include-in-my-description-of-support-processes"></a>
+  Which product listing\(s\) will you enroll in PSC? 
+  Have you already built and tested a way to pull data from the API and port it to your support systems? 
  +  If yes, describe how you import this data to your support systems? 
  +  If no, when do you expect to have this implemented? Describe your planned approach\. 
+ Summarize your support process for AWS Marketplace customers that participate in PSC\. 
  +  How can AWS Marketplace PSC customers contact you to receive support for these products \(email, phone, other methods\)? 
  +  If PSC customers contact you for support, how long will it typically take before they receive a reply? 
  +  Do you have different support levels for different AWS Marketplace products? If so, describe your support tiers and what they cover\. 
  +  What communications do you plan to send to customers under your support policy? If you plan to send proactive communications, describe what you plan to send\. 
  +  After customers enter their data in the AWS Marketplace site, how long will it take for the data to appear in your support system\(s\)? 
  +  If a customer opts out of PSC, what is your process for deleting their contact data? 
  +  Do you have a web page describing the support you offer for AWS Marketplace customers? If so, provide it\. 

## Enrolling Your Products<a name="enrolling-your-products"></a>

### How do I enroll products in PSC?<a name="how-do-i-enroll-products-in-psc"></a>

 After reviewing the program requirements, contact the AWS Marketplace Seller Catalog Operations team to provide a list of the products you would like to enroll in PSC\. You can enroll new or existing AMI\-based products in the program\. Allow 1\-2 weeks for your request to be processed\. You will need to verify that you have completed integration with the API before your products can be enabled for PSC\. As described above, you must also provide a valid support email address on your product page\(s\), and you should provide a writeup describing the data handling and support process you plan to follow for AWS Marketplace customers\. 

## Handling Customer Data<a name="handling-customer-data"></a>

### How can I use the data available through Product Support Connection?<a name="how-can-i-use-the-data-available-through-product-support-connection"></a>

 Information you receive under the PSC program constitutes “Subscriber Information” under the Terms and Conditions for AWS Marketplace Sellers \(the “Seller Terms”\) and may only be used in accordance with the Seller Terms \(including Section 3\.8 thereof\)\. The data cannot be used for marketing or other purposes not related to product support\. 

### How should I handle and store customer data provided through AWS Marketplace Product Support Connection?<a name="how-should-i-handle-and-store-customer-data-provided-through-aws-marketplace-product-support-connection"></a>

 You must handle customer data in accordance with applicable law and your privacy policy; we recommend that customer data should be encrypted in transit and at rest\. The provided customer data constitutes Subscriber Information under the Seller Terms and can only be used for providing product support\. 

## Technical Implementation Guide<a name="technical-implementation-guide"></a>

 This section covers API specification details and how to onboard with the API\. The PSC API, “start\-support\-data\-export” is part of the AWS Marketplace Commerce Analytics Service \(CAS\)\. In order to integrate with the API for PSC you must first enroll in CAS\. If you have already enrolled in CAS, you can skip steps 1\-4 below\. If you have already enrolled in CAS, you will need to use the same IAM Role that you created when you first onboarded\. 

### Making requests with the AWS Command Line Interface \(CLI\)<a name="making-requests-with-the-aws-command-line-interface-cli"></a>

 You can request an export of the PSC data using the [AWS CLI](https://aws.amazon.com/cli/) or any of the [AWS Software Development Kits \(SDKs\)](https://aws.amazon.com/tools/)\. 

 If you have already been using CAS to call the *generate\-data\-set* method, you must use the same IAM Role for both *generate\-data\-set* and *start\-support\-data\-export*\. To ensure the security of the customer contact data available through the Product Support Connection program, we recommend that the S3 bucket you use for *start\-support\-data\-export* be separate from the S3 bucket you use for *generate\-data\-set*\. Verify the permissions on your IAM role allow access to all S3 buckets you intend to use\. 

```
        aws marketplacecommerceanalytics start-support-data-export
        --data-set-type "test_customer_support_contacts_data" \
        --from-date “{START-DATE}” \
        --role-name-arn "{YOUR-ROLE-NAME-ARN}” \
        --destination-s3-bucket-name “{YOUR-S3-BUCKET}” \
        --destination-s3-prefix “test-prefix” \
        --sns-topic-arn “{YOUR-SNS-TOPIC-ARN}”
```

 A successful response from the service will return the *dataSetRequestId* of the request\. 

 **Sample response**: 


|  | 
| --- |
|   \{   "dataSetRequestId":   "646dd4ed\-6806\-11e5\-a6d8\-fd5dbcaa74ab"   \}   | 

## API Request Parameters and Responses<a name="api-request-parameters-and-responses"></a>

### StartSupportDataExport Method<a name="startsupportdataexport-method"></a>

 The StartSupportDataExport method allows you to request contact details that customers have submitted for your PSC\-enabled products\. Data will be exported from the start date specified in the request up to 15 minutes prior to the time of the request\. A successful request will result in the dataset being published to the Amazon S3 bucket specified\. 

 At this time, you can query the API to request the test\_customer\_support\_contacts\_data data set\. This will export a static test data set containing data that does not correspond to any real customer data\. You should use the test data for testing and integration\. The customer\_support\_contacts\_data option, which will return the real customer contact data for your PSC\-enabled products, will not be available until after the General Availability of this feature later in 2016\. 

### Request Parameters<a name="request-parameters"></a>


|  Input  |  Description  | 
| --- | --- | 
|  Data Set Type  |   The type of dataset requested to be exported\. Valid options for datasets are:   test\_customer\_support\_contacts\_data   customer\_support\_contacts\_data   The test\_customer\_support\_contacts\_data dataset provides sample data for testing and integration purposes and is available immediately\. The customer\_support\_contacts\_data dataset is currently unavailable\. This option will contain actual customer data and be available upon general availability of PSC\.   | 
|  From Date  |   The earliest date of data to be exported\. The exported data will contain information from the specified From Date to 15 minutes prior to the time of the request\.   The From Date must be expressed as an ISO 8601 date/time string\.   If you would like to receive the full data set, as opposed to a set of updates, specify any date prior to the date when you onboarded to the program\. To receive only incremental data since your last request, specify the endDateTime from the dataSetCoverageRange from the metadata JSON file resulting from your previous request\. See below for more information about the metadata JSON file\.   | 
|  Role Name ARN  |  The Amazon Resource Name \(ARN\) of the IAM role with an attached permissions policy which provides the service with access to your resources\.  | 
|  Destination S3 Bucket Name  |  The name \(friendly name, not ARN\) of the destination [Amazon S3 bucket](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingBucket.html)\. Your data sets will be published to this location\.  | 
|  Destination S3 Prefix  |   \(Optional\) The desired Amazon S3 prefix for the published data set, similar to a directory path in standard file systems\.   For example, if given the bucket name "mybucket" and the prefix "myprefix/mydatasets", the output file "outputfile" would be published to "s3://mybucket/myprefix/mydatasets/outputfile"\.   If the prefix directory structure does not exist, it will be created\.   If no prefix is provided, the data set will be published to the Amazon S3 bucket root\.   | 
|  SNS Topic ARN  |  The Amazon Resource Name \(ARN\) for the Amazon SNS topic that will be notified when the data set has been published, or if an error occurs\.  | 

## Responses<a name="responses"></a>

 Calls to the API will immediately return a response with the Data Set Request ID\. 


|  Field  |  Description  | 
| --- | --- | 
|  Data Set Request ID  |  A unique identifier representing a specific request to the service\. This identifier can be used to correlate a request with notifications on the Amazon SNS topic\.  | 

 An additional response containing metadata will be posted to the Amazon SNS \(Simple Notification Service\) topic specified in the original request\. The contents of the post are detailed in the table below\. 


|  Field  |  Description  | 
| --- | --- | 
|  Data Set S3 Location  |  The bucket name and key for the delivered data set\.  | 
|  Data Set Meta Data S3 Location  |  The bucket name and key for the delivered data set meta data file\.  | 
|  Data Set Request ID  |  A unique identifier representing a specific request to the service\. This identifier can be used to correlate a request with notifications on the Amazon SNS topic\.  | 
|  Success  |  True if the operation succeeded, false if not\.  | 
|  Message  |  \(Optional\) If an error occurred \(i\.e\., “Success” is “false”\), this message will contain information about the failure\.  | 

 The metadata file is JSON\-formatted and contains the following fields: 


|  Field  |  Description  | 
| --- | --- | 
|  Data Set Request ID  |  A unique identifier representing a specific request to the service\. This identifier can be used to correlate a request with notifications on the Amazon SNS topic\.  | 
|  Data Set Coverage Range  |  Defines the start date / time and end date / time for the data coverage range\. These dates are in ISO 8601 format\.  | 
|  Data Set Request Parameters  |  The original request parameters to the GenerateDataSet method\.  | 
|  Data Set S3 Location  |  The bucket name and key for the delivered data set\.  | 
|  Data Set Meta Data S3 Location  |  The bucket name and key for the delivered data set meta data file\.  | 
|  Request Received Date Time  |  The date/time at which the request was received, in ISO 8601 format\.  | 
|  Request Completed Date Time  |  The date/time at which the request was completed, in ISO 8601 format\.  | 

 Example JSON\-formatted metadata contents: 

 \{ 

 "dataSetRequestId": "c3c84ee0\-5aba\-11e6\-8d9c\-235dc080841d", 

 "dataSetCoverageRange": \{ 

 "startDateTime": "2016\-08\-18T00:00:00\.000Z", 

 "endDateTime": "2016\-08\-05T03:14:50\.334Z" 

 \}, 

 "dataSetRequestParameters": \{ 

 "fromDate": "2016\-08\-18T00:00:00\.000Z", 

 "dataSetType": "test\_customer\_support\_contacts\_data", 

 "roleNameArn": "arn:aws:iam::123456789012:role/MarketplaceCommerceAnalyticsRole", 

 "destinationS3BucketName": "mybucket", 

 "destinationS3Prefix": "mydata", 

 "snsTopicArn": "arn:aws:sns:us\-west\-2:123456789012:mynotification" 

 \}, 

 "dataSetS3Location": \{ 

 "bucketName": "mybucket", 

 "key": "mydata/test\_customer\_support\_contacts\_data\_2015\-01\-18T00\-00\-00Z\_to\_2016\-08\-05T03\-14\-50Z\.csv" 

 \}, 

 "dataSetMetaDataS3Location": \{ 

 "bucketName": "mybucket", 

 "key": "mydata/test\_customer\_support\_contacts\_data\_2015\-01\-18T00\-00\-00Z\_to\_2016\-08\-05T03\-14\-50Z\.meta\.json" 

 \}, 

 "requestReceivedDateTime": "2016\-08\-05T03:14:50\.108Z", 

 "requestCompletedDateTime": "2016\-08\-05T03:14:50\.334Z" 

 \} 

## Output Data Format<a name="output-data-format"></a>

 The output data contains customer contact records, product code, product ID, subscription start date, and the AWS account ID of the customer\. A summary of the fields is shown below\. Each output file contains a comma\-separated header, followed by the records containing customer data and subscription information\. Each record contains a “Create”, “Update”, or “Delete” operation type to indicate whether the record is newly created, modified, or deleted since the “From Date” indicated in the API request\. The overall file format adheres to the RFC4180 standard\. 

 If multiple operations have occurred on a record in the time frame specified by the “from\-date” parameter API request, only the most recent data will be reflected or exported\. For example, if a customer creates and then updates a record, the record returned will be different depending on the specified “from\-date”\. If the “from\-date” is prior to the date at which the record was created, only a CREATE record will be passed in the output data set, and the record will reflect the most recently entered details\. If the “from\-date” is after the record was created, but before it was updated, only an UPDATE record will be passed in the output data set\. If the from\-date is after the record was updated, no record will be passed\. Likewise, if a customer creates and then deletes a record, only the “DELETE” will appear in the output file\. 

 If you would like to receive the full data set, as opposed to a set of updates, specify any date prior to the date when you onboarded to the program\. To receive only incremental data since your last request, specify the endDateTime from the dataSetCoverageRange from the metadata JSON file resulting from your previous request\. 


|  Field  |  Format  |  Description  | 
| --- | --- | --- | 
|  Product ID  |  36\-character hexadecimal string  |   Unique identifier for the product in AWS Marketplace \(GUID\)\.   Required field; always appears in every record\.   | 
|  Product Code  |  25\-character alphanumeric string  |   Unique identifier for the product, associated with billing and available in EC2 instance metadata\.   Required field; always appears in every record\.   | 
|  Customer Guid  |  36\-character hexadecimal string  |   Unique GUID identifying the customer contact data record\. This will be unique for each record that appears in the output file\.   Required field; always appears in every record\.   | 
|  Subscription Guid  |  36\-character hexadecimal string  |   Unique GUID corresponding to the customer’s product subscription\. A customer can have multiple subscriptions to the same product\.   Required field; always appears in every record\.   | 
|  Subscription Start Date  |   ISO 8601 date/time, with UTC time zone\.   The format is YYYY\-MM\-DDTHH:mm:ss\.nnnZ, where YYYY is year, MM is month, DD is day, HH is hour from 00\-23, mm is minute of hour from 00\-59, ss is second of minute from 00\-59, and nnn is millisecond of second from 000\-9999, such as “2016\-04\-07T14:05:15\.275Z”   |   Start date of the customer’s product subscription\.   Required field; always appears in every record\.   | 
|  Organization  |  String with a maximum length of 255 characters  |   Organization name provided by the customer\.   Always appears in records with operation type “Update” or “Create\.” Does not appear in records with operation type “Delete\.”   | 
|  AWS Customer Id  |  12\-digit numeric string which may include leading zeroes  |   The AWS customer ID for the customer subscribed to the product\.   Required field; always appears in every record\.   | 
|  Given Name  |  String with a maximum length of 100 characters  |   Given name or first name for the point of contact provided by the customer\.   Always appears in records with operation type “Update” or “Create\.” Does not appear in records with operation type “Delete\.”   | 
|  Surname  |  String with a maximum length of 100 characters  |   Surname \(family name or last name\) for the point of contact provided by the customer\.   Always appears in records with operation type “Update” or “Create\.” Does not appear in records with operation type “Delete\.”   | 
|  Telephone Number  |  String with a maximum length of 25 characters\. May include international phone numbers\.  |   Telephone number provided by the customer\.   Always appears in records with operation type “Update” or “Create\.” Does not appear in records with operation type “Delete\.”   | 
|  Email  |  String with a maximum length of 254 characters  |   Email address provided by the customer\.   Always appears in records with operation type “Update” or “Create\.” Does not appear in records with operation type “Delete\.”   | 
|  Title  |  String with a maximum length of 255 characters  |   Job title provided by the customer\.   Optional field\. Will sometimes occur in records with operation type “Update” or “Create\.” Does not appear in records with operation type “Delete\.”   | 
|  Country Code  |  2\-character ISO 3166 country code  |   Country code provided by the customer\.   Optional field\. Will sometimes occur in records with operation type “Update” or “Create\.” Does not appear in records with operation type “Delete\.”   | 
|  ZIP Code  |  5\-digit string  |   Zip code provided by the customer; applicable to USA only\.   Optional field\. Will sometimes occur in records with operation type “Update” or “Create\.” Does not appear in records with operation type “Delete\.”   | 
|  Operation Time  |  ISO 8601 date/time, with UTC time zone\. The format is YYYY\-MM\-DDTHH:mm:ss\.nnnZ \(YYYY is year, MM is month, DD is day of month, HH is hour of day from 00\-23, mm is minute of hour from 00\-59, ss is second of minute from 00\-59 and nnn is millisecond of second from 000\-9999\), such as “2016\-04\-07T14:05:15\.275Z”  |   Indicates the date/time when the record was most recently created, updated, or deleted by the customer\.   Required field; always appears in every record\.   | 
|  Operation Type  |  String; possible values are “CREATE”, “UPDATE”, or “DELETE”  |   CREATE: Indicates that the record has been newly created since the from\-date specified in the API request\.   UPDATE: Indicates that the record has been updated since the from\-date specified in the API request\.   DELETE: Indicates that the record has been deleted since the from\-date specified in the API request\.   Required field; always appears in every record\.   | 

 An example of the output file format is shown below\. 

 Product Id,Product Code,Customer Guid,Subscription Guid,Subscription Start Date,Organization,AWS Customer Id,Given Name,Surname,Telephone Number,Email,Title,Country Code,ZIP Code,Operation Time,Operation Type 

 4b898955\-84fa\-4cfb\-8f43\-98287ad69c06,4gzp2symm0v9zidfrn9f854w6,ba1d75cc\-d984\-4f07\-bb14\-ae04b952afbc,cad371fb\-6f2c\-4537\-a054\-1a7afc6312fd,2016\-05\-27T00:00:00\.000Z,Example Inc \-\- Service Division,000011112222,Eugene,Thietmar,555\-947\-8228,eugethi@example\.org,,,,2016\-05\-12T03:54:46\.143Z,CREATE 

 4b898955\-84fa\-4cfb\-8f43\-98287ad69c06,4gzp2symm0v9zidfrn9f854w6,1b4a2b5f\-2c5d\-4779\-b0c7\-2878b0f45cfc,cad371fb\-6f2c\-4537\-a054\-1a7afc6312fd,2016\-05\-19T00:00:00\.000Z,Example Inc \-\- Service Division,000011112222,Angela,Doe,555\-294\-4528,adoe@example\.com,,US,02201,2016\-05\-19T18:21:06\.834Z,CREATE 

 cade58ff\-ff82\-4770\-b84b\-0bd399bf1c6d,c0dcyyqczbk5uc62acmp6450t,6c83ff14\-5167\-43cc\-bb9f\-24865a78db72,c2f40319\-8fc2\-409a\-884b\-2f85adf9e29c,2015\-12\-01T00:00:00\.000Z,Example Inc \-\- European Sales Division,111122223333,Ravi,Smith,555\-111\-1010,ravis@example\.com,Head of IT,ES,,2016\-04\-07T14:05:15\.145Z,CREATE 

 4b898955\-84fa\-4cfb\-8f43\-98287ad69c06,4gzp2symm0v9zidfrn9f854w6,1b4a2b5f\-2c5d\-4779\-b0c7\-2878b0f45cfc,cad371fb\-6f2c\-4537\-a054\-1a7afc6312fd,2016\-05\-01T00:00:00\.000Z,,000011112222,,,,,,,,2016\-04\-22T14:36:24\.054Z,DELETE 

 3f4300eb\-bfa0\-4610\-8d68\-d8ba71baaa50,3qtu9xydxldrj8c5jyldy1lqo,91c72621\-6cf4\-4d69\-8ebe\-073ff4f8ab9e,d118eb96\-55ce\-4752\-909c\-eedcfdcd6647,2015\-11\-30T00:00:00\.000Z,Example Inc \-\- Design Division,333344445555,Nathan,Zhenyuan,555\-2222\-1010,nathanz@example\.com,Sr\. Program Manager,US,98109,2016\-04\-07T14:05:15\.275Z,CREATE 

 3f4300eb\-bfa0\-4610\-8d68\-d8ba71baaa50,3qtu9xydxldrj8c5jyldy1lqo,2ae0be12\-7397\-4fdb\-a1c7\-ead17967002c,d118eb96\-55ce\-4752\-909c\-eedcfdcd6647,2016\-05\-01T00:00:00\.000Z,Example Inc \-\- Design Division,333344445555,Abdul,Alves,555\-676\-8989,abdal@example\.com,,,,2016\-05\-11T05:26:51\.000Z,UPDATE 

 \.\.\. 

## A Note about the “Delete” Operation Type<a name="a-note-about-the-delete-operation-type"></a>

 When a customer deletes their contact information from the PSC program, you will see a record in the output csv file that indicates an operation type “DELETE\.” After a customer deletes their data, the API will no longer transmit contact information such as name, telephone number, email, and so forth\. Each delete record consists of the data required to uniquely identify the record to be deleted\. Delete records contain product ID, product code, operation time, customer GUID, subscription GUID, subscription start date, AWS Customer ID, operation time, and operation type\. 

 If a customer opts out of Product Support Connection by deleting their contact information, you should also remove the contact information from your records\. Since the customer contact data will not be included in the DELETE record, you will need to look up the record in your system by using the unique Customer GUID\. 

 A delete record will also be sent if a customer terminates a subscription\. 

## I’ve Pulled the Data into My S3 Bucket\. Now What Do I Do?<a name="ive-pulled-the-data-into-my-s3-bucket.-now-what-do-i-do"></a>

 The integration steps from this point will depend on your internal support systems and processes\. You should ensure that the customer contact details exported from the API are added to your internal support or CRM system\(s\) within no more than one business day, so that AWS Marketplace customers can be identified if they contact your support team\. Many CRM systems offer APIs to create, update, and delete records from the system in an automated way\. 

## More Questions?<a name="more-questions"></a>

 If you have questions or would like more information about participating in AWS Marketplace Product Support Connection, contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 