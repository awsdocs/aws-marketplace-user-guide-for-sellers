# Testing Your SaaS Product<a name="testing-your-saas-product"></a>

 During the onboarding process, you create a second AWS account ID for testing your product\. You sign in to the test account to view your SaaS listing on AWS Marketplace and use it to verify the metering and billing process on an ongoing basis\. You can also use seller reports provided through the AWS Marketplace Management Portal to conﬁrm that metered usage corresponds with the account identiﬁer for your customers\. Any charges that this test account incurs when using your product will be voided\. 

 We whitelist the product so that it's visible only to your account and any other accounts that you own and specify\. These accounts can be used to subscribe to your product and confirm that everything is working properly\. 

**Note**  
 If you create a SaaS product for use in the AWS GovCloud \(US\) Region, that SaaS product must be tested and meet the requirements for the AWS GovCloud \(US\) Region\. 

## Test New Customer Registration<a name="test-new-customer-registration"></a>

 Verify the customer registration process works, and that the customer can acceptyour terms and then register: 

1.  Create an account in your product\. 

1.  Verify that your redirect page is functional\. 

1.  Verify that your website resolves the registration token for a customer identiﬁer\. 

1.  Verify that your website allows the creation of an account\. 

1.  Verify that the product code matches the one assigned to your product\. 

1.  Verify that the customer identiﬁer is added to your accounts database\. 

1.  Verify that you receive a subscription notiﬁcation\. 

## \(Optional\) Test Existing Customer Registration<a name="optional-test-existing-customer-registration"></a>

 You can build your landing page so that existing accounts can be changed to use AWS for billing\. Repeat the process in the previous section with an existing account that doesn't have AWS billing information attached\. 

## Verify Records Using AWS CloudTrail<a name="verify-records-using-aws-cloudtrail"></a>

`BatchMeterUsage` operation calls are captured by AWS CloudTrail\. You can use CloudTrail to verify that the SaaS metering records that you sent are accurate by searching for records with the event name `BatchMeterUsage`\. You can also use CloudTrail to audit records over time\. 

 For more information, see the [AWS Marketplace Metering Service API](http://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) and [CloudTrail Supported Services and Integrations](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-supported-services.html) in the *AWS CloudTrail User Guide*\. 

## Test Duplicate Accounts<a name="test-duplicate-accounts"></a>

 Use your test account to create an account in your system and then repeat the process\. Verify that you are unable to create an account in your SaaS product because another account with that customer identiﬁer already exists\. 

## Test Metering<a name="test-metering"></a>

 Sign in to a test account in your SaaS product and begin consuming resources for a SaaS subscriptions product\. For a SaaS contracts product, purchase a contract first and then consume resources above the contracted amount\. Verify that your system is emitting metering records\. Conﬁrm with your AWS Marketplace representative that these records have been received\. 

 To test entitlements, sign in to a test account and purchase your SaaS contracts product\. Then perform the following steps: 

1.  Verify that the entitlements you retrieve from the AWS Marketplace Entitlement Service match your purchase\. 

1.  Verify that your system provisions access to your product’s features and resources based on the entitlements you retrieve\. 

1.  Verify that your system updates customers’ entitlements after a contract upgrade\. 

## Test Unsubscribe<a name="test-unsubscribe"></a>

 Unsubscribe your test account through the **Your Software** page on the AWS Marketplace website\. Verify the following information: 
+  Your product received an `unsubscribe-pending` notiﬁcation\. 
+  Your product responds as expected in an unsubscribe scenario\. For example, your product might complete existing work, but prevent work from being created for your test account\. 
+  Your product received an `unsubscribe-success` notiﬁcation\. 
+  Your product no longer sends metering records after receiving the `unsubscribe-success` notiﬁcation\. 