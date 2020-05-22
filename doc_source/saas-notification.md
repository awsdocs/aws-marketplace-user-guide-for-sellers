# Amazon SNS notifications for SaaS products<a name="saas-notification"></a>

To receive notifications, you subscribe to the AWS Marketplace Amazon SNS topic provided to you during product creation\. The topic provides notifications about changes to customers’ subscription and contract entitlement statuses\. This enables you to know when to provide and revoke access for specific customers\. 

The following Amazon SNS topics are specific to SaaS products:
+ `aws-mp-entitlement-notification` – This Amazon SNS topic is for SaaS contracts\. 
+ `aws-mp-subscription-notification` – This Amazon SNS topic is for SaaS subscriptions and contracts with additional consumption\.

**Note**  
If your product is priced for SaaS contracts with consumption, you must use both of these topics\.

## SaaS product Amazon SNS message body<a name="saas-sns-message-body"></a>

Each message for the SaaS product Amazon SNS notifications has the following format:

```
{
    "action": "action-name",
    "CustomerIdentifier": " X01EXAMPLEX",
    "ProductCode": "n0123EXAMPLEXXXXXXXXXXXX"
}
```

## SaaS product Amazon SNS actions<a name="saas-sns-actions"></a>

As a SaaS contract provider, you'll receive messages with the `aws-mp-entitlement-action` action\. When you get one of these messages, a subsequent call to the [GetEntitlement](https://docs.aws.amazon.com/marketplaceentitlement/latest/APIReference/API_GetEntitlements.html) AWS Marketplace Entitlement Service action is required to discover the content of the update\.

If you provide a SaaS subscription product \(or a SaaS contract with consumption product\), you'll receive messages with the following actions:
+ `subscribe-success`
+ `subscribe-fail`
+ `unsubscribe-pending`
+ `unsubscribe-success`

## Subscribing an SQS queue to the SNS topic<a name="subscribing-an-sqs-queue-to-the-sns-topic"></a>

 We recommend subscribing an Amazon SQS queue to the provided SNS topic\. For detailed instructions on creating an SQS queue and subscribing the queue to the provided topic, see [Tutorial: Creating an Amazon SQS Queue](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-create-queue.html) and [Tutorial: Subscribing an Amazon SQS Queue to an Amazon SNS Topic](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-subscribe-queue-sns-topic.html) in the *Amazon Simple Queue Service Developer Guide*\. 

## Polling the SQS queue for notifications<a name="polling-the-sqs-for-notifications"></a>

 Finally, you need to define a service that continually polls the queue, looks for messages, and handles them accordingly\.