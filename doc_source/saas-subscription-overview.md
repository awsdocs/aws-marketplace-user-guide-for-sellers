# SaaS subscriptions<a name="saas-subscription-overview"></a>

To list and maintain a SaaS product with the subscription pricing model on AWS Marketplace, follow the procedures in this topic\. 

Before you begin, make sure you've chosen the right pricing model for your SaaS product in AWS Marketplace\. For more information, see [Plan your SaaS product](saas-prepare.md)\. 

**Topics**
+ [List your SaaS subscription product on AWS Marketplace](#saas-subscription-listing)
+ [Conduct AWS integration testing](#saas-subscription-integration)
+ [Review your SaaS AWS Marketplace product page before going live](#saas-subscription-final-review)

## List your SaaS subscription product on AWS Marketplace<a name="saas-subscription-listing"></a>

The following process outlines the steps you must take to list your SaaS subscription product on AWS Marketplace\.

### Gather your product information<a name="gather-saas-information"></a>

Before you create your product on AWS Marketplace, gather the following information:
+ A SaaS application that you can list as a product with a subscription billing model on AWS Marketplace\.
+ Product logo URL\. A publicly accessible URL that contains a clear image of the logo for the product you're providing\.
+ Your product's End User License Agreement \(EULA\) URL\. Your product must have an EULA and you must provide a link to it for customers to read and review on your product's AWS Marketplace page\.
+ Your product's registration URL\. This is where customers will be sent after they subscribe to your product on AWS Marketplace\.
+ Metadata about your product, as defined in the product creation wizard of the AWS Marketplace Management Portal\.
+ Support information for your product\. This includes email addresses and URLs for your product's support channels\.

### Create a SaaS product<a name="create-saas-product"></a>

Take your SaaS application information and create a new SaaS product in the AWS Marketplace Management Portal\.

1. Sign in to the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. For **Products**, choose **SaaS**\.

1. For **Create SaaS product**, choose **SaaS Subscriptions**, and then choose **Start**\.

1. Read through and fill out the product creation wizard using the information you gathered\. For assistance with creating your SaaS subscription product, [contact us](https://aws.amazon.com/marketplace/management/contact-us/)\.

1. The AWS Marketplace Operations team publishes your product as a limited product stage that is visible to you and any AWS accounts you have allowed to view the product\. 
**Note**  
Prices can be temporarily reduced to enable you to test the purchase flow without incurring high charges\. For more information, [contact us](https://aws.amazon.com/marketplace/management/contact-us/)\.

1. The AWS Marketplace Operations team sends an email to the address associated with your AWS account to enable testing of product codes, Amazon SNS topics, and product page URLs\. This is the first of several tests for your product that are required before the product can go live\.

## Conduct AWS integration testing<a name="saas-subscription-integration"></a>

After you've created the product, you must conduct in\-depth AWS integration testing\.

1. Use an allowed account to test the customer experience by subscribing to your product\. 

1. After you've subscribed with the allowed account, ensure that the account is redirected to the registration URL, and that the redirect is a POST request that includes a temporary token\. Then, your SaaS application must do the following:
   + Exchange the token for a `customerID` by calling the `ResolveCustomer` action in the AWS Marketplace Metering Service\.
   + Persist the `customerID` in your application for future calls\.

1. After verifying the test account in the previous step, onboard the account into your application\. For example, you can have the test customer fill out a form to create a new user account\. Or, provide them with other next steps to get access to your SaaS application\. 

1. After they're onboarded, send metering records to AWS for billing purposes using the `BatchMeterUsage` action in the AWS Marketplace Metering Service\. We recommend using AWS CloudTrail to monitor activity to ensure that billing information is being sent to AWS\. Keep the following in mind when sending metering records:
   + Metering requests are de\-duplicated on the hour\.
   + Records sent every hour are cumulative\.
   + Even if there where no records in the last hour, we strongly recommend as a best practice that you send metering send records every hour\.

1. Test for subscription changes by setting up an Amazon SQS queue and subscribing to your product's Amazon SNS topic\. The Amazon SNS topic provides notifications about changes to customer subscriptions\. This enables you to know when to provide and revoke access for specific customers\. Possible scenarios include unsubscribes, successful subscriptions, and failed subscriptions\.

1. Verify a successful subscription\. After you receive an Amazon SNS notification for your test account with a successful subscription message, metering can begin\. Records that are sent to the AWS Marketplace Metering Service before you receive the Amazon SNS notification aren't metered\. 
**Note**  
To prevent billing issues, we strongly recommend programmatically waiting for this notification before launching resources on behalf of your customers\.

1. After you have completed all of the integration requirements and tested the solution, notify the AWS Marketplace Operations team\. They will run a series of final tests on the solution by verifying that you have successfully sent metered records with the `BatchMeterUsage` action\.

For additional information, see [Metering for usage](metering-for-usage.md)\.

## Review your SaaS AWS Marketplace product page before going live<a name="saas-subscription-final-review"></a>

After end\-to\-end testing is complete, you need to review the product page with the original prices\. After you approve the page, the AWS Marketplace Operations team will make the product page live on AWS Marketplace\. At this point, customers can start discovering and subscribing to your product\.