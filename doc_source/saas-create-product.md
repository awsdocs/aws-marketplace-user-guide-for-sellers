# Creating a SaaS product<a name="saas-create-product"></a>

To sell software as a service \(SaaS\) products, you create the SaaS product in AWS Marketplace, integrate it with AWS Marketplace, test the integration, and release the product to customers\. The following steps explain the process in more detail\.

**To create a SaaS product in AWS Marketplace**

1. **Decide to list a SaaS product**

   Have a SaaS product that you would like to sell in AWS Marketplace\. Review and understand how to [Plan your SaaS product](saas-prepare.md)\.

1. **Determine pricing and offer type**

   There are three offer types for SaaS products: subscriptions, contracts, and contracts with pay\-as\-you\-go \. Your choice of offer type affects how you integrate your SaaS product with AWS Marketplace\. For more information, see [Plan your pricing](saas-prepare.md#plan-pricing)\.

1. **Collect assets**

   Collect the assets that you will need to use to submit your product\. Assets for your product include:
   + Product logo URL – A publicly accessible URL that contains a clear image of the logo for the product you are providing\.
   + End User License Agreement \(EULA\) URL – Your product must have a EULA, and you must provide a link to it for customers to read and review on your product's AWS Marketplace page\.
   + Product registration URL – This URL is where customers are sent after subscribing to your product in AWS Marketplace\.
   + Metadata about your product – You provide the metadata in the product creation wizard of the AWS Marketplace Management Portal\.
   + Support information for your product – This includes email addresses and URLs for your product's support channels\.

1. **Submit your product for integration**

   [Create an initial SaaS product page](saas-create-product-page.md) from your seller account using AWS Marketplace Management Portal\. AWS Marketplace will publish your product as a limited product, which means that it's only available to your accounts to use for integration and testing\. The AWS Marketplace Operations Team will send you an email message with your product code, Amazon Simple Notification Service \(Amazon SNS\) topics, and product page URL\. With that information, you will have an environment to use for creating and testing your integration with AWS Marketplace in your product\. Use the email you received from the AWS Marketplace Operations team for correspondence regarding the product\.

1. **Integrate with AWS Marketplace**

   Your product must support customers onboarding and using your product, including validating their subscription before giving them access, and, in some cases, metering for their usage\. How you integrate with AWS Marketplace depends on the offer type you're using for your product\. For more information about integration, based on offer type, see the following topics\.
   + [ Subscription integration](https://docs.aws.amazon.com/marketplace/latest/userguide/saas-integrate-subscription.html)
   + [ Contract integration](https://docs.aws.amazon.com/marketplace/latest/userguide/saas-integrate-contract.html)
   + [ Contract with pay\-as\-you\-go integration](https://docs.aws.amazon.com/marketplace/latest/userguide/saas-integrate-contract-consumption.html)

   The final step of integrating your product with AWS Marketplace is to test it to ensure that the integration works properly\.

1. **Submit your product for launch**

   After you have verified your integration, and you're ready for the product to be live, submit it to the AWS Marketplace Operations team \(using the email case created earlier\) for end\-to\-end testing and launch\.

1. **Launch**

   After end\-to\-end testing is complete, you need to review the product page with the original prices\. Approve the page by responding to the email case you received when you created your product \(see [Creating a SaaS product](#saas-create-product)\)\. After your approval, the AWS Marketplace Operations team will make the product page live on AWS Marketplace\. At this point, customers can start discovering and subscribing to your product\.