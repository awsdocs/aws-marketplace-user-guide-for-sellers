# Amazon SNS notifications for SaaS products<a name="saas-notification"></a>

To receive notifications, you subscribe to the AWS Marketplace Amazon Simple Notification Service \(Amazon SNS\) topics provided to you during product creation\. The topics provide notifications about changes to customers’ subscriptions and contract entitlements for your products\. This enables you to know when to provide and revoke access for specific customers\. 

**Note**  
During the product creation process, you'll receive the actual Amazon Resource Name \(ARN\) to the SNS topic\. For example: `arn:aws:sns:us-east-1:123456789012:aws-mp-subscription-notification-PRODUCTCODE`

The following Amazon SNS topics are available to software as a service \(SaaS\) products:
+ [Amazon SNS topic: `aws-mp-entitlement-notification`](#saas-sns-message-body) – This topic notifies you when buyers create a new contract, upgrade it, renew it, or it expires\. This is only available for products with pricing models that include a contract \(also known as **SaaS Contracts** and **SaaS Contracts with Consumption \(Overages\)**\)\.
+ [Amazon SNS topic: `aws-mp-subscription-notification`](#saas-sns-subscription-message-body) – This topic notifies you when a buyer subscribes to or unsubscribes from a product and includes the `offer-identifier` for private offers and a free trials flag for SaaS free trials\. This is available for all pricing models, including contracts and subscriptions \(also known as **SaaS Subscriptions**, **SaaS Contracts**, and **SaaS Contracts with Consumption \(Overages\)**\.

To learn more about the scenarios in which you respond to these notifications, see the following topics:
+ [Integrate your SaaS subscription product](saas-integrate-subscription.md)
+ [Integrate your SaaS contract product](saas-integrate-contract.md)
+ [Integrate your SaaS contract with pay\-as\-you\-go product](saas-integrate-contract-with-pay.md)

## Amazon SNS topic: `aws-mp-entitlement-notification`<a name="saas-sns-message-body"></a>

Each message in the `aws-mp-entitlement-notification` topic has the following format\.

```
{
    "action": "<action-name>",
    "customer-identifier": " X01EXAMPLEX",
    "product-code": "n0123EXAMPLEXXXXXXXXXXXX",
}
```

The *<action\-name>* will always be ` entitlement-updated`\. 

**Note**  
For entitlement messages, regardless of the action \(new, upgrade, renewal, or expired\), the message is the same\. A subsequent call to `GetEntitlement` is required to discover the content of the update\.
For **SaaS Contract with Consumption \(Overages\)**, sellers are provided with the [`aws-mp-subscription-notification` SNS topic](#saas-sns-subscription-message-body)\. This is an extra notification that a seller receives when they add on overage pricing\. When a seller acquires new customers, instead of only getting `entitlement-updated` \(which may refer to any kind of action\), the seller receives a subscribe message indicating that this is a new customer\.

Products with contract pricing \(including contracts with pay\-as\-you\-go\) must respond to these messages\. For more information about how to respond, see [Scenario: Monitor changes to user subscriptions](saas-integrate-contract.md#saas-contract-monitor-changes)\.

## Amazon SNS topic: `aws-mp-subscription-notification`<a name="saas-sns-subscription-message-body"></a>

Each message in the `aws-mp-subscription-notification` topic has the following format\.

```
{
    "action": "<action-name>",
    "customer-identifier": " X01EXAMPLEX",
    "product-code": "n0123EXAMPLEXXXXXXXXXXXX",
    "offer-identifier": "offer-abcexample123",
    "isFreeTrialTermPresent":"true"
}
```

The `offer-identifier` only appears in the notification if the offer is a *private offer*\.

The `isFreeTrialTermPresent` property indicates if the buyer's subscription is a free trial\. The JSON value of this property is not a *boolean* datatype\. Instead, the value is converted to a *string* datatype\. For more information, see [ SaaS free trials\.](https://docs.aws.amazon.com/marketplace/latest/userguide/saas-free-trials.html)

The *<action\-name>* will vary depending on the notification\. Possible actions are:
+ `subscribe-success` – The `subscribe-success` message signals when the seller can begin sending metering records\.
+ `subscribe-fail` – If the `subscribe-fail` message is generated, payment might have failed even though the buyer has already transitioned from the AWS Marketplace to the seller's SaaS landing page\. The seller should wait for the `subscribe-success` message before allowing consumption of the product\.
+ `unsubscribe-pending` – When a buyer unsubscribes, an `unsubscribe-pending` message is sent first\. This indicates that the seller has a limited time \(about one hour\) to get final metering records sent before the buyer is cancelled completely\. 
+ `unsubscribe-success` – The `unsubscribe-success` message signals the completion of cancellation, after which no further metering records will be accepted\.

**Note**  
If a buyer unsubscribes and then immediately successfully re\-subscribes before the final `unsubscribe-success` message is sent, the final `unsubscribe-success` message will not be sent and a `subscribe-success` message will be sent instead\. 

Products with subscription pricing \(including contracts with pay\-as\-you\-go\) must respond to these messages\. For more information about how to respond, see the following topics:
+ [Integrate your SaaS subscription product](saas-integrate-subscription.md)
+ [Integrate your SaaS contract with pay\-as\-you\-go product](saas-integrate-contract-with-pay.md)

## Subscribing an SQS queue to the SNS topic<a name="subscribing-an-sqs-queue-to-the-sns-topic"></a>

 We recommend subscribing an Amazon SQS queue to the provided SNS topics\. For detailed instructions on creating an SQS queue and subscribing the queue to a topic, see [ Subscribing an Amazon SQS queue to an Amazon SNS topic](https://docs.aws.amazon.com/sns/latest/dg/subscribe-sqs-queue-to-sns-topic.html) in the *Amazon Simple Notification Service Developer Guide*\.

**Note**  
You can only subscribe to AWS Marketplace SNS topics from the AWS account used to sell the products\. However, you can forward the messages to a different account\. For more information, see [Sending Amazon SNS messages to an Amazon SQS queue in a different account](https://docs.aws.amazon.com/sns/latest/dg/sns-send-message-to-sqs-cross-account.html) in the *Amazon Simple Notification Service Developer Guide*\.

### Polling the SQS queue for notifications<a name="polling-the-sqs-for-notifications"></a>

After you subscribe your SQS queue to an SNS topic, the messages are stored in SQS\. You must define a service that continually polls the queue, looks for messages, and handles them accordingly\.