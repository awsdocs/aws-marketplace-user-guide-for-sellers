# Pricing for SaaS subscriptions<a name="saas-subscriptions"></a>

For software as a service \(SaaS\) subscriptions, AWS Marketplace bills your customers based on the metering records that you send to us\. All charges must be measured and reported every hour from the software deployed in the customer's account\. All usage is then calculated monthly and billed monthly using the same mechanism as AMI based AWS Marketplace offerings\. Our ability to bill customers for usage of your product is dependent upon receiving metering records from you\. You are responsible for ensuring that your product’s metering records are successfully transmitted and received\. 

Before you can publish a SaaS product with subscription pricing, you must do the following:

1. Create a new SaaS product in the AWS Marketplace Management Portal, choose **New SaaS Subscription**\.

1. Complete the fields in the **General** tab with the necessary information\. Make a note of the product code\.

1. On the **Pricing** tab, under **Set Pricing**, select the **Category** that describes your product’s pricing most accurately\. The pricing category appears to customers on the AWS Marketplace website\. You can choose from **Bandwidth** \(GBps, MBps\), **Data** \(GB, MB, TB\), **Hosts** \(hours\), **Requests**, **Tiers** \(hours\), or **Users** \(hours\)\. If none of the predefined categories fit your needs, you can choose the more generic **Units** category\.

   Next, define your Pricing Dimensions\. Each Pricing Dimension represents a feature or service that you can set a per\-unit price for\. Examples of dimensions include users, hosts scanned, and GB of logs ingested\. You can define up to 24 dimensions\. For each dimension you define, you must add the following information: 
   + **Dimension API Name** – The API name used when sending metering records to the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html)\. This name indicates which dimension your customer used\. This name is visible in billing reports\. The name doesn't need to be reader\-friendly because you're the only one with access to your reports\. After you set the name, you can't change it\. 
   + **Dimension Description** – The customer\-facing statement that describes the dimension for the product\. The description can be no more than 70 characters and should be user\-friendly\. Examples of descriptions are Administrators per hour, and Per Mbps bandwidth provisioned\. After the product is published, you can't change this description\. 
   + **Dimension Rate** – The software charge per FCP unit for this product, in USD\. This ﬁeld supports three decimal places\. 

## When a SaaS subscription ends<a name="saas-subscription-ends"></a>

 A customer can unsubscribe from your SaaS subscription product through the AWS Management Console\. Key points of the SaaS subscription ending process include the following: 

1.  Your SaaS product is sent an `unsubscribe-pending` notiﬁcation through the Amazon SNS topic for that customer\.

1.  You have one hour to meter any remaining usage for the customer\. 

1.  After this hour, you receive an `unsubscribe-success` notiﬁcation\. At this point, you can no longer send metering records for this customer\. 

 It’s up to you to decide how you want to disable functionality in your SaaS product for unsubscribed customers\. For example, your product might complete the customer's existing work but prevent them from creating work\. You might want to display a message to the customer that their usage has been disabled\. Customers can resubscribe to your product through AWS Marketplace\. 

## When a SaaS subscription is cancelled<a name="saas-subscription-cancellations"></a>

Key points of the SaaS subscription cancellation process include the following: 

1. A customer can cancel their subscription to your SaaS subscription product the **Your Marketplace Software** page of the AWS Marketplace website\. 

   Your SaaS product is sent notiﬁcation through the Amazon SNS topic for that customer\.

1.  You have one hour to meter any remaining usage for the customer\. 

1. You notify the customer from your product that the cancellation is in progress\. If a customer indicates that they want to cancel through your product, direct the customer to AWS Marketplace\. To guarantee that there will be no future charges, customers should conﬁrm the cancellation with AWS Marketplace\. 