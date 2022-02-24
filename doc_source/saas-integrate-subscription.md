# Integrate your SaaS subscription product<a name="saas-integrate-subscription"></a>

Integrating your product with AWS Marketplace is one step in [Creating a SaaS product](saas-create-product.md)\. To integrate your software as a service \(SaaS\) subscription product with AWS Marketplace, you must write code and demonstrate that it can respond successfully to several customer scenarios\. The following sections describe these scenarios, how to respond to them, and provide an overview of testing your integration\.

**Note**  
Before you begin, make sure you've chosen the right pricing model for your software as a service \(SaaS\) product in AWS Marketplace\. For more information, see [Plan your SaaS product](saas-prepare.md)\. 

**Topics**
+ [Scenario: Your service validates new customers](#saas-subscription-validate-customer)
+ [Scenario: Meter usage](#saas-subscription-meter-usage)
+ [Scenario: Monitor changes to user subscriptions](#saas-subscription-monitor-changes)
+ [Scenario: Verify customer subscription](#saas-subscription-verify-subscriptions)
+ [Testing your SaaS subscription product integration](#saas-subscription-integration-testing)

## Scenario: Your service validates new customers<a name="saas-subscription-validate-customer"></a>

When a customer subscribes to your product, they are redirected to your registration URL which is an HTTP POST request with a temporary `x-amzn-marketplace-token` token\. Respond to this request in the following ways:

1. Exchange the token for a `CustomerIdentifier`, `CustomerAWSAccountId`, and `ProductCode` by calling the `[ ResolveCustomer](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_ResolveCustomer.html)` API operation in the AWS Marketplace Metering Service\.

1. Persist the `CustomerIdentifier`, `CustomerAWSAccountID`, and `ProductCode` in your system for future calls\. You must store whether the customer has a valid subscription, along with whatever information you need about the customer\.

1. As a response to the request, you must show your user's first use experience \(as applicable for your service\)\.

## Scenario: Meter usage<a name="saas-subscription-meter-usage"></a>

When the customer starts to use your service, you must send metering records hourly\. For details on how to meter, see [Metering for usage](metering-for-usage.md)\.

We recommend that you use AWS CloudTrail to monitor activity to ensure that billing information is being sent to AWS\. Keep the following in mind when sending metering records:
+ Metering requests are de\-duplicated on the hour\.
+ Records sent every hour are cumulative\.
+ We strongly recommend as a best practice that, even if there were no records in the last hour, you send metering records every hour, with usage of 0\.

## Scenario: Monitor changes to user subscriptions<a name="saas-subscription-monitor-changes"></a>

Set up an Amazon Simple Queue Service \(Amazon SQS\) queue, and subscribe to your product's Amazon SNS topic\. Your SNS topic information was included in the email message that you received from the AWS Marketplace Operations team when you created your product\. For more information, see [Creating a SaaS product](saas-create-product.md)\. By subscribing to your SNS topic, you receive notifications about changes to customer subscriptions, including providing or revoking access for specific customers\.

**Note**  
An Amazon SNS topic Amazon Resource Name \(ARN\) looks like `arn:aws:sns:us-east-1:<account id>:aws-mp-subscription-notification-<product code>`\.

The notifications that you must respond to are:
+ `subscribe-success` – The customer is subscribed, and you can successfully meter against their customer ID\.
+ `unsubscribe-pending` – The customer is in the process of unsubscribing\. You should send any last metering records\.
+ `unsubscribe-success` – The customer has unsubscribed\. Metering records for the customer will no longer be accepted\. Follow your practices for shutting down customer resources, adhering to your retention policies\.
+ `subscribe-fail` – The customer subscription failed\. You should not meter against their customer ID or create resources on behalf of the customer\.

## Scenario: Verify customer subscription<a name="saas-subscription-verify-subscriptions"></a>

Before creating resources on the customer's behalf, verify that the customer should have access to your product\. Store the latest status of the customer from the notifications you receive via Amazon SQS to know if the customer has access\.

## Testing your SaaS subscription product integration<a name="saas-subscription-integration-testing"></a>

After you've integrated your SaaS subscription product with AWS Marketplace, you must conduct in\-depth testing to ensure that the integration is successful\. The following procedure outlines the steps to verify your product integration\.

**Note**  
Use your own accounts to subscribe to your product and test that the integration is successful\. Prices can be temporarily reduced so that you can test the purchase flow without incurring high charges in those accounts\. For more information about temporarily reducing the prices or allowing additional test accounts to access your product, [contact us](https://aws.amazon.com/marketplace/management/contact-us/)\.  
After your product is launched, the service must continue to respond to these scenarios for new customers\.

1. Use an allowed account to test the customer experience by subscribing to your product\. 

1. After you've subscribed with the allowed account, ensure that the account is redirected to the registration URL, and that the redirect is a POST request that includes a temporary token\. Make sure that your application persists the customer ID for future calls\. This tests part of [Scenario: Your service validates new customers](#saas-subscription-validate-customer)\.

1. After verifying the test account in the previous step, onboard the account into your application\. For example, you can have the test customer fill out a form to create a new user account\. Or, provide them with other next steps to get access to your SaaS application\. This tests part of [Scenario: Your service validates new customers](#saas-subscription-validate-customer)\.

1. After the test customer is onboarded, make requests that will send metering records to AWS for billing purposes by using the `BatchMeterUsage` API operation in the AWS Marketplace Metering Service\. This tests [Scenario: Meter usage](#saas-subscription-meter-usage)\.

1. Test for subscription changes\. Possible scenarios include unsubscribes, successful subscriptions, and failed subscriptions\. This tests [Scenario: Monitor changes to user subscriptions](#saas-subscription-monitor-changes)\.

1. Verify a successful subscription\. After you receive an Amazon SNS notification for your test account with a successful subscription message, metering can begin\. Records that are sent to the AWS Marketplace Metering Service before you receive the Amazon SNS notification aren't metered\. This tests [Scenario: Verify customer subscription](#saas-subscription-verify-subscriptions)\.
**Note**  
To prevent billing issues, we strongly recommend programmatically waiting for this notification before launching resources on behalf of your customers\.

1. After you have completed all of the integration requirements and tested the solution, notify the AWS Marketplace Operations team\. They will run a series of final tests on the solution by verifying that you have successfully sent metered records with the `BatchMeterUsage` API operation\.

After your integration and testing is complete, you can perform a final review and list your product on the public AWS Marketplace\. For more information, see [Creating a SaaS product](saas-create-product.md)\.