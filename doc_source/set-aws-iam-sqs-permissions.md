# Amazon SQS permissions<a name="set-aws-iam-sqs-permissions"></a>

 As part of the SaaS product publication process, AWS Marketplace provides you an Amazon SNS topic you can use to receive notifications if a customer's subscription or entitlement status changes\. You can configure one or more Amazon SQS queues to the topic so that the queues can take action on the notification\. For example, if a customer adds more storage to the subscription they have to your SaaS product, the Amazon SNS topic can send a message to an Amazon SQS queue that starts a process to automatically increase the storage capacity available to that customer\. 

 When you subscribe the Amazon Simple Queue Service \(Amazon SQS\) queue to the provided Amazon SNS topic, permissions are automatically added to allow the topic to publish messages to the queue\. However, you still need an IAM policy for granting the AWS Marketplace Metering and Entitlement Service API user access to the queue\. This can be applied to the same user if the services run with the same credentials\. Create a policy with the following contents and attach it to your IAM user or role\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "sqs:ReceiveMessage", "sqs:DeleteMessage", "sqs:GetQueueAttributes", "sqs:GetQueueUrl"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:sqs:REGION_HERE:XXXXXXXXXXXX:NAME_HERE"
        }
    ]
}
```

**Note**  
 The `Resource` ﬁeld is the Amazon Resource Name \(ARN\) of your Amazon SQS queue\. 

 For more information on message notification and queuing for your SaaS products, see [Subscribing an SQS queue to the SNS topic](saas-notification.md#subscribing-an-sqs-queue-to-the-sns-topic) and [Accessing the AWS Marketplace Metering and Entitlement Service APIs](saas-integration-metering-and-entitlement-apis.md)\. 