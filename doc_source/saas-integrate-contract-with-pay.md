# Integrate your SaaS contract with pay\-as\-you\-go product<a name="saas-integrate-contract-with-pay"></a>

Integrating your product with AWS Marketplace is one step in [Creating a SaaS product](saas-create-product.md)\. To integrate your software as a service \(SaaS\) contract product with AWS Marketplace, you must write code and demonstrate that it can respond successfully to several customer scenarios\. The following sections describe these scenarios, how to respond to them, and provide an overview of testing your integration\.

**Note**  
Before you begin, make sure you've chosen the right pricing model for your software as a service \(SaaS\) product in AWS Marketplace\. For more information, see [Plan your SaaS product](saas-prepare.md)\. 

**Topics**
+ [Scenario: Your service validates new customers](#saas-contract-with-pay-validate-customer)
+ [Scenario: Your service handles customer requests](#saas-contract-with-pay-customer-requests)
+ [Scenario: Meter usage](#saas-contract-with-pay-meter-usage)
+ [Scenario: Monitor changes to user entitlements](#saas-contract-with-pay-monitor-changes)
+ [Testing your SaaS contract product integration](#saas-contract-consumption-integration-testing)

## Scenario: Your service validates new customers<a name="saas-contract-with-pay-validate-customer"></a>

When a customer subscribes to your product, they are redirected to your registration URL, which is an HTTP POST request with a temporary `x-amzn-marketplace-token` token\. Respond to this request in the following ways:

1. Exchange the token for a `CustomerIdentifier`, `CustomerAWSAccountId`, and `ProductCode` by calling the `[ ResolveCustomer](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_ResolveCustomer.html)` API operation in the AWS Marketplace Metering Service\.

1. Verify the subscription and quantity \(if applicable\) the customer has access to by calling the `[ GetEntitlements](https://docs.aws.amazon.com/marketplaceentitlement/latest/APIReference/API_GetEntitlements.html)` action in the AWS Marketplace Entitlement Service\.

1. Persist the `CustomerIdentifier`, `CustomerAWSAccountId`, and `ProductCode` in your system for future calls\. Store whether the customer has a valid subscription, along with whatever information you need about the customer\.

1. As a response to the request, you must show your user's first use experience \(as applicable for your service\)\.

## Scenario: Your service handles customer requests<a name="saas-contract-with-pay-customer-requests"></a>

When a customer makes a request to your service, you must respond to the following scenarios with appropriate actions or messaging:
+ They don't have a customer ID in your system\. This means that they have not yet subscribed\. You should give them messaging describing how to subscribe\.
+ They have a customer ID, and the `GetEntitlements` API operation returns an appropriate entitlement\. In this scenario, you should fulfill the request\.
+ They do have a customer ID, but the `GetEntitlements` API operation returns no entitlement, or not enough quantity to fulfill the request\. In this scenario, you must determine how to handle access and manage their experience\.

## Scenario: Meter usage<a name="saas-contract-with-pay-meter-usage"></a>

When the customer starts to use your service, you must send metering records hourly\. For details on how to meter, see [Metering for usage](metering-for-usage.md)\.

We recommend that you use AWS CloudTrail to monitor activity to ensure that billing information is being sent to AWS\. Keep the following in mind when sending metering records:
+ Metering requests are de\-duplicated on the hour\.
+ Records sent every hour are cumulative\.
+ We strongly recommend as a best practice that, even if there were no records in the last hour, you send metering records every hour, with usage of 0\.

## Scenario: Monitor changes to user entitlements<a name="saas-contract-with-pay-monitor-changes"></a>

Set up an Amazon Simple Queue Service \(Amazon SQS\) queue, and subscribe to your product's Amazon SNS topics—there are two SNS topics, one for entitlement changes and one for subscription changes\. Your topic information was included in the email message that you received from the AWS Marketplace Operations Team when you created your product\. For more information, see [Creating a SaaS product](saas-create-product.md)\. By subscribing to your SNS topics, you receive notifications about changes to customer subscriptions, including providing or revoking access for specific customers\.

**Note**  
An SNS topic Amazon Resource Name \(ARN\) for a subscription change looks like `arn:aws:sns:us-east-1:<account id>:aws-mp-subscription-notification-<product code>`\. An SNS topic ARN for entitlement changes looks like `arn:aws:sns:us-east-1:<account id>:aws-mp-entitlement-notification-<product code>`\.

The notifications that you must respond to are as follows:
+ `entitlement-updated` \(in the entitlement SNS topic\)– The customer entitlement has changed, and you must call the `GetEntitlements` API operation to see the new status\. Update your customer store, and, if applicable \(for example, the customer's contract has lapsed\), follow your practices for shutting down customer resources, adhering to your retention policies\.
+ `subscribe-success` \(in the subscription SNS topic\) – The customer is subscribed, and you can successfully meter against their customer ID\.
+ `unsubscribe-pending` \(in the subscription SNS topic\) – The customer is in the process of unsubscribing\. You should send any last metering records\.
+ `unsubscribe-success` \(in the subscription SNS topic\) – The customer has unsubscribed\. Metering records for the customer will no longer be accepted\. Follow your practices for shutting down customer resources, adhering to your retention policies\.
+ `subscribe-fail` \(in the subscription SNS topic\) – The customer subscription failed\. You should not meter against their customer ID or enable resources on behalf of the customer\.

**Note**  
For additional information, see [Checking entitlements](checking-entitlements.md)\.

## Testing your SaaS contract product integration<a name="saas-contract-consumption-integration-testing"></a>

After you've integrated your contract with pay\-as\-you\-go product with AWS Marketplace, you must conduct in\-depth testing to ensure that the integration is successful\. The following procedure outlines the steps to verify your product integration\.

**Note**  
Use your own accounts to subscribe to your product and test that the integration is successful\. Prices can be temporarily reduced so that you can test the purchase flow without incurring high charges in those accounts\. For more information about temporarily reducing the prices or allowing additional test accounts to access your product, [contact us](https://aws.amazon.com/marketplace/management/contact-us/)\.  
After your product is launched, the service must continue to respond to these scenarios for new customers\.

1. Use an allowed account to test the customer experience by getting a contract for your product\. 

1. After the account has the contract, ensure that the account is redirected to the registration URL, and that the redirect is a POST request that includes a temporary token\. Make sure that your application persists the customer ID for future calls and correctly handles the entitlement the customer has\. This tests part of [Scenario: Your service validates new customers](#saas-contract-with-pay-validate-customer)\.

1. After verifying the test account in the previous step, onboard the account into your application\. For example, you can have the test customer fill out a form to create a new user account\. Or, provide them with other next steps to get access to your SaaS application\. This tests part of [Scenario: Your service validates new customers](#saas-contract-with-pay-validate-customer)\.

1. If no entitlement is returned from the `GetEntitlements` API operation, either during onboarding or in your ongoing verification passes, your application must correctly manage access and the experience for users who are not entitled\. This tests [Scenario: Your service handles customer requests](#saas-contract-with-pay-customer-requests)\.

1. After the test customer is onboarded, make requests that will send metering records to AWS for billing purposes by using the `BatchMeterUsage` API operation in the AWS Marketplace Metering Service\. This tests [Scenario: Meter usage](#saas-contract-with-pay-meter-usage)\.

1. Test for subscription changes\. Verify that your application correctly handles unsubscribes, successful subscription, and failed subscription scenarios\. This tests [Scenario: Monitor changes to user entitlements](#saas-contract-with-pay-monitor-changes)\.

1. After you have completed all the integration requirements and tested the solution, notify the AWS Marketplace Operations team\. They will then test the solution by verifying that you have successfully called the `GetEntitlements` API operation and sufficiently onboarded new customers\. They will also verify that you have successfully sent metered records with the `BatchMeterUsage` API operation\.

After your integration and testing is complete, you can perform a final review and list your product on the public AWS Marketplace\. For more information, see [Creating a SaaS product](saas-create-product.md)\.