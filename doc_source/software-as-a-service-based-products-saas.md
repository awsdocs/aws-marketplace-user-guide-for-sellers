# Software\-as\-a\-Service–Based Products<a name="software-as-a-service-based-products-saas"></a>

For software as a service \(SaaS\) products, you deploy software hosted on Amazon Web Services \(AWS\) infrastructure and you are responsible for granting AWS Marketplace customers access to the software\. There are no AMIs to conﬁgure, and your customers don't have to run your software on their own Amazon Elastic Compute Cloud \(Amazon EC2\) instances\. With SaaS, customers subscribe to products through AWS Marketplace, but they access the product in your environment\.

**Important**  
The content in this chapter is undergoing improvements, and the information available might be out of date\. For the latest information about getting started with your SaaS product on AWS Marketplace, see the [AWS Marketplace SaaS Listing Process & Integration Guide](https://awsmp-loadforms.s3.amazonaws.com/AWS+Marketplace+-+SaaS+Integration+Guide.pdf)\. The integration guide can help you understand each step of getting your product on AWS Marketplace\. You'll find integration diagrams for pricing models, code examples for interacting with our APIs, a list of frequently asked seller questions, and links to external resources that help you deep dive into the concepts presented throughout\.

AWS Marketplace oﬀers two pricing models for SaaS products:
+ SaaS subscriptions
+ SaaS contracts

With **SaaS subscriptions**, you track usage and customers pay only for what they use\. This pay\-as\-you go pricing model is familiar to your customers because it is similar to that of many AWS services\. You use the AWS Marketplace Metering Service to report metered usage to AWS Marketplace\. We use the metering data that you provide to bill customers for their usage of your SaaS product\. All charges must be measured and reported every hour\.

With **SaaS contracts**, customers commit to upfront payment for their expected usage for 1\-month, 1\-year, 2\-year, or 3\-year contract terms\. Customers are billed in advance for the use of your software, or you can offer them a flexible payment schedule\. For example, you might sell your customer a certain amount of storage per month for a year or a certain amount of end\-user licenses for two years\. You use the AWS Marketplace Entitlement Service to retrieve information about a customer’s contract and what it entitles them to\. Customers can also pay for additional usage that exceed their contract\. You use the AWS Marketplace Metering Service to report the additional usage to AWS\.

After a customer ﬁnds and subscribes to your SaaS product on AWS Marketplace, AWS Marketplace passes a billing identiﬁer to your website\. You use the billing identifier to call the AWS Marketplace Entitlement Service and the AWS Marketplace Metering Service\. Customer account creation, resource provisioning, and account management is done through your website or APIs\.

For both kinds of SaaS products, you can use [AWS PrivateLink](https://docs.aws.amazon.com/marketplace/latest/userguide/privatelink.html) technology to conﬁgure your service as an Amazon Virtual Private Cloud \(Amazon VPC\) endpoint service\. Your customers can create a VPC endpoint and access your software across the Amazon network\. Alternatively, you can provide access to your software product through your website, with customers creating a connection across the internet\.

## Comparing SaaS Subscriptions and SaaS Contracts<a name="saas-subscriptions-and-saas-contracts-comparison"></a>

To make your SaaS product available on AWS Marketplace, decide whether you will offer the SaaS subscriptions pricing model or the SaaS contracts pricing model\.

To review some example applications, see the following products on the AWS Marketplace Management Portal:

### SaaS Subscription Application Examples<a name="saas-subscription-examples"></a>
+ [SendGrid Email Delivery Service](https://aws.amazon.com/marketplace/pp/B074CQY6KB)
+ [Cisco Stealthwatch Cloud \| Public Cloud Monitoring \- Metered](https://aws.amazon.com/marketplace/pp/B075MWZVBM)

### SaaS Contract Application Examples<a name="saas-contracts-examples"></a>
+ [Informatica ETL for AWS SaaS Contract](https://aws.amazon.com/marketplace/pp/B06XXM7JJT)
+ [Cisco Stealthwatch Cloud \| Public Cloud Monitoring \- Contracts](https://aws.amazon.com/marketplace/pp/B076J22YD8)

### SaaS Amazon API Gateway Products<a name="saas-api-gateway"></a>

You can sell your Amazon API Gateway APIs on AWS Marketplace as SaaS products\. For more information on developing your API product, see the following:

#### Related Resources<a name="saas-api-gateway-resources"></a>
+ [API Gateway Developer Guide](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html) 
+ [Sell Your API Gateway APIs through AWS Marketplace](https://docs.aws.amazon.com/apigateway/latest/developerguide/sell-api-as-saas-on-aws-marketplace.html) in the *API Gateway Developer Guide* 
+ [A Serverless Developer Portal for easily publishing and cataloging APIs](https://github.com/awslabs/aws-api-gateway-developer-portal) on *GitHub* 