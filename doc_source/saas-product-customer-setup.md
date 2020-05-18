# SaaS customer onboarding<a name="saas-product-customer-setup"></a>

 With SaaS subscriptions and SaaS contracts, your customers subscribe to your products through AWS Marketplace, but access the product in your AWS environment\. After subscribing to the product, your customer is directed to a website you create and manage as a part of your SaaS product to register their account and conﬁgure the product\. 

When creating your product, you provide a URL to your registration landing page\. We use that URL to redirect customers to your registration landing page after they subscribe\. On your software's registration URL, you collect whatever information is required to create an account for the customer\. We recommend collecting your customer’s email addresses if you plan to contact them through email for usage notifications\.

The registration landing page needs to be able to identify and accept the `x-amzn-marketplace-token` token in the form data from AWS Marketplace with the customer’s identiﬁer for billing\. It should then pass that token value to the AWS Marketplace Metering Service and AWS Marketplace Entitlement Service APIs to resolve for the unique customer identiﬁer and corresponding product code\. For a code example, see [ResolveCustomer code example](saas-code-examples.md#saas-resolvecustomer-example)\.

## Configuring your SaaS product to accept new buyers<a name="configuring-your-saas-application-to-accept-new-customers"></a>

You're responsible for correctly configuring your SaaS software to accept new customers and meter them appropriately\. The following process outlines one recommended way of identifying, implementing, and metering a new customer's access to your software: 

1. When a customer visits your product page on the AWS Marketplace website, they choose to subscribe to your product\. 

1. The customer’s AWS account is subscribed to your product\. This means metering records sent from your product become part of the customer’s AWS bill\. 

1. A registration token is generated for the customer that contains their customer identiﬁer to your website\. 

1. The customer is redirected to your software's registration URL\. This page must be able to accept the token with the customer’s identiﬁer\. 

1. The customer’s browser sends a POST request to your SaaS registration URL\. The request contains one POST parameter, *x\-amzn\-marketplace\-token*, containing the customer’s registration token\. From the perspective of your registration website, the customer has submitted a form with this parameter\. The registration token is an opaque string\. 

1. To redeem this token for a customer identifier and a product code, your website must call [ResolveCustomer](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_ResolveCustomer.html) on the AWS Marketplace Metering Service\. The customer identiﬁer isn't the customer’s AWS account ID, but it's universal between products\. The product code is a unique string for your SaaS product that AWS provides to you\. Each AWS product has one unique product code, which is assigned to you during registration\.

   The following is an example of a response to a `ResolveCustomer` call\.

   ```
           
       ##### Resolving Customer Registration Token ##### 
       formFields = urlparse.parse_qs(postBody):
       if formFields.has_key('x-amzn-marketplace-token'):
       marketplaceClient = boto3.client('meteringmarketplace') 
       customerData = marketplaceClient.resolve_customer( 
       RegistrationToken=formFields['x-amzn-marketplace-
       token']) productCode = customerData['ProductCode']
       customerId = customerData['CustomerIdentifier']
       # TODO: Store information away with your customer record
       # TODO: Validate no other accounts share this identifier
   ```

1. Your website validates that the product code matches your SaaS product identity\. Your website must keep this customer identiﬁer in the customer’s session\. It can be stored temporarily on your server, or it can be part of a signed session cookie on the customer’s browser\. 

1.  The customer is instructed to either create an account in your product or sign in to an existing account\. 

1.  The customer is now signed in to your website using credentials speciﬁc to that SaaS product\. In your accounts database, you can have a row for each customer\. Your accounts database must have a column for the AWS customer identiﬁer, which you populate with the customer identiﬁer that you obtained in step 2\. Verify that no other accounts in your system share this customer identiﬁer\. Otherwise, you might send conﬂicting metering records\. 

1.  During your seller registration process, you are assigned an Amazon SNS topic that notifies you when customers subscribe or unsubscribe to your system\. The notification is an Amazon SNS notiﬁcation in JSON format that informs you of customer actions\.

   We recommend that you use Amazon Simple Queue Service \(Amazon SQS\) to capture these messages\. After you receive a subscription notification with `subscribe-success`, the customer account is ready for metering\. Records that you send before this notification aren't metered\. For information about how to do this, see [Step 2: Give Permission to the Amazon SNS Topic to Send Messages to the Amazon SQS Queue](https://docs.aws.amazon.com/sns/latest/dg/sns-sqs-as-subscriber.html#SendMessageToSQS.sqs.permissions) in the *Amazon Simple Notification Service Developer Guide*\.

   If you have a SaaS contracts product, you also get an `entitlement-updated` notification when the contract is created\. Your accounts database must have an extra column for the subscription state\. The following is an example of a `subscribe-success` subscription notification\.

   ```
       {
       "action": "subscribe-success",
       "customer-identifier": "T1EXAMPLEjM0MTIzNDEyMzQtNTY3ODU2ODc1EXAMPLENj",
       "product-code": "72EXAMPLE2dgb8dfEXAMPLEmn"
       }
   ```
**Note**  
Do not activate a product subscription unless you receive a `SUBSCRIPTION_SUCCESSFUL` notification\.

1.  Use the customer identiﬁer stored in your database to meter for usage through the AWS Marketplace Metering Service or check for entitlements through the AWS Marketplace Entitlement Service\. 

### Security and ordering<a name="security-and-ordering"></a>

 As a seller, it’s your responsibility to trust only customer identiﬁers that are immediately returned from AWS or those that your system has signed\. We recommend that you resolve the registration token immediately because it expires after 1 hour\. After you resolve the registration token, store the customer identiﬁer as a signed attribute on the customer’s browser session until the registration is complete\. 