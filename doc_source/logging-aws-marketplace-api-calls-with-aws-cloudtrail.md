# Logging AWS Marketplace API calls with AWS CloudTrail<a name="logging-aws-marketplace-api-calls-with-aws-cloudtrail"></a>

 AWS Marketplace is integrated with CloudTrail, a service that provides a record of actions taken by a user, role, or an AWS service in AWS Marketplace\. CloudTrail captures API calls for AWS Marketplace as events\. The calls captured include calls from the AWS Marketplace console and code calls to the AWS Marketplace API operations\.

 CloudTrail is enabled on your AWS account when you create the account\. When supported event activity occurs in AWS Marketplace, that activity is recorded in a CloudTrail event along with other AWS service events in **Event history**\. You can view, search, and download recent events in your account\.

 Every event or log entry contains information about who generated the request\. The identity information helps you determine the following: 
+  Whether the request was made with root or AWS Identity and Access Management \(IAM\) user credentials\.
+  Whether the request was made with temporary security credentials for a role or a federated user\.
+  Whether the request was made by another AWS service\.

AWS Marketplace supports logging the `BatchMeterUsage` operation as events in CloudTrail log ﬁles\.

## Example: AWS Marketplace Log File Entries<a name="example-aws-marketplace-log-file-entries"></a>

The following example shows a CloudTrail log entry that demonstrates the `BatchMeterUsage` action from the AWS Marketplace Metering Service\. 

```
    {
"Records": [
        {
            "eventVersion": "1.05",
            "userIdentity": { 
                "type": "IAMUser",
                "principalId": "EX_PRINCIPAL_ID",
                "arn": "arn:aws:iam::123456789012:user/Alice", 
                "accountId": "123456789012",
                "accessKeyId": "EXAMPLE_KEY_ID", 
                "userName": "Alice"
           },
           "eventTime": "2018-04-19T16:32:51Z",
           "eventSource": "metering-marketplace.amazonaws.com", 
           "eventName": "BatchMeterUsage",
           "awsRegion": "us-east-1", 
           "sourceIPAddress": "192.0.0.2/24", 
           "userAgent": "Coral/Netty14", 
           "requestParameters": {
               "usageRecords": [
                   {
                       "dimension": "Dimension1", 
                       "timestamp": "Apr 19, 2018 4:32:50 PM", 
                       "customerIdentifier": "customer1", 
                       "quantity": 1
                   }
               ],
               "productCode": "EXAMPLE_proCode"
           },
           "responseElements": { 
               "results": [
                   {
                       "usageRecord": {
                           "dimension": "Dimension1", 
                           "timestamp": "Apr 19, 2018 4:32:50 PM", 
                           "customerIdentifier": "customer1", 
                           "quantity": 1
                       },
                       "meteringRecordId": "bEXAMPLE-98f0-4e90-8bd2-bf0EXAMPLE1e", 
                       "status": "Success"
                   }
               ],
               "unprocessedRecords": [ ]
           },
           "requestID": "dEXAMPLE-251d-11e7-8d11-1f3EXAMPLE8b", 
           "eventID": "cEXAMPLE-e6c2-465d-b47f-150EXAMPLE97", 
           "readOnly": false,
           "eventType": "AwsApiCall", 
           "recipientAccountId": "123456789012"
       }
    ]
  }
```

## Related Topics<a name="saas-ct-related-topics"></a>

For more information, see the following topics in the *AWS CloudTrail User Guide*:
+  [Overview for Creating a Trail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html) 
+  [AWS Service Integrations with CloudTrail Logs](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-aws-service-specific-topics.html#cloudtrail-aws-service-specific-topics-integrations) 
+  [Conﬁguring Amazon SNS Notiﬁcations for CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/getting_notifications_top_level.html) 
+  [Receiving CloudTrail Log Files from Multiple Regions](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/receive-cloudtrail-log-files-from-multiple-regions.html) and [Receiving CloudTrail Log Files from Multiple Accounts](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-receive-logs-from-multiple-accounts.html) 
+  [CloudTrail userIdentity Element](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference-user-identity.html)\. 