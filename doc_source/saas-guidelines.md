# SaaS Product Recommendations and Requirements<a name="saas-guidelines"></a>

AWS Marketplace maintains these guidelines for all SaaS products and offerings on AWS Marketplace to promote a safe, secure, and trustworthy platform for our customers\. 

The AWS Marketplace seller operations team reviews all products and their related metadata when submitted to ensure that they meet or exceed current AWS Marketplace guidelines\. We review and adjust these guidelines to meet our evolving security requirements\. In addition, AWS Marketplace continuously reviews products to verify that they meet any changes to these guidelines\. If products fall out of compliance, we might require that you update your product\. In some cases, your product might temporarily be unavailable to new subscribers until issues are resolved\.

## Product Setup Requirements<a name="saas-guidelines-setup"></a>

All SaaS products must adhere to the following product setup guidelines:
+ At least one pricing dimension must have a price greater than $0\.00\.
+ All pricing dimensions must relate to actual software and cannot include any other products or services unrelated to the software\.
+ SaaS products offered exclusively in the AWS GovCloud \(US\) Region must include `GovCloud` somewhere in the product title\.

## Customer Information Requirements<a name="saas-customer-information"></a>

All SaaS products must adhere to the following customer information requirements:
+ SaaS products must be billed entirely through the listed dimensions on AWS Marketplace\.
+ You cannot collect customer payment information for your SaaS product at any time, including credit card and bank account information\.

## Product Usage Requirements<a name="saas-product-usage"></a>

All SaaS products must adhere to the following product usage requirements:
+ If a customer cannot gain access to your application immediately, you must provide a message with specific instructions on when they will gain access\. 
+ After an account has been created, you must send the customer a notification confirming that one has been created along with clear next steps\.
+ If a customer already has an account in the SaaS application, they must have the ability to log in from the fulfillment landing page\.
+ Customers must be able to see the status of their subscription within the SaaS application, including any relevant contract or subscription usage information\.
+ Customers must be able to easily get help with issues such as using the application, troubleshooting, and requesting refunds \(if applicable\)\. Support contact options must be specified on the fulfillment landing page\.

### Product Usage Recommendation<a name="saas-product-usage-recommendation"></a>

After subscribing to the product in AWS Marketplace, customers should be able to create an account within your SaaS application and gain access to a web console within two business days\. 

## Architecture Requirements<a name="saas-architecture"></a>

All SaaS products must adhere to the following architecture requirements:
+ A portion of your application must be hosted in an AWS account you own\.
+ All application components should be hosted in infrastructure you manage\. Applications that require additional resources in the customer’s infrastructure must follow these guidelines:
  + Provision resources in a secure way, such as using the AWS Security Token Service \(AWS STS\) or AWS Identity and Access Management \(IAM\)\. 
  + Provide additional documentation including a description of all provisioned AWS services, IAM policy statements, and how an IAM role or user is getting deployed and used in the customer’s account\. 
  + Include a notification in the product description describing that, if the customer incurs additional AWS infrastructure charges separate from their AWS Marketplace transaction, they're responsible for paying the charges\.
  + If your product deploys an agent, you must provide instructions to the customer on how to deploy it in their AWS account\.
+ You must call the AWS Marketplace APIs from the AWS account that registered as a provider and submitted the SaaS publishing request\. The SaaS pricing model determines which APIs should be called:
  + SaaS contracts: [GetEntitlements](https://docs.aws.amazon.com/marketplaceentitlement/latest/APIReference/API_GetEntitlements.html) in the AWS Marketplace Entitlement Service\.
  + SaaS contracts with consumption: [GetEntitlements](https://docs.aws.amazon.com/marketplaceentitlement/latest/APIReference/API_GetEntitlements.html) in the AWS Marketplace Entitlement Service and [BatchMeterUsage](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_BatchMeterUsage.html) in the AWS Marketplace Metering Service\.
  + SaaS subscriptions: [BatchMeterUsage](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_BatchMeterUsage.html) in the AWS Marketplace Metering Service\.
+ SaaS products offered exclusively in AWS GovCloud \(US\) Regions must outline the architectural boundaries between commercial and AWS GovCloud \(US\) Regions, use cases for the product, and the workloads not recommended for the product\.