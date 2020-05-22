# SaaS contracts with consumption<a name="saas-contract-consumption-overview"></a>

To list and maintain a SaaS product with the contract with consumption pricing model on AWS Marketplace follow the procedures in this topic\. 

Before you begin, make sure you've chosen the right pricing model for your SaaS product in AWS Marketplace\. For more information, see [Plan your SaaS product](saas-prepare.md)\. 

**Topics**
+ [List your SaaS contract product on AWS Marketplace](#saas-contract-consumption-listing)
+ [Conduct AWS integration testing](#saas-contract-integration-consumption)
+ [Review your SaaS AWS Marketplace product page before going live](#saas-contract-consumption-final-review)

## List your SaaS contract product on AWS Marketplace<a name="saas-contract-consumption-listing"></a>

The following process outlines the steps you must take to list your SaaS contract with consumption product on AWS Marketplace:

### Gather your product information<a name="gather-saas--contract-consumption-information"></a>

Before you create your product on AWS Marketplace, gather the following information:
+ A SaaS application that you can list as a product with a contract with consumption billing model on AWS Marketplace\.
+ Product logo URL\. A publicly accessible URL that contains a clear image of the logo for the product you're providing\.
+ Your product's End User License Agreement \(EULA\) URL\. Your product must have an EULA and you must provide a link to it for customers to read and review on your product's AWS Marketplace page\.
+ Your product's registration URL\. This is where customers will be sent after they subscribe to your product on AWS Marketplace\.
+ Metadata about your product, as defined in the product creation wizard of the AWS Marketplace Management Portal\.
+ Support information for your product\. This includes email addresses and URLs for your product's support channels\.

### Create a SaaS product<a name="create-saas-product-contract-consumption"></a>

Take your SaaS application information and create a new SaaS product in the AWS Marketplace Management Portal\.

1. Sign in to the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the **Products** dropdown menu, choose **SaaS**\.

1. From **Create SaaS product**, choose **SaaS Contracts**, and then choose **Start**\.

1. Read through and fill out the product creation wizard using the information you gathered previously\. For assistance with creating your SaaS contract product, [contact us](https://aws.amazon.com/marketplace/management/contact-us/)\.

1. The AWS MP Ops team will publish your product as a limited product stage visible to you and any AWS accounts you have allowed to view the product\. 
**Note**  
Prices can be temporarily reduced to enable you to test the purchase flow without incurring high charges, contact us for more information\.

1. The AWS MP Ops team will send an email to the address associated with your AWS account to enable testing of product codes, Amazon SNS topics, and product page URLs\. This is the first of several tests for your product that are required before the product can go live\.

## Conduct AWS integration testing<a name="saas-contract-integration-consumption"></a>

Once the product has been created, more in\-depth testing can begin\. The following test must be completed:

1. Use an allowed account to test the customer experience by getting a contract for your product\. 

1. Once the account has the contract, ensure that the account is redirected to the registration URL, and that the redirect is a POST request that includes a temporary token\. Then your SaaS application must:
   + Exchange the token for a `customerID` by calling the `ResolveCustomer` action in the AWS Marketplace Metering Service\.
   + Persist the `customerID` in your application for future calls\.
   + With the `customerID`, call `GetEntitlement` in the AWS Marketplace Entitlement Service to verify which dimension the customer is subscribed to and the quantity, if applicable\.

1. After verifying the test account in the previous step, onboard the account into your application\. For example, you can have the test customer fill out a form to create a new user account\. Or provide them with other next steps to get access to your SaaS application\. 

1. If no entitlement is returned from `GetEntitlement`, either during onboarding or in your ongoing verification passes, determine how to manage access and the experience for unentitled users\.

1. Once onboarded, send metering records to AWS for billing purposes using the `BatchMeterUsage` action in the AWS Marketplace Metering Service\. We recommend using AWS CloudTrail to monitor activity to ensure that billing information is being sent to AWS\. Keep the following in mind when sending metering records:
   + Metering requests are de\-duplicated on the hour\.
   + Records sent every hour are cumulative\.
   + Even if there where no records in the last hour, we strongly recommend as a best practice that you send metering send records every hour\.

1. Setup an Amazon SQS queue and subscribe to your products Amazon SNS topics\. These topics provide notifications about changes to customers subscription and entitlement statuses\. This enables you to know when to provide and revoke access for specific customers\. Possible scenarios include: unsubscribes, upgrades, renewals, and failed subscription\.

1. After you have completed all the integration requirements and tested the solution, notify the AWS Marketplace Ops team\. They will then test the solution by verifying you have successfully called `GetEntitlement` and sufficiently onboard new customers\. They will also verify you have successfully sent metered records via `BatchMeterUsage`\.

For additional information, see [Checking entitlements](checking-entitlements.md)\.

## Review your SaaS AWS Marketplace product page before going live<a name="saas-contract-consumption-final-review"></a>

After end\-to\-end testing is complete, you will have the chance to review the product page with the original prices\. After giving approval, the AWS Marketplace Ops team will make the product page live on AWS Marketplace\. At this point, customers can start discovering and subscribing to your product\.