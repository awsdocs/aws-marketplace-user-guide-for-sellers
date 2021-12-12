# Accessing the AWS Marketplace Metering and Entitlement Service APIs<a name="saas-integration-metering-and-entitlement-apis"></a>

This section outlines the process of integrating with the AWS Marketplace Metering Service or AWS Marketplace Entitlement Service, used to ensure your billing and reporting of customer usage of your software as a service \(SaaS\) products is accurate\. It's assumed that you've submitted a SaaS subscriptions product or a SaaS contracts product that has been published to a limited state\. In a limited state, you can use your test accounts to verify proper configuration and function but your product is not available publicly\. 

**Note**  
If your SaaS product is integrated with another AWS managed service that handles metering in a different way \(such as Amazon SageMaker Ground Truth, or AWS WAF\), then you do not need to integrate with AWS Marketplace metering service\. Metering for your product should only happen in one system to avoid double billing your customer\.

**Topics**
+ [Metering for usage](metering-for-usage.md)
+ [Checking entitlements](checking-entitlements.md)
+ [SaaS product integration checklist](aws-marketplace-integration-checklist.md)

 For information about setting up the AWS CLI, along with credentials, see [Configuring the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html) in the *AWS Command Line Interface User Guide*\. If you're new to the AWS Python SDK, see the Boto 3 [Quickstart](https://boto3.readthedocs.io/en/latest/guide/quickstart.html)\. 