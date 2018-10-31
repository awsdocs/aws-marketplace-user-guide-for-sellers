# Subscription Notiﬁcations<a name="subscription-notification"></a>

 To receive notifications, you subscribe to the AWS Marketplace SNS topic provided to you during the product listing\. The topic provides notiﬁcations about changes to customers’ subscription and entitlement statuses\. This enables you to know when to provide and revoke access for speciﬁc customers\. 

## Subscribing an SQS Queue to the SNS Topic<a name="subscribing-an-sqs-queue-to-the-sns-topic"></a>

 We recommend subscribing an AWS SQS queue to the provided SNS topic\. Detailed instructions on creating an SQS queue can be found at [Tutorial: Creating an Amazon SQS Queue](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-create-queue.html)\. Instructions for subscribing the queue to the provided topic can be found at [Tutorial: Subscribing an Amazon SQS Queue to an Amazon SNS Topic](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-subscribe-queue-sns-topic.html)\. 

## Granting Permissions to Access the Queue<a name="granting-permissions-to-access-the-queue"></a>

 When you subscribe the SQS queue to the provided SNS topic, permissions are automatically added to allow the SNS topic to publish messages to the queue\. However, you still need an AWS Identity and Access Management \(IAM\) policy for granting the API user access to the queue\. This can be applied to the same user, if the services run with the same credentials\. Create a policy with the following contents, and attach it to your IAM user or role\. 

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
 The *Resource* ﬁeld is your SQS Queue ARN\. 

## Polling the SQS Queue for Notiﬁcations<a name="polling-the-sqs-for-notifications"></a>

 Finally, you need to deﬁne a service that continually polls the queue, looking for messages, and handling them accordingly\. 

 Example of polling the SQS queue for notifications 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-polling-sqs-queue.png)

 **Note**: As a *SaaS subscriptions* seller, you must handle four actions: *unsubscribe\-success, subscribe\- fail, unsubscribe\-pending, and unsubscribe\-success\.* As a **SaaS contracts** seller you will also get an *entitlement\-updated* SNS notification to let you know that a customer’s contract has been created, updated, renewed, or expired\. 

## **Updating SaaS Products**<a name="updating-saas-products"></a>

 Once your product is listed on AWS Marketplace, you are responsible for keeping the pricing and product information up\-to\-date\. You make changes to your listing from the [AWS Marketplace Management](https://aws.amazon.com/marketplace/management/) [Portal](https://aws.amazon.com/marketplace/management/)\. To make changes, from the **Listings** tab, under **Current Listings** submit the updated information 