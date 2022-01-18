# Amazon SNS notifications for container products<a name="container-notification"></a>

To receive notifications, you subscribe to the AWS Marketplace Amazon Simple Notification Service \(Amazon SNS\) topics provided to you during product creation\. The topics provide notifications about changes to customers’ subscriptions for your products\. For example, you can use this to know when customers accept a private oﬀer\. 

**Note**  
Amazon SNS notifications are not supported for container\-based products with contract pricing\.

The following Amazon SNS topic is available for container products:
+ [Amazon SNS topic: `aws-mp-subscription-notification`](#container-sns-subscription-message-body) – This topic notifies you when a buyer subscribes or unsubscribes to a product\. This is available for hourly pricing models, including hourly and hourly with long term\.

## Amazon SNS topic: `aws-mp-subscription-notification`<a name="container-sns-subscription-message-body"></a>

Each message in the `aws-mp-subscription-notification` topic has the following format\.

```
{
    "action": "<action-name>",
    "customer-identifier": " X01EXAMPLEX",
    "product-code": "n0123EXAMPLEXXXXXXXXXXXX",
    "offer-identifier": "offer-abcexample123"
}
```

The *<action\-name>* will vary depending on the notification\. Possible actions are:
+ `subscribe-success`
+ `subscribe-fail`
+ `unsubscribe-pending`
+ `unsubscribe-success`

The `offer-identifier` only appears in the notification if the offer is a *private offer*\.

## Subscribing an Amazon SQS queue to the Amazon SNS topic<a name="subscribing-sqs-queue-to-sns-topic"></a>

We recommend subscribing an Amazon SQS queue to the provided SNS topics\. For detailed instructions on creating an SQS queue and subscribing the queue to a topic, see [ Subscribing an Amazon SQS queue to an Amazon SNS topic](https://docs.aws.amazon.com/sns/latest/dg/subscribe-sqs-queue-to-sns-topic.html) in the *Amazon Simple Notification Service Developer Guide*\.

**Note**  
You can only subscribe to AWS Marketplace SNS topics from the AWS account used to sell the products\. However, you can forward the messages to a different account\. For more information, see [Sending Amazon SNS messages to an Amazon SQS queue in a different account](https://docs.aws.amazon.com/sns/latest/dg/sns-send-message-to-sqs-cross-account.html) in the *Amazon Simple Notification Service Developer Guide*\.

### Polling the SQS queue for notifications<a name="polling-the-sqs-for-notifications"></a>

After you subscribe your SQS queue to an SNS topic, the messages are stored in SQS\. You must define a service that continually polls the queue, looks for messages, and handles them accordingly\.