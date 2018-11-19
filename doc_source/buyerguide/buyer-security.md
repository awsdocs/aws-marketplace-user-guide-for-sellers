# Security on AWS Marketplace<a name="buyer-security"></a>

 We list software from high\-quality vendors, and actively work to maintain the quality of our selection\.  Since every customer is different, our goal is for there to be enough information about the products listed on AWS Marketplace to enable customers to make good purchasing decisions\. 

## What information do you share with the software seller about the customers of a product?<a name="what-information-do-you-share-with-the-software-seller-about-the-customers-of-a-product"></a>

 We generally do not share customer information with vendors and any information shared is not personally identifiable, unless \(i\) you have given us permission to share such information, or \(ii\) we believe that providing the information to the vendor is necessary to comply with laws or regulations\. We may share information such as company name and usage fees with vendors in order for those vendors to compensate their sales teams\. We may also share certain information with vendors to help them evaluate the effectiveness of their marketing campaigns\. Vendors may use this information along with information that they already possess to determine usage on a customer\-by\-customer basis\. 

## How do I control access to my AWS Marketplace subscriptions?<a name="how-do-i-control-access-to-my-aws-marketplace-subscriptions"></a>

 Use AWS Identity and Access Management \(IAM\) to create IAM users and assign them permissions to work with your subscriptions\. This can include listing subscriptions, subscribing to software, and launching instances of subscribed software\. Others can then log in to AWS Marketplace using the user name and password that you give them, and they have only the permissions that you’ve assigned\. For details, see [Controlling Access to AWS Marketplace Subscriptions](ControllingAccessToAWSMarketplaceSubscriptions.md)\. 

## As an IAM user, how do I log in and work with subscriptions?<a name="as-an-iam-user-how-do-i-log-in-and-work-with-subscriptions"></a>

 If your organization is using IAM, your account owner probably set you up with user information that includes account credentials and a URL for logging in\. The URL looks something like *https://123456789012\.signin\.aws\.amazon\.com/console*, but with a different number\. Once you have these, go to the login URL, log in using your credentials, and then open [AWS Marketplace](https://aws.amazon.com/marketplace)\. The owner might have restricted the tasks that you can perform\.

## Why do I get a **permission denied** error when I try to subscribe to software or start an instance?<a name="why-do-i-get-a-permission-denied-error-when-i-try-to-subscribe-to-software-or-start-an-instance"></a>

 When the IAM account administrator set up your user information, they granted you certain permissions\. If you try to perform a task in AWS Marketplace that the owner has not allowed, you get this error\. Contact your account administrator for more information\. 