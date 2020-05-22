# Plan your SaaS product<a name="saas-prepare"></a>

Before you add your SaaS product to AWS Marketplace, you must first do some planning\. This step is critical to the success of your product\. A lack of planning can result in billing issues or you might have to re\-create your product in AWS Marketplace\.

**Important**  
Most of your product's settings can’t be changed after you've configured them\. If you need to change them after the product is created in AWS Marketplace, you probably need to create a new product with the correct settings\.

## Plan your pricing<a name="plan-pricing"></a>

There are three pricing options for SaaS products on AWS Marketplace\. Choosing the right pricing model for your product is the most important decision you will make\. Choosing the wrong pricing model can set you back by weeks, because it determines the payment options for your customers and the billing integration code you'll need to write, test, and deploy\.
+ **SaaS subscriptions** – A pay\-as\-you\-go model where buyers are billed for their hourly usage of your SaaS product\.
+ **SaaS contracts** – Buyers are either billed in advance for the use of your software, or you can offer them a flexible payment schedule\. 
+ **SaaS contracts with pay\-as\-you\-go** – This option is similar to a standard contract, however your customers can also pay for additional usage above their contract\. This is a blended pricing option, that gives your customers the most pricing options and it requires the most integration code on your end\.

For more information on pricing, see [Pricing SaaS products](saas-pricing-models.md)\.

## Plan your billing integration<a name="saas-plan-integration"></a>

One of the benefits of having a SaaS product on AWS Marketplace is consolidating billing\. In order to take advantage of this benefit, you must integrate with the AWS Marketplace Metering Service or the AWS Marketplace Entitlement Service, depending on your chosen pricing model\. These two services help you ensure that your billing and usage reporting is accurate\.

After you plan your integration, you must test the integration with your product before it goes live\. For more information about integration and testing, see [Accessing the AWS Marketplace Metering and Entitlement Service APIs](saas-integration-metering-and-entitlement-apis.md)\.

## Plan your Amazon SNS integration<a name="saas-plan-sns"></a>

There are two Amazon SNS topics that you can subscribe to for your SaaS product\. These messages can help you programmatically handle changes to subscriptions and contracts initiated by AWS or by your customers\. You can use these Amazon SNS notifications as programmatic triggers to enable a customer to register for a new account in on your product registration website, to deny customers with expired subscriptions from accessing your product, depending on how you program the handling of these notifications\.

## Plan how customers will access your product<a name="saas-plan-customer-access"></a>

This section describes how to make your product accessible to buyers\. 

### Plan your SaaS product registration Website<a name="saas-plan-registration"></a>

Customers who buy your SaaS product need to access to it\. You must plan and implement how you want your customers to access the product\. SaaS products support the following access options:
+ AWS PrivateLink
+ Your own product website

#### Using AWS PrivateLink for customers to access your SaaS product<a name="saas-plan-privatelink"></a>

You can use [Using AWS PrivateLink with AWS Marketplace](privatelink.md) to conﬁgure your service as an Amazon Virtual Private Cloud \(Amazon VPC\) endpoint service\. Your customers can create a VPC endpoint and access your software across the AWS Cloud virtual network\. Alternatively, you can provide access to your software product through a website you own and maintain, with customers creating a connection across the internet\.

#### Using your own registration website<a name="saas-plan-website"></a>

 Your SaaS product is hosted in your environment and it must be accessed over the internet through a public endpoint that you manage and maintain, like a website\. Typically, you have a website that customers use to register for your product, sign in to use the product, and access support for your product\. For the sake of simplicity, this endpoint will be referred to as your *registration website*\.

If you choose this access option and your product doesn't already have a registration website, you need to create one\. After you have a registration website, your website must be programmed to validated customers whenever they access your registration page\.

**To validate customers using your registration website**

1. Accept POST requests that includes the temporary token `x-amzn-marketplace-token`\.

1. Exchange the token for a `customerID` by calling [ResolveCustomer](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_ResolveCustomer.html) in the AWS Marketplace Metering Service\.

1.  After obtaining a `customerID`, persist it in your application for future calls\.

1. With the `customerID`, call [GetEntitlement](https://docs.aws.amazon.com/marketplaceentitlement/latest/APIReference/API_GetEntitlements.html) in the AWS Marketplace Entitlement Service to verify which dimension the customer is subscribed to and the quantity\.

1. After you've verified your customer's access and entitlement, program your application to ensure that the customer doesn't exceed what they're entitled to\.