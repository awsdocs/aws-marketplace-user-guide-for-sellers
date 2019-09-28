# Configuring Your SaaS Product to Accept New Customers<a name="configuring-your-saas-application-to-accept-new-customers"></a>

 The following process takes place when customers purchase your product\. 

## In AWS Marketplace<a name="saas-app-config-asw-side"></a>

1.  When a customer visits your product page on the AWS Marketplace website, they choose to subscribe to your product\. 

1.  The customer’s AWS account is subscribed to your product\. This means metering records sent from your product become part of the customer’s AWS bill\. 

1.  A registration token is generated for the customer that contains their customer identiﬁer to your website\. 

1.  The customer is redirected to your registration page\. This page must be able to accept the token with the customer’s identiﬁer\. 

## In Your Product<a name="in-your-application"></a>

1.  The customer’s browser sends a POST request to your SaaS registration URL\. The request contains one POST parameter, *x\-amzn\-marketplace\-token*, containing the customer’s registration token\. From the perspective of your registration website, the customer has submitted a form with this parameter\. The registration token is an opaque string\. 

1.  To redeem this token for a customer identifier and a product code, your website must call [ResolveCustomer](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_ResolveCustomer.html) on the AWS Marketplace Metering Service\. The customer identifier is a string that represents a customer who is subscribed to your product\. The customer identiﬁer isn't the customer’s AWS account ID, but it's universal between products\. The product code is a unique string for your SaaS product that AWS provides to you\. Each AWS product has one unique product code, which is assigned to you during registration\. For example, a290sds6en72spp3ph4q890es is a product code, and b53a9230\-6767\-4735\-a3d9\-d5c41caa24c4 is a product ID\.

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

1.  Your website validates that the product code matches your SaaS product identity\. 

1.  Your website must keep this customer identiﬁer in the customer’s session\. It can be stored temporarily on your server, or it can be part of a signed session cookie on the customer’s browser\. 

1.  The customer is instructed to either create an account in your product or sign in to an existing account\. 

1.  The customer is now signed in to your website using credentials speciﬁc to that SaaS product\. In your accounts database, you can have a row for each customer\. Your accounts database must have a column for the AWS customer identiﬁer, which you populate with the customer identiﬁer that you obtained in step 2\. Verify that no other accounts in your system share this customer identiﬁer\. Otherwise, you might send conﬂicting metering records\. 

1.  During your seller registration process, you are assigned an Amazon SNS topic that notifies you when customers subscribe or unsubscribe to your system\. The notification is an Amazon SNS notiﬁcation in JSON format that informs you of customer actions\. AWS whitelists your account to enable you to listen to these notiﬁcations on an Amazon SNS topic\.

   We recommend that you use Amazon Simple Queue Service \(Amazon SQS\) to capture these messages\. After you receive a subscription notification with `subscribe-success`, the customer account is ready for metering\. Records that you send before this notification aren't metered\. For information on how to do this, see [Step 2: Give Permission to the Amazon SNS Topic to Send Messages to the Amazon SQS Queue](https://docs.aws.amazon.com/sns/latest/dg/sns-sqs-as-subscriber.html#SendMessageToSQS.sqs.permissions) in the *Amazon Simple Notification Service Developer Guide*\.

   If you have a SaaS contracts product, you also get an `entitlement-updated` notification when the contract is created\. Your accounts database must have an extra column for the subscription state\. The following is an example of a `subscribe-success` subscription notification\.

   ```
       {
       "action": "subscribe-success",
       "customer-identifier": "T1VJRC0xMjM0MTIzNDEyMzQtNTY3ODU2ODc1Nj",
       "product-code": "72m8mmj6t2dgb8dfscnpsbfmn"
       }
   ```
**Note**  
 Do not activate a product subscription unless you receive a SUBSCRIPTION\_SUCCESSFUL notification\. 

1.  You use the customer identiﬁer stored in your database to meter for usage through the AWS Marketplace Metering Service or check for entitlements through the AWS Marketplace Entitlement Service\. 