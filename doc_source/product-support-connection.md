# Product Support Connection<a name="product-support-connection"></a>

 AWS Marketplace Product Support Connection \(PSC\) is a feature that enables AWS Marketplace customers to provide contact information in the AWS Marketplace website for the purposes of obtaining and accessing product support from AWS Marketplace Sellers\. AWS Marketplace shares the provided data with participating Sellers via an API to enable a better support experience\. Customers can choose to add contact details during or after a purchase of PSC\-enabled AWS Marketplace products, and Sellers can retrieve the Customer contact data, along with relevant product subscription details, by calling a pull\-based API\. 

 Your staff can use the Customer Support Eligibility tool to access near\-real\-time information about a customer's subscription to your products and provide fast, personalized service\. AWS Marketplace Management Portal makes it easy to get started: Enter a customer's AWS account ID to retrieve subscription and usage information from their account\. 

 You also have the option to enroll your products in AWS Marketplace Product Support Connection \(PSC\)\. For products that are enrolled in PSC, AWS Marketplace customers can choose to provide contact information \(including name, organization, email address, and phone number\) via the AWS Marketplace website for the purposes of obtaining and accessing product support\. If you enroll in PSC, AWS Marketplace shares the provided data with you via an API to help enable a more seamless support experience\. 

**Note**  
Currently, data products don't support this feature\.

## Technical implementation guide<a name="technical-implementation-guide"></a>

This section covers API specification details and how to onboard with the product support connection feature\. The PSC `start-support-data-export` API is part of the AWS Marketplace Commerce Analytics Service \(CAS\)\. To integrate with the API for PSC, you must first enroll in CAS\. If you are already enrolled in CAS, use the same AWS Identity and Access Management \(IAM\) role that you created when you onboarded\.

### IAM policy for PSC<a name="allow-iam-users-permission-for-psc"></a>

To allow your IAM users to access the AWS Marketplace product support connection feature, you must attach the following inline policy to your users\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "marketplacecommerceanalytics:StartSupportDataExport",
            "Resource": "*"
        },
    ]
}
```

For more information, see [Creating Policies in the IAM console](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-json-editor) in the *IAM User Guide*\.

### Making requests with the AWS Command Line Interface \(CLI\)<a name="making-requests-with-the-aws-command-line-interface-cli"></a>

 You can request an export of the PSC data using the [AWS CLI](https://aws.amazon.com/cli/) or any of the [AWS Software Development Kits \(SDKs\)](https://aws.amazon.com/tools/)\. 

 If you have already been using CAS to call the `generate-data-set` operation,you must use the same IAM role for both `generate-data-set` and `start-support-data-export`\. 

To ensure the security of the customer contact data available through the Product Support Connection program, we recommend that the Amazon Simple Storage Service \(Amazon S3\) bucket you use for `start-support-data-export` be separate from the S3 bucket you use for `generate-data-set`\. Verify the permissions on your IAM role allow access to all S3 buckets you intend to use\. 

```
        aws marketplacecommerceanalytics start-support-data-export
        --data-set-type "test_customer_support_contacts_data" \
        --from-date “{START-DATE}” \
        --role-name-arn "{YOUR-ROLE-NAME-ARN}” \
        --destination-s3-bucket-name “{YOUR-S3-BUCKET}” \
        --destination-s3-prefix “test-prefix” \
        --sns-topic-arn “{YOUR-SNS-TOPIC-ARN}”
```

 A successful response from the service returns the `dataSetRequestId`*dataSetRequestId* of the request\. 

**Example**  

```
{

"dataSetRequestId":

"646dd4ed-6806-11e5-a6d8-fd5dbcaa74ab"

}
```

## API request parameters and responses<a name="api-request-parameters-and-responses"></a>

### StartSupportDataExport method<a name="startsupportdataexport-method"></a>

 The `StartSupportDataExport` method allows you to request contact details that customers have submitted for your PSC\-enabled products\. Data is exported from the start date specified in the request up to 15 minutes prior to the time of the request\. A successful request results in the dataset being published to the Amazon S3 bucket specified\. 

 At this time, you can query the API to request the test\_customer\_support\_contacts\_data dataset\. This will export a static test dataset containing data that does not correspond to any real customer data\. You should use the test data for testing and integration\. The customer\_support\_contacts\_data option, which will return the real customer contact data for your PSC\-enabled products, will not be available until after the General Availability of this feature later in 2016\. 

### Request parameters<a name="request-parameters"></a>


|  Input  |  Description  | 
| --- | --- | 
|  Data Set Type  |   The type of dataset requested to be exported\. Valid options for datasets are:   test\_customer\_support\_contacts\_data   customer\_support\_contacts\_data   The test\_customer\_support\_contacts\_data dataset provides sample data for testing and integration purposes and is available immediately\. The customer\_support\_contacts\_data dataset is currently unavailable\. This option will contain actual customer data and be available upon general availability of PSC\.   | 
|  From Date  |   The earliest date of data to be exported\. The exported data will contain information from the specified From Date to 15 minutes prior to the time of the request\.   The From Date must be expressed as an ISO 8601 date/time string\.   If you would like to receive the full data set, as opposed to a set of updates, specify any date prior to the date when you onboarded to the program\. To receive only incremental data since your last request, specify the endDateTime from the dataSetCoverageRange from the metadata JSON file resulting from your previous request\. See below for more information about the metadata JSON file\.   | 
|  Role Name ARN  |  The Amazon Resource Name \(ARN\) of the IAM role with an attached permissions policy which provides the service with access to your resources\.  | 
|  Destination S3 Bucket Name  |  The name \(friendly name, not ARN\) of the destination [Amazon S3 bucket](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingBucket.html)\. Your datasets will be published to this location\.  | 
|  Destination S3 Prefix  |   \(Optional\) The desired Amazon S3 prefix for the published dataset, similar to a directory path in standard file systems\.   For example, if given the bucket name "mybucket" and the prefix "myprefix/mydatasets", the output file "outputfile" would be published to "s3://*awsexamplebucket*/myprefix/mydatasets/outputfile"\.   If the prefix directory structure does not exist, it will be created\.   If no prefix is provided, the data set will be published to the Amazon S3 bucket root\.   | 
|  SNS Topic ARN  |  The Amazon Resource Name \(ARN\) for the Amazon SNS topic that will be notified when the data set has been published, or if an error occurs\.  | 

## Responses<a name="responses"></a>

 Calls to the API will immediately return a response with the Data Set Request ID\. 


|  Field  |  Description  | 
| --- | --- | 
|  Data Set Request ID  |  A unique identifier representing a specific request to the service\. This identifier can be used to correlate a request with notifications on the Amazon SNS topic\.  | 

 An additional response containing metadata will be posted to the Amazon Simple Notification Service \(Amazon SNS\) topic specified in the original request\. The contents of the post are detailed in the following table\. 


|  Field  |  Description  | 
| --- | --- | 
|  Data Set S3 Location  |  The bucket name and key for the delivered dataset\.  | 
|  Data Set Meta Data S3 Location  |  The bucket name and key for the delivered dataset meta data file\.  | 
|  Data Set Request ID  |  A unique identifier representing a specific request to the service\. This identifier can be used to correlate a request with notifications on the Amazon SNS topic\.  | 
|  Success  |  "True" if the operation succeeded; "false " if not\.  | 
|  Message  |  \(Optional\) If an error occurred \(for example, “Success” is “false”\), this message will contain information about the failure\.  | 

 The metadata file is JSON\-formatted and contains the following fields\. 


|  Field  |  Description  | 
| --- | --- | 
|  Data Set Request ID  |  A unique identifier representing a specific request to the service\. This identifier can be used to correlate a request with notifications on the Amazon SNS topic\.  | 
|  Data Set Coverage Range  |  Defines the start date / time and end date / time for the data coverage range\. These dates are in ISO 8601 format\.  | 
|  Data Set Request Parameters  |  The original request parameters to the GenerateDataSet method\.  | 
|  Data Set S3 Location  |  The bucket name and key for the delivered dataset\.  | 
|  Data Set Meta Data S3 Location  |  The bucket name and key for the delivered dataset metadata file\.  | 
|  Request Received Date Time  |  The date/time at which the request was received, in ISO 8601 format\.  | 
|  Request Completed Date Time  |  The date/time at which the request was completed, in ISO 8601 format\.  | 

**Example JSON\-formatted metadata contents**  

```
{
    "dataSetRequestId": "c3c84ee0-5aba-11e6-8d9c-235dc080841d",
    "dataSetCoverageRange": {
        "startDateTime": "2016-08-18T00:00:00.000Z",
        "endDateTime": "2016-08-05T03:14:50.334Z"
    },
    "dataSetRequestParameters": {
        "fromDate": "2016-08-18T00:00:00.000Z",
        "dataSetType": "test_customer_support_contacts_data",
        "roleNameArn": "arn:aws:iam::123456789012:role/MarketplaceCommerceAnalyticsRole",
        "destinationS3BucketName": "mybucket",
        "destinationS3Prefix": "mydata",
        "snsTopicArn": "arn:aws:sns:us-west-2:123456789012:mynotification"
    },
    "dataSetS3Location": {
        "bucketName": "mybucket",
        "key": "mydata/test_customer_support_contacts_data_2015-01-18T00-00-00Z_to_2016-08-05T03-14-50Z.csv"
    },
    "dataSetMetaDataS3Location": {
        "bucketName": "mybucket",
        "key": "mydata/test_customer_support_contacts_data_2015-01-18T00-00-00Z_to_2016-08-05T03-14-50Z.meta.json"
    },
    "requestReceivedDateTime": "2016-08-05T03:14:50.108Z",
    "requestCompletedDateTime": "2016-08-05T03:14:50.334Z"
}
```

## Output data format<a name="output-data-format"></a>

 The output data contains customer contact records, product code, product ID, subscription start date, and the AWS account ID of the customer\. A summary of the fields is shown in the following table\. Each output file contains a comma\-separated header, followed by the records containing customer data and subscription information\. Each record contains a “Create”, “Update”, or “Delete” operation type to indicate whether the record is newly created, modified, or deleted since the “From Date” indicated in the API request\. The overall file format adheres to the RFC4180 standard\. 

 If multiple operations have occurred on a record in the time frame specified by the “from\-date” parameter API request, only the most recent data will be reflected or exported\. For example, if a customer creates and then updates a record, the record returned will be different depending on the specified “from\-date”\. If the “from\-date” is prior to the date at which the record was created, only a CREATE record will be passed in the output data set, and the record will reflect the most recently entered details\. If the “from\-date” is after the record was created, but before it was updated, only an UPDATE record will be passed in the output data set\. If the from\-date is after the record was updated, no record will be passed\. Likewise, if a customer creates and then deletes a record, only the “DELETE” will appear in the output file\. 

 If you would like to receive the full dataset, as opposed to a set of updates, specify any date prior to the date when you onboarded to the program\. To receive only incremental data since your last request, specify the `endDateTime` from the `dataSetCoverageRange` from the metadata JSON file resulting from your previous request\. 


|  Field  |  Format  |  Description  | 
| --- | --- | --- | 
|  Product ID  |  36\-character hexadecimal string  |   Unique identifier for the product in AWS Marketplace \(GUID\)\.   Required field; always appears in every record\.   | 
|  Product Code  |  25\-character alphanumeric string  |   Unique identifier for the product, associated with billing and available in Amazon Elastic Compute Cloud \(Amazon EC2\) instance metadata\.   Required field; always appears in every record\.   | 
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

**Note**  
When a customer deletes their contact information from the PSC program, you will see a record in the output \.csv file that indicates an operation type “DELETE\.” After a customer deletes their data, the API no longer transmits contact information such as name, telephone number, email, and so forth\. Each delete record consists of the data required to uniquely identify the record to be deleted\. Delete records contain product ID, product code, operation time, customer GUID, subscription GUID, subscription start date, AWS Customer ID, operation time, and operation type\.   
 If a customer opts out of Product Support Connection by deleting their contact information, you should also remove the contact information from your records\. Because the customer contact data will not be included in the DELETE record, you will need to look up the record in your system by using the unique Customer GUID\.   
 A delete record will also be sent if a customer terminates a subscription\. 

 If you have questions or would like more information about participating in AWS Marketplace Product Support Connection, contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 