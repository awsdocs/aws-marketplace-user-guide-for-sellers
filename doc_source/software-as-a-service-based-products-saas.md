# Software\-as\-a\-Service–Based Products<a name="software-as-a-service-based-products-saas"></a>

For software as a service \(SaaS\) products, you deploy software hosted on AWS infrastructure and you are responsible for granting AWS Marketplace customers access to the software\. There are no AMIs to conﬁgure, and your customers don't have to run your software on their own Amazon EC2 instances\. With SaaS, customers subscribe to products through AWS Marketplace, but access the product in your environment\.

**Important**  
The content in this chapter is undergoing improvements, and the information available might be out of date\. For the latest information on getting started with your SaaS product on AWS Marketplace, see the [AWS Marketplace SaaS Listing Process & Integration Guide](https://awsmp-loadforms.s3.amazonaws.com/AWS+Marketplace+-+SaaS+Integration+Guide.pdf)\. The integration guide can help you understand each step of getting your product on AWS Marketplace\. You'll find integration diagrams for pricing models, code examples for interacting with our APIs, a list of frequently asked seller questions, and links to external resources that help you deep dive into the concepts presented throughout\.

AWS Marketplace oﬀers two pricing models for SaaS products:
+ SaaS subscriptions
+ SaaS contracts

With **SaaS subscriptions**, you track usage and customers pay only for what they use\. This pay\-as\-you go pricing model is familiar to your customers because it is similar to that of many AWS services\. You use the AWS Marketplace Metering Service to report metered usage to AWS Marketplace\. We use the metering data that you provide to bill customers for their usage of your SaaS product\. All charges must be measured and reported every hour\.

With **SaaS contracts**, customers commit to upfront payment for their expected usage for 1\-month, 1\-year, 2\-year, or 3\-year contract terms\. Customers are billed in advance for the use of your software, or you can offer them a flexible payment schedule\. For example, you might sell your customer a certain amount of storage per month for a year or a certain amount of end\-user licenses for 2 years\. You use the AWS Marketplace Entitlement Service to retrieve information about a customer’s contract and what it entitles them to\. Customers can also pay for additional usage above their contract\. You use the AWS Marketplace Metering Service to report the additional usage to AWS\.

After a customer ﬁnds and subscribes to your SaaS product on AWS Marketplace, AWS Marketplace passes a billing identiﬁer to your website\. You use the billing identifier to call the AWS Marketplace Entitlement Service and the AWS Marketplace Metering Service\. Customer account creation, resource provisioning, and account management is done through your website or APIs\. Then customers access the product in your AWS environment or through a VPC endpoint service connection you create\.

For both kinds of SaaS products, you can use [AWS PrivateLink](https://docs.aws.amazon.com/marketplace/latest/userguide/privatelink.html) technology to conﬁgure your service as an Amazon Virtual Private Cloud \(Amazon VPC\) endpoint service\. Your customers can create a VPC endpoint and access your software across the Amazon network\. Alternatively, you can provide access to your software product through your website, with customers creating a connection across the Internet\.

## Comparing SaaS Subscriptions and SaaS Contracts<a name="saas-subscriptions-and-saas-contracts-comparison"></a>

To make your SaaS product available on AWS Marketplace, decide whether you will offer the SaaS subscriptions pricing model or the SaaS contracts pricing model\. The following table compares the two models\.


|   |  SaaS Subscriptions  |  SaaS Contracts  | 
| --- | --- | --- | 
| What are common industry names for each pricing model? | Metered pricing, pay\-as\-you\-go pricing, consumption\-based pricing  | Upfront payments, prepaid contracts, upfront commitments  | 
| How do customers use your application? | Customers subscribe to the product, get provisioned in seller’s environment, and are charged based on usage\. Customers can cancel their subscription at any time\. | Customers choose a contract that matches their predictable usage and commit to upfront payment\. Customers subscribe to the product and are entitled to use the application within the limits of their contract terms and duration\. Customers are charged for additional services used above their contracted amounts\. | 
| How long can customers use your application? | Subscriptions are ongoing\. Customers can use your application as long as they do not cancel their subscription\. | You can offer contracts of the following durations: 1, 12, 24, or 36 months\. Customers can choose to set up auto\-renew so that they are automatically billed for a new contract term when their current one ends\. | 
| How do sellers integrate with AWS for billing? | Sellers send AWS hourly metering records to the AWS Marketplace Metering Service: “Customer X used Y for Z hours\.” | AWS stores the contract entitlements, including the duration, contract dimensions, and quantities of units\. Sellers can retrieve a customer’s contract entitlements from the AWS Marketplace Entitlement Service: “Customer X is allowed to use Y until Z date\.” | 
| When are customers charged? | Monthly, within the normal AWS billing cycle\. |  When the customer purchases an initial contract, they upgrade to a more expensive contract, or their contract is auto\-renewed\. Customers are also charged monthly for additional usage above their contracts based on the metering records that we receive from you\.  | 
| How are discounts traditionally realized? | Volume tiered usage plans; pay less per unit for increased usage\. | Discounts are incorporated into prices for longer\-term commitments or bundles of higher quantities\. | 

To review some example applications, see the following products on the AWS Marketplace Management Portal:

### SaaS Subscription Application Examples<a name="saas-subscription-examples"></a>
+ [SendGrid Email Delivery Service](https://aws.amazon.com/marketplace/pp/B074CQY6KB)
+ [Cisco Stealthwatch Cloud \| Public Cloud Monitoring \- Metered](https://aws.amazon.com/marketplace/pp/B075MWZVBM)

### SaaS Contract Application Examples<a name="saas-contracts-examples"></a>
+ [Informatica ETL for AWS SaaS Contract](https://aws.amazon.com/marketplace/pp/B06XXM7JJT)
+ [Cisco Stealthwatch Cloud \| Public Cloud Monitoring \- Contracts](https://aws.amazon.com/marketplace/pp/B076J22YD8)