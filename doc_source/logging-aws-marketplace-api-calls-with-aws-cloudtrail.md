# Logging AWS Marketplace API calls with AWS CloudTrail<a name="logging-aws-marketplace-api-calls-with-aws-cloudtrail"></a>

 AWS Marketplace is integrated with CloudTrail, a service that provides a record of actions taken by a user, role, or an AWS service in AWS Marketplace\. CloudTrail captures API calls for AWS Marketplace as events\. The calls captured include calls from the AWS Marketplace console and code calls to the AWS Marketplace API operations\.

 CloudTrail is enabled on your AWS account when you create the account\. When supported event activity occurs in AWS Marketplace, that activity is recorded in a CloudTrail event along with other AWS service events in **Event history**\. You can view, search, and download recent events in your account\.

 Every event or log entry contains information about who generated the request\. The identity information helps you determine the following: 
+  Whether the request was made with root or AWS Identity and Access Management \(IAM\) user credentials\.
+  Whether the request was made with temporary security credentials for a role or a federated user\.
+  Whether the request was made by another AWS service\.

AWS Marketplace supports logging the `BatchMeterUsage` operation as events in CloudTrail log ﬁles\.

## AWS Marketplace log file entry examples<a name="example-aws-marketplace-log-file-entries"></a>

### Example: BatchMeterUsage<a name="example-aws-marketplace-log-file-entries-batchmeterusage"></a>

The following example shows a CloudTrail log entry that demonstrates the `BatchMeterUsage` action from the AWS Marketplace Metering Service\. 

```
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

### Example: RegisterUsage for containers<a name="example-aws-marketplace-log-file-entries-registerusage-containers"></a>

The following example shows a CloudTrail log entry that demonstrates the `RegisterUsage` action from the AWS Marketplace Metering Service\. 

```
{
    "eventVersion": "1.05",
    "userIdentity": {
        "type": "AssumedRole",
        "principalId": "EX_PRINCIPAL_ID:botocore-session-1111111111",
        "arn": "arn:aws:sts::123456789012:assumed-role/Alice/botocore-session-1111111111",
        "accountId": "123456789012",
        "accessKeyId": "EXAMPLE_KEY_ID",
        "sessionContext": {
            "sessionIssuer": {
                "type": "Role",
                "principalId": "EX_PRINCIPAL_ID",
                "arn": "arn:aws:iam::123456789012:role/Alice",
                "accountId": "123456789012",
                "userName": "Alice"
            },
            "webIdFederationData": {
                "federatedProvider": "arn:aws:iam::123456789012:oidc-provider/oidc.eks.us-east-1.amazonaws.com/id/EXAMPLEFA1C58F08CDB049167EXAMPLE",
                "attributes": {}
            },
            "attributes": {
                "mfaAuthenticated": "false",
                "creationDate": "2020-07-23T02:19:34Z"
            }
        }
    },
    "eventTime": "2020-07-23T02:19:46Z",
    "eventSource": "metering-marketplace.amazonaws.com",
    "eventName": "RegisterUsage",
    "awsRegion": "us-east-1",
    "sourceIPAddress": "1.2.3.4",
    "userAgent": "aws-cli/1.18.103 Python/3.8.2 Linux/4.14.181-142.260.amzn2.x86_64 botocore/1.17.26",
    "requestParameters": {
        "productCode": "EXAMPLE_proCode",
        "publicKeyVersion": 1
    },
    "responseElements": {
        "signature": "eyJhbGciOiJQUzI1Ni..."
    },
    "requestID": "dEXAMPLE-251d-11e7-8d11-1f3EXAMPLE8b",
    "eventID": "cEXAMPLE-e6c2-465d-b47f-150EXAMPLE97",
    "eventType": "AwsApiCall",
    "recipientAccountId": "123456789012"
}
```

### Example: MeterUsage for containers on Amazon EKS<a name="example-aws-marketplace-log-file-entries-meterusage"></a>

The following example shows a CloudTrail log entry that demonstrates the `MeterUsage` action from the AWS Marketplace Metering Service for containers on Amazon EKS\. 

```
{
    "eventVersion": "1.05",
    "userIdentity": {
        "type": "AssumedRole",
        "principalId": "EX_PRINCIPAL_ID:botocore-session-1111111111",
        "arn": "arn:aws:sts::123456789012:assumed-role/Alice/botocore-session-1111111111",
        "accountId": "123456789012",
        "accessKeyId": "EXAMPLE_KEY_ID",
        "sessionContext": {
            "sessionIssuer": {
                "type": "Role",
                "principalId": "EX_PRINCIPAL_ID",
                "arn": "arn:aws:iam::123456789012:role/Alice",
                "accountId": "123456789012",
                "userName": "Alice"
            },
            "webIdFederationData": {
                "federatedProvider": "arn:aws:iam::123456789012:oidc-provider/oidc.eks.us-east-1.amazonaws.com/id/EXAMPLEFA1C58F08CDB049167EXAMPLE",
                "attributes": {}
            },
            "attributes": {
                "mfaAuthenticated": "false",
                "creationDate": "2020-07-23T01:03:26Z"
            }
        }
    },
    "eventTime": "2020-07-23T01:38:13Z",
    "eventSource": "metering-marketplace.amazonaws.com",
    "eventName": "MeterUsage",
    "awsRegion": "us-east-1",
    "sourceIPAddress": "1.2.3.4",
    "userAgent": "aws-cli/1.18.103 Python/3.8.2 Linux/4.14.181-142.260.amzn2.x86_64 botocore/1.17.26",
    "requestParameters": {
        "timestamp": "Jul 23, 2020 1:35:44 AM",
        "usageQuantity": 1,
        "usageDimension": "Dimension1",
        "productCode": "EXAMPLE_proCode"
    },
    "responseElements": {
        "meteringRecordId": "bEXAMPLE-98f0-4e90-8bd2-bf0EXAMPLE1e"
    },
    "requestID": "dEXAMPLE-251d-11e7-8d11-1f3EXAMPLE8b",
    "eventID": "cEXAMPLE-e6c2-465d-b47f-150EXAMPLE97",
    "eventType": "AwsApiCall",
    "recipientAccountId": "123456789012"
}
```

### Example: MeterUsage on AMIs<a name="example-aws-marketplace-log-file-entries-meterusage-amis"></a>

The following example shows a CloudTrail log entry that demonstrates the `MeterUsage` action from the AWS Marketplace Metering Service for AMIs\. 

```
{
    "eventVersion": "1.05",
    "userIdentity": {
        "type": "AssumedRole",
        "principalId": "EX_PRINCIPAL_ID:i-exampled859aa775c",
        "arn": "arn:aws:sts::123456789012:assumed-role/Alice/i-exampled859aa775c",
        "accountId": "123456789012",
        "accessKeyId": "EXAMPLE_KEY_ID",
        "sessionContext": {
            "sessionIssuer": {
                "type": "Role",
                "principalId": "EX_PRINCIPAL_ID",
                "arn": "arn:aws:iam::123456789012:role/Alice",
                "accountId": "123456789012",
                "userName": "Alice"
            },
            "webIdFederationData": {},
            "attributes": {
                "mfaAuthenticated": "false",
                "creationDate": "2020-07-10T23:05:20Z"
            },
            "ec2RoleDelivery": "1.0"
        }
    },
    "eventTime": "2020-07-10T23:06:42Z",
    "eventSource": "metering-marketplace.amazonaws.com",
    "eventName": "MeterUsage",
    "awsRegion": "us-east-1",
    "sourceIPAddress": "1.2.3.4",
    "userAgent": "aws-cli/1.16.102 Python/2.7.16 Linux/4.14.133-113.112.amzn2.x86_64 botocore/1.12.92",
    "requestParameters": {
        "productCode": "EXAMPLE_proCode",
        "timestamp": "Jul 10, 2020 11:06:41 PM",
        "usageDimension": "Dimension1",
        "usageQuantity": 1,
        "dryRun": false
    },
    "responseElements": {
        "meteringRecordId": "bEXAMPLE-98f0-4e90-8bd2-bf0EXAMPLE1e"
    },
    "requestID": "dEXAMPLE-251d-11e7-8d11-1f3EXAMPLE8b",
    "eventID": "cEXAMPLE-e6c2-465d-b47f-150EXAMPLE97",
    "eventType": "AwsApiCall",
    "recipientAccountId": "123456789012"
}
```

## Related Topics<a name="saas-ct-related-topics"></a>

For more information, see the following topics in the *AWS CloudTrail User Guide*:
+  [Overview for Creating a Trail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html) 
+  [AWS Service Integrations with CloudTrail Logs](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-aws-service-specific-topics.html#cloudtrail-aws-service-specific-topics-integrations) 
+  [Conﬁguring Amazon SNS Notiﬁcations for CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/getting_notifications_top_level.html) 
+  [Receiving CloudTrail Log Files from Multiple Regions](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/receive-cloudtrail-log-files-from-multiple-regions.html) and [Receiving CloudTrail Log Files from Multiple Accounts](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-receive-logs-from-multiple-accounts.html) 
+  [CloudTrail userIdentity Element](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference-user-identity.html)\. 