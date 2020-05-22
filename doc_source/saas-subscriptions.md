# Pricing for SaaS subscriptions<a name="saas-subscriptions"></a>

For SaaS subscriptions, AWS Marketplace bills your customers based on the metering records that you send to us\. Before you can publish a subscription\-based SaaS product you must do the following:

1. Create a new SaaS product in the AWS Marketplace Management Portal, and make a note of its product code\.

1. Complete the wizard with the necessary information\.

To set your pricing, select the category that best describes your product’s pricing\. The pricing category appears to customers on the AWS Marketplace website\. You can choose from bandwidth \(GBps, MBps\), data \(GB, MB, TB\), hosts, requests, tiers, or users\. If none of the predefined categories fit your needs, you can choose the more generic **units** category\.

Next, define your pricing dimensions\. Each pricing dimension represents a feature or service that you can set a per\-unit price for\. Examples of dimensions include users, hosts scanned, and GB of logs ingested\. You can define up to 24 dimensions\. For each dimension you define, you must add the following information: 
+ **Dimension API Name** – The API name used when sending metering records to the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html)\. This name indicates which dimension your customer used\. This name is visible in billing reports\. The name doesn't need to be reader\-friendly because you're the only one with access to your reports\. After you set the name, you can't change it\. 
+ **Dimension Description** – The customer\-facing statement that describes the dimension for the product\. The description \(administrators per hour, per Mbps bandwidth provisioned, etc\.\) can be no more than 70 characters and should be user\-friendly\. After the product is published, you can't change this description\. 
+ **Dimension Price** – The software charge per unit for this product, in USD\. This ﬁeld supports three decimal places\. 

## When a SaaS subscription ends<a name="saas-subscription-ends"></a>

 A customer can unsubscribe from your SaaS subscription product through the AWS Management Console\.

1.  Your SaaS product is sent an `unsubscribe-pending` notiﬁcation through the Amazon SNS topic for that customer\.

1.  You have one hour to meter any remaining usage for the customer\. 

1.  After this hour, you receive an `unsubscribe-success` notiﬁcation\. At this point, you can no longer send metering records for this customer\. 

 It’s up to you to decide how you want to disable functionality in your SaaS product for unsubscribed customers\. For example, your product might complete the customer's existing work, but prevent them from creating work\. You might want to display a message to the customer that their usage has been disabled\. Customers can resubscribe to your product through AWS Marketplace\. 

### Subscription Cancellations<a name="saas-subscription-cancellations"></a>

 Customers cancel SaaS subscription products through the **Your Marketplace Software** page of the AWS Marketplace website\. When a customer cancels a subscription, you receive a notiﬁcation, and you have 1 hour to send a ﬁnal metering record for the customer\. You notify the customer from your product that the cancellation is in progress\. If a customer indicates that they want to cancel through your product, direct the customer to AWS Marketplace\. To guarantee that there will be no future charges, customers should conﬁrm the cancellation with AWS Marketplace\. 

 Customers can request a cancellation and refund for SaaS contract products though AWS Support\. Customers must request refunds within 48 hours through AWS Support\. The full or prorated refund is typically granted in 3–5 business days\. When a customer cancels a contract, you receive a notiﬁcation, and you have 1 hour to send a ﬁnal metering record for the customer for any additional usage charges\. 