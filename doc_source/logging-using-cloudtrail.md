# Logging AWS Marketplace API Calls with AWS CloudTrail<a name="logging-using-cloudtrail"></a>

The AWS Marketplace SaaS subscription service enables you to create software as a service \(SaaS\) products that are billed based on usage in one of four categories: users, data, bandwidth, or hosts\. You send billing information to AWS Marketplace using the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) API\. You must send billing information hourly to bill the customer\. Using AWS CloudTrail, you can monitor activity to ensure that your billing information is being sent to AWS Marketplace\. 

AWS Marketplace is integrated with AWS CloudTrail, a service that provides a record of actions taken by a user, role, or an AWS service in AWS Marketplace\. CloudTrail captures API calls for AWS Marketplace as events\. The calls captured include calls from the AWS Marketplace console and code calls to the AWS Marketplace API operations\. If you create a trail, you can enable continuous delivery of CloudTrail events to an Amazon S3 bucket, including events for AWS Marketplace\. If you don't configure a trail, you can still view the most recent events in the CloudTrail console in **Event history**\. Using the information collected by CloudTrail, you can determine the request that was made to AWS Marketplace, the IP address that the request was made from, who made the request, when it was made, and additional details\. 

To learn more about CloudTrail, including how to configure and enable it, see the [AWS CloudTrail User Guide](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.

## AWS Marketplace Information in CloudTrail<a name="service-name-info-in-cloudtrail"></a>

CloudTrail is enabled on your AWS account when you create the account\. When supported event activity occurs in AWS Marketplace, that activity is recorded in a CloudTrail event along with other AWS service events in **Event history**\. You can view, search, and download recent events in your account\. For more information, see [Viewing Events with CloudTrail Event History](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events.html)\. 

For an ongoing record of events in your AWS account, including events for AWS Marketplace, create a trail\. A *trail* enables CloudTrail to deliver log files to an Amazon S3 bucket\. By default, when you create a trail in the console, the trail applies to all AWS Regions\. The trail logs events from all Regions in the AWS partition and delivers the log files to the Amazon S3 bucket that you specify\. Additionally, you can configure other AWS services to further analyze and act upon the event data collected in CloudTrail logs\. For more information, see the following: 
+ [Overview for Creating a Trail](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html)
+ [AWS Service Integrations with CloudTrail Logs](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-aws-service-specific-topics.html#cloudtrail-aws-service-specific-topics-integrations)
+ [Configuring Amazon SNS Notifications for CloudTrail](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/getting_notifications_top_level.html)
+ [Receiving CloudTrail Log Files from Multiple Regions](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/receive-cloudtrail-log-files-from-multiple-regions.html) and [Receiving CloudTrail Log Files from Multiple Accounts](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-receive-logs-from-multiple-accounts.html)

AWS Marketplace supports logging the `BatchMeterUsage` action as events in CloudTrail log files\. Every event or log entry contains information about who generated the request\. The identity information helps you determine the following: 
+ Whether the request was made with root or AWS Identity and Access Management \(IAM\) user credentials
+ Whether the request was made with temporary security credentials for a role or federated user
+ Whether the request was made by another AWS service

For more information, see the [CloudTrail userIdentity Element](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference-user-identity.html)\.

## Example: AWS Marketplace Log File Entries<a name="understanding-service-name-entries"></a>

A trail is a configuration that enables delivery of events as log files to an Amazon S3 bucket that you specify\. CloudTrail log files contain one or more log entries\. An event represents a single request from any source and includes information about the requested action, the date and time of the action, request parameters, and so on\. CloudTrail log files aren't an ordered stack trace of the public API calls, so they don't appear in any specific order\.

The following example shows a CloudTrail log entry that demonstrates the action\.

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
            "sourceIPAddress": "203.0.113.0/24",
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
                        "meteringRecordId": "b52e6ed6-98f0-4e90-8bd2-bf01b024961e",
                        "status": "Success"
                    }
                ],
                "unprocessedRecords": [ ]
            },
            "requestID": "d45f8acd-251d-11e7-8d11-1f3d1d72808b",
            "eventID": "cace04c7-e6c2-465d-b47f-1506ee1ed497",
            "readOnly": false,
            "eventType": "AwsApiCall",
            "recipientAccountId": "123456789012"
        }
  ]
}
```