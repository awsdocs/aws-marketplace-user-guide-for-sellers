# AWS Marketplace Commerce Analytics Service<a name="commerce-analytics-service"></a>

The AWS Marketplace Commerce Analytics Service lets you programmatically access product and customer data through AWS Marketplace\. After you enroll in the service, you can access your usage, subscription, and billing reports through the AWS SDK\.

 ![\[Commerce Analytics Service Overview\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/commerce-analytics-service-overview.png) 

 The data you request using the SDK tools is delivered to your AWS account as datasets\. Most of the datasets correspond to the same data as the text\-based reports available on the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour)\. You can request datasets for a specific date, and the data is delivered to the provided Amazon S3 bucket\. Notification of data delivery is provided by the Amazon Simple Notification Service \(Amazon SNS\)\. 

## Terms and conditions<a name="terms-and-conditions"></a>

 These AWS Marketplace Commerce Analytics Service Terms and Conditions \(these "**CAS Terms**”\) contain the terms and conditions specific to your use of and access to the AWS Marketplace Commerce Analytics Service \("**CA Service**”\) and are effective as of the date you click an "I Accept” button or check box presented with these CAS Terms or, if earlier, when you use any CA Service offerings\. These CAS Terms are an addendum to the Terms and Conditions for AWS Marketplace Sellers \(the "**AWS Marketplace Seller Terms**”\) between you and Amazon Web Services, Inc\. \("**AWS**,” "**we**,” "**us**” or "**our**”\), the terms of which are hereby incorporated herein\. In the event of a conflict between these CAS Terms and the AWS Marketplace Seller Terms, the terms and conditions of these CAS Terms apply, but only to the extent of such conflict and solely with respect to your use of the CA Service\. Capitalized terms used herein but not defined herein shall have the meanings set forth in the AWS Marketplace Seller Terms\. 

1.  **CA Services and CAS Data\.** To qualify for access to the CA Service, you must be an AWS Marketplace Seller bound by existing AWS Marketplace Seller Terms\. Information and data you receive or have access to in connection with the CA Service \("**CAS Data**”\) constitutes Subscriber Information and is subject to the restrictions and obligations set forth in the AWS Marketplace Seller Terms\. You may use CAS Data on a confidential basis to improve and target marketing and other promotional activities related to Your AWS Marketplace Content provided that you do not \(a\) disclose CAS Data to any third party; \(b\) use any CAS Data in any way inconsistent with applicable privacy policies or law; \(c\) contact a subscriber to influence them to make an alternative purchase outside of the AWS Marketplace; \(d\) disparage us, our affiliates, or any of their or our respective products; or \(e\) target communications of any kind on the basis of the intended recipient being an AWS Marketplace subscriber\. 

1.  **CA Service Limitations and Security\.** You will only access \(or attempt to access\) the CA Service by the means described in the CA Service documentation\. You will not misrepresent or mask your identity or your client's identity when using the CA Service\. We reserve the right, in our sole discretion, to set and enforce limits on your use of the CA Service, including, without limitation, with respect to the number of connections, calls and servers permitted to access the CA Service during any period of time\. You agree to, and will not attempt to circumvent such limitations\. We reserve the right to restrict, suspend or terminate your right to access the CA Service if we believe that you may be in breach of these CAS Terms or are misusing the CA Service\. 

1.  **CA Service Credential Confidentiality and Security\.** CA Service credentials \(such as passwords, keys and client IDs\) are intended to be used by you to identify your API client\. You are solely responsible for keeping your credentials confidential and will take all reasonable measures to avoid disclosure, dissemination or unauthorized use of such credentials, including, at a minimum, those measures you take to protect your own confidential information of a similar nature\. CA Service credentials may not be embedded on open source projects\. You are solely responsible for any and all access to the CA Service with your credentials\. 

1.  **Modification\.** We may modify these CAS Terms at any time by posting a revised version on the AWS Site or providing you with notice in accordance with the AWS Marketplace Seller Terms\. The modified terms will become effective upon posting or, if we notify you by email, as stated in the email message\. By continuing use or access the CA Service after the effective date of any modifications to these CAS Terms, you agree to be bound by the modified terms\. 

1.  **Termination\.** These CAS Terms and the rights to use CAS Data granted herein will terminate, with or without notice to you upon termination of your AWS Marketplace Seller Terms for any reason\. In addition, we may stop providing the CA Services or terminate your access to the CA Services at any time for any or no reason\. 

## Onboarding guide<a name="on-boarding-guide"></a>

You must configure your AWS account and AWS services to use the AWS Marketplace Commerce Analytics Service\. 

**To use the AWS Marketplace Commerce Analytics Service**

1. [Set up your AWS account with permissions](#permissions-for-commerce-analytics)\.

1. [Create a destination Amazon S3 bucket](#create-a-destination-amazon-s3-bucket)\.

1. [Configure an Amazon SNS topic for response notifications](#create-an-amazon-sns-topic-for-response-notifications)\. 

1. [Enroll in the Commerce Analytics Service program](#enroll-in-the-commerce-analytics-service-program)\.

1. [Verify your configuration](#verify-your-configuration)\.

### Set up your AWS account with permissions<a name="permissions-for-commerce-analytics"></a>

AWS Marketplace **strongly** recommends using AWS Identity and Access Management \(IAM\) roles to sign in to the AWS Marketplace Management Portal rather than using your root account credentials\. See [Policies and permissions for AWS Marketplace sellers](detailed-management-portal-permissions.md) for specific IAM permissions for AWS Marketplace Commerce Analytics Service permissions\. See [Create IAM Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_identity-management.html#intro-identity-users) for details\. By creating individual IAM users for people accessing your account, you can give each IAM user a unique set of security credentials\. You can also grant different permissions to each IAM user\. If necessary, you can change or revoke an IAM user's permissions any time\.

### Create a destination Amazon S3 bucket<a name="create-a-destination-amazon-s3-bucket"></a>

The Commerce Analytics Service delivers the data you request to an Amazon S3 bucket that you specify\. If you already have an Amazon S3 bucket to use, proceed to the next step\.

If you don't have an Amazon S3 bucket or you want to create an Amazon S3 bucket specifically for this data, see [How do I Create an S3 Bucket](https://docs.aws.amazon.com/AmazonS3/latest/UG/CreatingaBucket.html)\. 

### Configure an Amazon SNS topic for response notifications<a name="create-an-amazon-sns-topic-for-response-notifications"></a>

The Commerce Analytics Service delivers response notifications using Amazon SNS\. The service publishes messages to this topic to notify you when your datasets are available or if an error occurred\. If you already have an Amazon SNS topic for this purpose, proceed to the next step\.

If you don't have an Amazon SNS topic configured for this service, configure one now\. For instructions, see [Create a Topic](https://docs.aws.amazon.com/sns/latest/dg/CreateTopic.html)\.

Record the topic Amazon Resource Name \(ARN\) for the topic you created, because the ARN is required to call the service\. 

### Enroll in the Commerce Analytics Service program<a name="enroll-in-the-commerce-analytics-service-program"></a>

The Commerce Analytics Service accesses the Amazon S3 bucket and Amazon SNS topic after you configure the service with the ARN for the topic and name of the bucket\.

**To enable access**

1. Log in to the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/) with the AWS account you use to manage your AWS Marketplace products\. 

1. Navigate to the [Commerce Analytics Service enrollment page](https://aws.amazon.com/marketplace/management/cas/enroll)\. 

1. Enter the Amazon S3 bucket name and Amazon SNS topic ARN, and choose **Enroll**\. 

1. On the permissions page, choose **Allow**\.

1. On the AWS Marketplace Management Portal, record the **Role Name ARN** in the success message\. You need the ARN to call the service\. 

### Verify your configuration<a name="verify-your-configuration"></a>

The last step is to verify that your configuration works as expected\.

**To test your configuration**

1.  Download, install, and configure the [AWS Command Line Interface](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-set-up.html) \(AWS CLI\)\. 

1.  Using the AWS CLI, run this command\. 

   ```
   aws marketplacecommerceanalytics generate-data-set \
   --data-set-type "customer_subscriber_hourly_monthly_subscriptions" \
   --data-set-publication-date "{TODAY'S-DATE}" \
   --role-name-arn "{YOUR-ROLE-NAME-ARN}" \
   --destination-s3-bucket-name "{YOUR-S3-BUCKET}" \
   --destination-s3-prefix "test-prefix" \
   --sns-topic-arn "{YOUR-SNS-TOPIC-ARN}"
   ```
+  For `--data-set-publication-date`, replace `{TODAY'S DATE}` with the current date using ISO\-8601 format, `YYYY-MM-DDT00:00:00Z`, where `YYYY` is the four\-digit year, `MM` is the two\-digit month, and `DD` is the two\-digit day\. 
+  For `--role-name-arn`, replace `{YOUR-ROLE-NAME-ARN}` with the ARN of the role you received from the enrollment process in [Enroll in the Commerce Analytics Service program](#enroll-in-the-commerce-analytics-service-program)\. 
+  For *\-\-destination\-s3\-bucket\-name*, replace *\{YOUR\-S3\-BUCKET\}* with the Amazon S3 bucket you created in [Create a destination Amazon S3 bucket](#create-a-destination-amazon-s3-bucket)\. 
+  For *–sns\-topic\-arn*, replace *\{YOUR\-SNS\-TOPIC\-ARN\}* with the Amazon SNS topic you created in [Configure an Amazon SNS topic for response notifications](#create-an-amazon-sns-topic-for-response-notifications)\. 

If you receive a response including the *dataSetRequestId* response from the service, you've completed the on\-boarding process\. A successful response looks like this: 

```
{
   "dataSetRequestId": "646dd4ed-6806-11e5-a6d8-fd5dbcaa74ab"
}
```

## Technical implementation guide<a name="technical-implementation-guide"></a>

 The AWS Marketplace Commerce Analytics Service is provided through the [AWS SDK](https://aws.amazon.com/tools/)\. This guide shows you how to interact with the service using the [AWS CLI](https://aws.amazon.com/cli/) and the [AWS SDK for Java](https://aws.amazon.com/sdk-for-java/)\.

### IAM policy for Commerce Analytics Service<a name="aws-marketplace-commerce-analytics-iam-permissions"></a>

To allow your IAM users to use the Commerce Analytics Service, attach the following inline policy to your users\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "marketplacecommerceanalytics:GenerateDataSet",
            "Resource": "*"
        },
    ]
}
```

For more information, see [Creating Policies in the IAM console](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-json-editor) in the *IAM User Guide*\.

### Making Requests with the AWS CLI<a name="making-requests-with-aws-cli"></a>

To get started, download the [AWS CLI](https://aws.amazon.com/cli/)\. The following AWS CLI example makes a request for the **Hourly/Monthly Subscriptions** dataset for October 1, 2017\. This dataset is published to the **demo\-bucket** Amazon S3 bucket using the prefix **demo\-prefix**, and the notification message is delivered to the **demo\-topic** Amazon SNS topic\. 

```
aws marketplacecommerceanalytics generate-data-set \
--data-set-type "customer_subscriber_hourly_monthly_subscriptions" \
--data-set-publication-date "2017-10-01T00:00:00Z" \
--role-name-arn "arn:aws:iam::123412341234:role/MarketplaceCommerceAnalyticsRole" \
--destination-s3-bucket-name "demo-bucket" \
--destination-s3-prefix "demo-prefix" \
--sns-topic-arn "arn:aws:sns:us-west-2:123412341234:demo-topic"
```

 This request returns an identifier that is unique for each request\. You can use this identifier to correlate requests with notifications published to your Amazon SNS topic\. The following example is an example of this identifier\.

```
{
   "dataSetRequestId": "646dd4ed-6806-11e5-a6d8-fd5dbcaa74ab"
}
```

### Making requests with the AWS SDK for Java<a name="making-requests-with-aws-java-sdk"></a>

To start, download the [AWS Java SDK](https://aws.amazon.com/sdk-for-java/)\. The following AWS SDK for Java example makes a request for the **Hourly/Monthly Subscriptions** dataset for October 1, 2015\. This dataset is published to the **demo\-bucket** Amazon S3 bucket using the prefix **demo\-prefix**, and the notification message is delivered to the **demo\-topic** Amazon SNS topic\. 

```
/*
* Copyright Amazon.com, Inc. or its affiliates. All Rights Reserved.
*
* Licensed under the Apache License, Version 2.0 (the "License").
* You may not use this file except in compliance with the License.
* A copy of the License is located at
*
* http://aws.amazon.com/apache2.0
*
* or in the "license" file accompanying this file. This file is distributed
* on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either
* express or implied. See the License for the specific language governing
* permissions and limitations under the License.
*/
import java.text.DateFormat;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.TimeZone;
import com.amazonaws.AmazonClientException;
import com.amazonaws.AmazonServiceException;
import com.amazonaws.auth.AWSCredentials;
import com.amazonaws.auth.profile.ProfileCredentialsProvider;
import com.amazonaws.regions.Region;
import com.amazonaws.regions.Regions;
import com.amazonaws.services.marketplacecommerceanalytics.AWSMarketplaceCommerceAnalyticsClient;
import com.amazonaws.services.marketplacecommerceanalytics.model.GenerateDataSetRequest;
import com.amazonaws.services.marketplacecommerceanalytics.model.GenerateDataSetResult;
/**
* This sample demonstrates how to make basic requests to the AWS Marketplace Commerce 
* Analytics service using the AWS SDK for Java.
* <p>
* <b>Prerequisites:</b> Follow the on-boarding guide: {URL OR SOMETHING}
* <p>
* Fill in your AWS access credentials in the provided credentials file
* template, and be sure to move the file to the default location
* (~/.aws/credentials) where the sample code will load the credentials from.
* <p>
* <b>WARNING:</b> To avoid accidental leakage of your credentials, DO NOT keep
* the credentials file in your source directory.
* <p>
* http://aws.amazon.com/security-credentials
*/
public class MarketplaceCommerceAnalyticsSample {
public static void main(String[] args) throws ParseException {
/*
* The ProfileCredentialsProvider will return your [default]
* credential profile by reading from the credentials file located at
* (~/.aws/credentials).
*/
AWSCredentials credentials = null;
try {
credentials = new ProfileCredentialsProvider().getCredentials();
} catch (Exception e) {
throw new AmazonClientException("Cannot load the credentials from the credential profiles "
+ "file. Make sure that your credentials file is at the correct "
+ "location (~/.aws/credentials), and is in valid
format.", e);
}
AWSMarketplaceCommerceAnalyticsClient client = new AWSMarketplaceCommerceAnalyticsClient(credentials);
Region usEast1 = Region.getRegion(Regions.US_EAST_1);
client.setRegion(usEast1);
System.out.println("===============================================================");
System.out.println("Getting Started with AWS Marketplace Commerce Analytics Service"); 
System.out.println("===============================================================\n");
// Create a data set request with the desired parameters
GenerateDataSetRequest request = new GenerateDataSetRequest();
request.setDataSetType("customer_subscriber_hourly_monthly_subscriptions");
request.setDataSetPublicationDate(convertIso8601StringToDateUtc("2014-06-09T00:00:00Z"));
request.setRoleNameArn("arn:aws:iam::864545609859:role/MarketplaceCommerceAnalyticsRole");
request.setDestinationS3BucketName("awsmp-goldmine-seller");
request.setDestinationS3Prefix("java-sdk-test");
request.setSnsTopicArn("arn:aws:sns:us-west-2:864545609859:awsmp-goldmine-seller-topic");
System.out.println(
String.format("Creating a request for data set %s for publication date %s.",
request.getDataSetType(), request.getDataSetPublicationDate()));
try {
// Make the request to the service
GenerateDataSetResult result = client.generateDataSet(request);
// The Data Set Request ID is a unique identifier that you can use to correlate the
// request with responses on your Amazon SNS topic 
System.out.println("Request successful, unique ID: " + result.getDataSetRequestId());
} catch (AmazonServiceException ase) {
System.out.println("Caught an AmazonServiceException, which means your request made it "
+ "to the AWS Marketplace Commerce Analytics service, but was rejected with an " 
+ "error response for some reason.");
System.out.println("Error Message: " + ase.getMessage());
System.out.println("HTTP Status Code: " + ase.getStatusCode());
System.out.println("AWS Error Code: " + ase.getErrorCode());
System.out.println("Error Type: " + ase.getErrorType());
System.out.println("Request ID: " + ase.getRequestId());
} catch (AmazonClientException ace) {
System.out.println("Caught an AmazonClientException, which means the client encountered "
+ "a serious internal problem while trying to communicate with the AWS Marketplace"
+ "Commerce Analytics service, such as not being able to access the "
+ "network.");
System.out.println("Error Message: " + ace.getMessage());
}
}
private static Date convertIso8601StringToDateUtc(String dateIso8601) throws ParseException {
TimeZone utcTimeZone = TimeZone.getTimeZone("UTC");
DateFormat utcDateFormat = new SimpleDateFormat("yyyy-MM-dd'T'HH:mm:ssX");
utcDateFormat.setTimeZone(utcTimeZone);
return utcDateFormat.parse(dateIso8601);
}
}
```

You should expect results similar to this example\.

```
===============================================================
Getting Started with AWS Marketplace Commerce Analytics Service 
===============================================================
Creating a request for data set customer_subscriber_hourly_monthly_subscriptions for publication
date Sun Jun 08 17:00:00 PDT 2014.
Request successful, unique ID: c59aff81-6875-11e5-a6d8-fd5dbcaa74ab
```

## Technical documentation<a name="technical-documentation"></a>

 The service exposes one method, `GenerateDataSet`, which enables you to request datasets to be published to your Amazon S3 bucket\. The following table lists the parameters for `GenerateDataSet`\.


**Dataset parameters**  

| **Field** | **Description** | 
| --- | --- | 
| Data Set Type | This dataset will be returned as the result of the request\. | 
| Data Set Publication Date  |  The date a dataset was published\.  For daily datasets, provide a date with day\-level granularity for the desired day\.  For monthly datasets, provide a date with month\-level granularity for the desired month\. The day value is ignored\.   | 
| Role Name ARN | The ARN of the role with an attached permissions policy that provides the service with access to your resources\. | 
| Destination Amazon S3 Bucket Name | The name \(the friendly name, not the ARN\) of the destination Amazon S3 bucket\. Your datasets are published to this location\. | 
| Destination Amazon S3 Prefix |  \(Optional\) The Amazon S3 prefix for the published dataset, similar to a directory path in standard file systems\.  For example, if given the bucket name `mybucket` and the prefix `myprefix/mydatasets`, the output file is published to `s3://awsexamplebucket/myprefix/mydatasets/outputfile`\.  If the prefix directory structure doesn't exist, it's created\.  If no prefix is provided, the dataset is published to the Amazon S3 bucket root\.   | 
| SNS Topic ARN |   The ARN for the Amazon SNS topic that is notified when the dataset has been published or if an error occurs\.   | 

### Responses<a name="responses"></a>

The AWS Marketplace Commerce Analytics service returns two responses\. The first is synchronous, which is returned immediately, and the second is asynchronous, which is returned using the Amazon SNS\. The synchronous response is similar to this example\.


**Data set parameters**  

| **Field** | **Description** | 
| --- | --- | 
| Data Set Request ID  | A unique identifier representing a specific request to the service\. This identifier can be used to correlate a request with notifications on the Amazon SNS topic\.  | 

The asynchronous response is posted as a JSON\-formatted document to your Amazon SNS topic and is similar to this example\.


**Dataset parameters**  

|  **Field**  |  **Description**  | 
| --- | --- | 
| Data Set S3 Location  | The bucket name and key for the delivered dataset\.  | 
| Data Set Meta Data S3 Location  | The bucket name and key for the delivered dataset metadata file\.  | 
| Data Set Request ID  | A unique identifier representing a specific request to the service\. This identifier can be used to correlate a request with notifications on the Amazon SNS topic\.  | 
| Success  | "True" if the operation succeeded; "false" if not\.  | 
| Message  | \(Optional\) If an error occurred \(for example, "Success” is "false”\), this message contains information about the failure\.  | 

 **Example JSON\-formatted asynchronous response** 

```
 {    
   "dataSetS3Location":{
      "bucketName":"demo-bucket",
      "key":"demo-prefix/customer_subscriber_hourly_monthly_subscriptions_2014-06-09.csv"
   },
   "dataSetMetaDataS3Location":{
      "bucketName":"demo-bucket",
      "key":"demo-prefix/customer_subscriber_hourly_monthly_subscriptions_2014-06-09.meta.json"
   },
   "dataSetRequestId":"f65b7244-6862-11e5-80e2-c5127e17c023",
   "success":true
 }
```

### Outputs<a name="outputs"></a>

After a successful request, the requested dataset is delivered to your Amazon S3 bucket as a \.csv file\. A JSON\-formatted metadata file is published to the same location as the dataset file\. The metadata file provides useful information about the dataset and original request parameters\. The metadata file has the same name as the dataset file, but ends with the extension \.meta\.json\. The following table lists the metadata fields in the \.csv file\.


**Metadata fields**  

|  **Field**  |  **Description**  | 
| --- | --- | 
| Data Set Request ID  | A unique identifier representing a specific request to the service\. This identifier can be used to correlate a request with notifications on the Amazon SNS topic\.  | 
| Data Set Coverage Range  | Defines the start date/time and end date/time for the data coverage range\. These dates are in ISO 8601 format\.  | 
| Data Set Request Parameters  | The original request parameters to the GenerateDataSet method\.  | 
| Data Set S3 Location  | The bucket name and key for the delivered dataset\.  | 
| Data Set Meta Data S3 Location  | The bucket name and key for the delivered dataset metadata file\.  | 

Following is an example of JSON\-formatted metadata contents\. 

```
{
"dataSetRequestId": "43d7137b-8a94-4042-a09d-c41e87f371c1",
"dataSetCoverageRange": {
"startDateTime": "2014-06-08T00:00:00.000Z",
"endDateTime": "2014-06-08T23:59:59.000Z"
},
"dataSetRequestParameters": {
"sellerAccountId": "123412341234",
"dataSetType": "customer_subscriber_hourly_monthly_subscriptions",
"dataSetPublicationDate": "2014-06-09T00:00:00.000Z",
"roleNameArn": "arn:aws:iam::123412341234:role/MarketplaceCommerceAnalyticsRole",
"destinationS3BucketName": "demo-bucket",
"destinationS3Prefix": "demo_prefix/customer_subscriber_hourly_monthly_subscriptions",
"snsTopicArn": "arn:aws:sns:us-west-2:123412341234:demo-topic"
},
"dataSetS3Location": {
"bucketName": "demo-bucket",
"key": "demo_prefix/customer_subscriber_hourly_monthly_subscriptions_2014-06-09.csv"
},
"dataSetMetaDataS3Location": {
"bucketName": "demo-bucket",
"key": "demo_prefix/customer_subscriber_hourly_monthly_subscriptions_2014-06-09.meta.json"
}
}
```

For a complete list of available datasets, including availability dates, refer to the [AWS SDK documentation](https://docs.aws.amazon.com/cli/latest/reference/marketplacecommerceanalytics/generate-data-set.html#options)\. 

## Troubleshooting<a name="troubleshooting"></a>

This sections describes solutions to issues you may encounter with using the AWS Marketplace Commerce Analytics Service\. 

 **I can't access the service because of an allow list issue\.** 

If you're not yet registered as a seller on the AWS Marketplace, visit [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management) to register\. If you have already registered as a seller on AWS Marketplace, contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

**I can't request datasets for a date in the past, even though the SDK documentation says it should be available for this date\.** 

Even though datasets are listed as being available for certain dates in the past, we have data only since the time that you joined AWS Marketplace\. If you believe that this is in error, contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

 **When I call the service, I receive the error message "Could not connect to the endpoint URL: https://marketplacecommerceanalytics\.eu\-central\-1\.amazonaws\.com/”** 

Currently, the AWS Marketplace Commerce Analytics Service is available only in the US East \(N\. Virginia\) Region\. You must make all calls to the Commerce Analytics Service to the `us-east-1` endpoint\. 

If you're using the AWS CLI, add the "`--region` flag to each call and specify the AWS Region as `us-east-1`, as shown in the following example\.

```
aws marketplacecommerceanalytics generate-data-set \
--data-set-type "customer_subscriber_hourly_monthly_subscriptions" \
--data-set-publication-date "2016-04-21T00:00:00Z" \
--role-name-arn "arn:aws:iam::138136086619:role/MarketplaceCommerceAnalyticsRole" \
--destination-s3-bucket-name "marketplace-analytics-service" \
--destination-s3-prefix "test-prefix" \
--sns-topic-arn "arn:aws:sns:eu-central-1:138136086619:Marketplace_Analytics_Service_Notice" \
 --region us-east-1
```

 **I want to use a different Amazon S3 bucket or Amazon SNS topic than the ones I selected when I went through the on\-boarding process\.** 

When enrolling in the AWS Marketplace Commerce Analytics Service, you specified an Amazon S3 bucket and Amazon SNS topic\. The onboarding process configures your IAM permissions to allow the service access to only these specific resources\. To use different resources, you need to modify your IAM policy: 

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1.  Choose ** Roles** on the left side of the IAM console\. 

1.  Choose **MarketplaceCommerceAnalyticsRole**\. 

1.  Expand the **Inline Roles** section, if not already expanded\. 

1.  Locate the policy with a name that starts with *oneClick\_MarketplaceCommerceAnalyticsRole* and choose **Edit Policy**\. 

1.  In the policy document, locate the section that specifies actions related to the service that you want to modify\. For example, to change your Amazon S3 bucket, locate the section that includes the actions that start with **s3:** and change their respective **Resource** selection to specify your new Amazon S3 bucket\.

 For additional information about IAM policies, see the following guide: [https://docs\.aws\.amazon\.com/IAM/latest/UserGuide/access\_policies\.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) 

**I get an `AccessDeniedException` error when I call the `GenerateDataSet` action**

This can happen if your IAM user doesn't have the permissions necessary to call `GenerateDataSet`\. The following procedure outlines the steps needed to update an IAM policy with those permissions using the IAM console\.

**To get the GenerateDataSet permissions**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. From the navigation pane on the right, choose **Users**\.

1. Choose the IAM user whose credentials you want to use for the `marketplacecommerceanalytics` AWS CLI commands to open the **Summary** page\.

1. From the **Permissions** tab, choose **Add inline policy**

1. Open the **JSON** tab and paste the following code:

   ```
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Action": "marketplacecommerceanalytics:GenerateDataSet",
         "Resource": "*",
       },
     ],a
   }
   ```

1. Choose **Review policy**, provide the inline policy with a descriptive name, like *GenerateDataSetPolicy*, and choose **Create policy**\.

After updating the permissions, run the AWS CLI command again with the same credentials as this IAM user to complete the action\. 

For more information, see [Creating Policies in the IAM console](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-json-editor) in the *IAM User Guide*\.

 **My problem isn't listed here\.**

 Contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 