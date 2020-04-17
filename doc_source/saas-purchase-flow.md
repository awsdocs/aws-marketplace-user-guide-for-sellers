# SaaS purchase flow<a name="saas-purchase-flow"></a>

 With SaaS subscriptions and SaaS contracts, your buyers subscribe to your products through AWS Marketplace, but access the product in your AWS environment\. After subscribing to the product, your buyer is directed to your website to register their account and conﬁgure the product\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-customer-billing-flow.png)

 When creating your product, you provide a URL to your registration landing page\. We use that URL to redirect buyers to your registration landing page after they subscribe using HTTPS\. The registration landing page needs to be able to accept a token from AWS Marketplace with the customer’s identiﬁer for billing\. This page should look for *x\-amzn\-marketplace\-token* in the form data\. It should then pass the registration token value to our API to resolve for the unique customer identiﬁer and corresponding product code\. These values are used to interact with the AWS MarketplaceMetering Service and AWS Marketplace Entitlement Service APIs, so store them with the associated record\. For more information, see [ResolveCustomer](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_ResolveCustomer.html) in the *AWS Marketplace Metering Service API*\.

 On the registration landing page, you collect whatever information is required to create an account for the buyer\. We recommend collecting your buyer’s email addresses if you plan to contact them via email for usage notifications\.

## Registration process<a name="registration-process"></a>

Buyers can ﬁnd all of the products that they have active subscriptions for under **Your Marketplace Software** on the AWS Marketplace website when they are signed in to their account\. This page contains a link to the page that buyers use to sign in to your SaaS product\. 

 Buyers access your SaaS product directly through your website or portal using credentials that you manage and provide\. 

### Cancellations<a name="cancellations"></a>

Buyers cancel SaaS subscription products through the **Your Marketplace Software** page of the AWS Marketplace website\. When a buyer cancels a subscription, you receive a notiﬁcation, and you have 1 hour to send a ﬁnal metering record for the buyer\. You notify the buyer from your product that the cancellation is in progress\. If a buyer indicates that they want to cancel through your product, direct the buyer to AWS Marketplace\. To guarantee that there will be no future charges, buyers should conﬁrm the cancellation with AWS Marketplace\. 

Buyers can request cancellations and refunds for SaaS contract products within 48 hours though AWS Support\. The full or prorated refund \(after some duration with the seller agreement\) is typically be granted in 3–5 business days\. When a buyer cancels a contract, you receive a notiﬁcation, and you have 1 hour to send a ﬁnal metering record for the buyer for any additional usage charges\. 