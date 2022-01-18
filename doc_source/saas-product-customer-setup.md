# SaaS customer onboarding<a name="saas-product-customer-setup"></a>

 With SaaS subscriptions and SaaS contracts, your customers subscribe to your products through AWS Marketplace, but access the product in your AWS environment\. After subscribing to the product, your customer is directed to a website you create and manage as a part of your SaaS product to register their account and conﬁgure the product\. 

When creating your SaaS product listing, you provide a URL to your registration landing page\. We use that URL to redirect customers to your registration landing page after they subscribe\. On your software's registration landing page, you collect whatever information is required to create an account for the customer\. We recommend collecting your customer’s email addresses if you plan to contact them through email for usage notifications\.

The registration landing page needs to be able to identify and accept the `x-amzn-marketplace-token` token in the form data from AWS Marketplace with the customer’s identiﬁer for billing\. It should then pass that token value to the AWS Marketplace Metering Service and AWS Marketplace Entitlement Service APIs to resolve for the unique customer identiﬁer and corresponding product code\. For a code example, see [`ResolveCustomer` code example](saas-code-examples.md#saas-resolvecustomer-example)\.

## Configuring your SaaS product to accept new buyers<a name="configuring-your-saas-application-to-accept-new-customers"></a>

You're responsible for correctly configuring your SaaS software to accept new customers and meter them appropriately\. The following process outlines one recommended way of identifying, implementing, and metering a new customer's access to your software: 

1. When a customer visits your product page on the AWS Marketplace website, they choose to subscribe to your product\. 

1. The customer’s AWS account is subscribed to your product\. This means subscription and metering records sent from your product become part of the customer’s AWS bill\. 

1. A registration token is generated for the customer that contains their customer identiﬁer and your product code\.

1. The customer is redirected to your software's registration landing page\. This page must be able to accept the token with the customer’s identiﬁer\. 

1. The customer’s browser sends a POST request to your software's registration landing page URL\. The request contains one POST parameter, *x\-amzn\-marketplace\-token*, containing the customer’s registration token\. From the perspective of your registration website, the customer has submitted a form with this parameter\. The registration token is an opaque string\. 

1. To redeem this registration token for a customer identifier and a product code, your website must call [ResolveCustomer](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_ResolveCustomer.html) on the AWS Marketplace Metering Service\. The customer identiﬁer isn't the customer’s AWS account ID, but it's universal between products and should be saved to an internal source as part of your customer records\. The product code is a unique string for your SaaS product that AWS provides to you\. Each AWS product has one unique product code, which is assigned to you during registration\.
**Note**  
To see an example of a `ResolveCustomer` call, see [`ResolveCustomer` code example](saas-code-examples.md#saas-resolvecustomer-example)\.

1. Your website validates that the product code returned matches your SaaS product the customer is attemping to access and calls `GetEntitlement` to return the entitlement data for the customer’s subscription\.

1.  The customer is instructed to either create an account in your product or sign in to an existing account\. 

1.  The customer is now signed in to your website using credentials speciﬁc to that SaaS product\. In your accounts database, you can have an entry for each customer\. Your accounts database must have a column for the AWS customer identiﬁer, which you populate with the customer identiﬁer that you obtained in step 6\. Verify that no other accounts in your system share this customer identiﬁer\. For customers who subscribe to multiple products through AWS Marketplace, the customer identifier will remain the same, with each subscription having a unique product code\. 

1.  During your seller registration process, you subscribe to Amazon SNS topics that notify you when customers subscribe or unsubscribe to your product\. These are Amazon SNS notiﬁcations in JSON format that inform you of customer actions:
   + Entitlement notification \- For products with pricing models that include a contract, you are notified when buyers create a new contract, upgrade it, renew it, or it expires\. Your accounts database must have an extra column for the subscription state\. For more information, see [Amazon SNS topic: aws\-mp\-entitlement\-notification](saas-notification.md#saas-sns-message-body)\.
   + Subscription notification – For products with any pricing model, including contracts and subscriptions, you are notified when a buyer subscribes or unsubscribes to a product\. For more information, see [Amazon SNS topic: aws\-mp\-subscription\-notification](saas-notification.md#saas-sns-subscription-message-body)\.

   We recommend that you use Amazon Simple Queue Service \(Amazon SQS\) to capture these messages\. After you receive a subscription notification with `subscribe-success`, the customer account is ready for metering\. Records that you send before this notification aren't metered\. For information about how to do this, see [Step 2: Give Permission to the Amazon SNS Topic to Send Messages to the Amazon SQS Queue](https://docs.aws.amazon.com/sns/latest/dg/subscribe-sqs-queue-to-sns-topic.html#SendMessageToSQS.sqs.permissions) in the *Amazon Simple Notification Service Developer Guide*\.
**Note**  
Do not activate a product subscription unless you receive a `subscribe-success` notification\.

1.  Use the customer identiﬁer stored in your database to meter for usage through the AWS Marketplace Metering Service or check for entitlements through the AWS Marketplace Entitlement Service\. 

### Security and ordering<a name="security-and-ordering"></a>

 As a seller, it’s your responsibility to trust only customer identiﬁers that are immediately returned from AWS or those that your system has signed\. We recommend that you resolve the registration token immediately because it may expire after approximately 1 hour\. After you resolve the registration token, store the customer identiﬁer as a signed attribute on the customer’s browser session until the registration is complete\. 