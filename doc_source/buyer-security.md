# Security on AWS Marketplace<a name="buyer-security"></a>

 We list software from high\-quality sellers, and actively work to maintain the quality of our selection\. Because every customer is different, our goal is to provide enough information about the products listed on AWS Marketplace so that customers can make good purchasing decisions\. For information about security for data products from AWS Data Exchange, see [Security](https://docs.aws.amazon.com/data-exchange/latest/userguide/security.html) in the *AWS Data Exchange User Guide*\.

## Subscriber information shared with sellers<a name="subscriber-information-shared-with-providers"></a>

We may share your contact information with our sellers for the following reasons:
+ If it is necessary for them to provide customer training and technical support\.
+ For software activation, configuration, and customization of content\.
+ Compensate their sales teams internally\.

In addition, we may share information such as company name, full address and usage fees with sellers in order for sellers to compensate their sales teams\. We may also share certain information with sellers to help them evaluate the effectiveness of their marketing campaigns\. Sellers may use this information along with information that they already possess to determine rewards for their sales teams or usage for a particular buyer\.

Otherwise, we generally do not share customer information with sellers, and any information shared is not personally identifiable, unless you have given us permission to share such information, or we believe that providing the information to sellers is necessary to comply with laws or regulations\.

## Control access to subscriptions<a name="control-access-to-subscriptions"></a>

Use AWS Identity and Access Management \(IAM\) to create IAM users and assign them permissions to work with your subscriptions\. This can include listing subscriptions, subscribing to product, and launching instances of subscribed software\. Others can then log in to AWS Marketplace using the user name and password that you give them, and they have only the permissions that you assigned\.

## Working with subscriptions<a name="work-with-subscriptions"></a>

 If your organization is using IAM, your account owner probably set you up with user information that includes account credentials and a URL for logging in\. The URL looks like `https://123456789012.signin.aws.amazon.com/console` but with a different number\. After you have the URL and credentials, navigate to the login URL, log in using your credentials, and navigate to [AWS Marketplace](https://aws.amazon.com/marketplace)\. The owner might have restricted the tasks that you can perform\.