# What is AWS Marketplace?<a name="what-is-marketplace"></a>

AWS Marketplace is an online store where you can sell or buy software that runs on Amazon Web Services \(AWS\)\. AWS Marketplace complements programs like Amazon DevPay and the Amazon Partner Network\. For information about how AWS Marketplace differs from Amazon DevPay, see the [AWS Marketplace Help and FAQ](https://aws.amazon.com/marketplace/help/)\. For more information about the Amazon Partner Network, see the [AWS Partner Network home page](https://aws.amazon.com/partners/)\.


+ [How Can I Use AWS Marketplace?](#how-to-use-marketplace)
+ [Controlling Access to AWS Marketplace](#controlling-access-to-marketplace)
+ [Additional Resources](#marketplace-additional-resources)
+ [Controlling Access to AWS Marketplace Subscriptions](ControllingAccessToAWSMarketplaceSubscriptions.md)
+ [Controlling User Access to AWS Marketplace Management Portal](marketplace-management-portal-user-access.md)

## How Can I Use AWS Marketplace?<a name="how-to-use-marketplace"></a>

You use AWS Marketplace primarily as a subscriber \(buyer\), or as a seller\.

### Using AWS Marketplace as a Subscriber<a name="using-marketplace-subscriber"></a>

AWS Marketplace is an online store where, as a subscriber, you can find, buy, and quickly deploy software that runs on Amazon Web Services \(AWS\)\. This software is available in the form of Amazon Machine Images \(AMIs\)\. An Amazon Machine Image \(AMI\) contains all the information necessary to boot an Amazon EC2 instance with your software\. An EC2 instance is the virtual computing environment available from the Amazon Elastic Compute Cloud \(Amazon EC2\) web service\.

An AMI is like a template of a computer's root volume\. For example, an AMI might contain the software to act as a web server \(Linux, Apache, and your web site\) or it might contain the software to act as a Hadoop node \(Linux, Hadoop, and a custom application\)\. You can launch one or more EC2 instances from an AMI\.

To buy software through AWS Marketplace, you subscribe to the software by purchasing a paid AMI, and then launch the software as an EC2 instance\.

For more information, see the following topics in the* Amazon EC2 User Guide for Linux Instances*:

+ [Finding a Paid AMI](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/paid-amis.html#using-paid-amis-finding-paid-ami)

+ [Purchasing a Paid AMI](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/paid-amis.html#using-paid-amis-purchasing-paid-ami)

+ [Launching an AWS Marketplace Instance](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/launch-marketplace-console.html)

+ [Managing Your AWS Marketplace Subscriptions](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/paid-amis.html#marketplace-manage-subscriptions)

### Using AWS Marketplace as a Seller<a name="using-marketplace-seller"></a>

As a seller, you can build a custom AMI to sell on AWS Marketplace and manage the sales channel for products you sell\. For information about becoming a seller on AWS Marketplace, go to the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour/)\. For detailed information about selling your AMI, see [Selling Your AMI](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/paid-amis.html#selling-your-ami) in the *Amazon EC2 User Guide for Linux Instances*\.

To manage the sales channel for products you sell on AWS Marketplace, you use the [AWS Marketplace Management Portal](https://aws.amazon.com//marketplace/management/tour/), where you can access five different pages from the navigation bar links: 

+ **Marketing page**

  Use this page to view the results of your marketing efforts and to better understand the traffic, conversion, customer usage, and revenue that your marketing efforts generate\.

+ **Customer Support Eligibility page**

  Your support staff can use this page to access near\-real\-time information about a customer's subscription to your products and provide fast, personalized service\.

+ **Reports page**

  Use this page to download all your latest reports, including Weekly Ref Tag Reports and other product subscription and usage reports\.

+ **Manage Products page**

  Use this page to share your AMI with AWS Marketplace and have your AMI scanned to ensure it meets the listing requirements\. You can also view all your AMIs \(whether shared or unshared\), and download data for your existing published products\.

+ **File Upload page**

  Use this page to upload files to AWS Marketplace, including product metadata, images, and product documentation\.

## Controlling Access to AWS Marketplace<a name="controlling-access-to-marketplace"></a>

Your company might have specific people who should be allowed to use AWS Marketplace or the AWS Marketplace Management Portal on the company’s behalf\. To use AWS Marketplace, these people must be signed into AWS\. It's not a good idea to share the primary credentials of your AWS account in order to give them access, however, for these reasons:

+ Revoking shared credentials is difficult\. For example, a person might change roles and responsibilities in your company and not be allowed to manage your subscriptions or product information in the new role\.

+ Anyone who has your primary credentials also has access to everything in your account, including the billing information for your account\.

A better approach is to use AWS Identity and Access Management \(IAM\) to create users and groups:

1. Create a user for each person in your company who needs to work with product information or subscriptions\. When you create users, each user has an individual user name and password that they use to sign in to AWS services, including AWS Marketplace and the AWS Marketplace Management Portal\.

1. After you've created users, you can create groups in IAM and configure the groups to provide different levels of access to the AWS Marketplace Management Portal or to your AWS Marketplace subscriptions\. For example, one group might have permission only to view your subscriptions; another group might be able to subscribe and unsubscribe; and a third group might have complete control, which includes starting and stopping instances\.

1. Finally, after you've created the groups, you can assign each IAM user to one of the groups, based on the level of access that user should have\.

For instructions on using IAM to manage access to AWS Marketplace as a subscriber \(buyer\), see [Controlling Access to AWS Marketplace Subscriptions](ControllingAccessToAWSMarketplaceSubscriptions.md)\.

For instructions on using IAM to manage access to AWS Marketplace Management Portal as a seller, see [Controlling User Access to AWS Marketplace Management Portal](marketplace-management-portal-user-access.md)\.

## Additional Resources<a name="marketplace-additional-resources"></a>

For more information about how to work with AWS Marketplace and AWS Marketplace Management Portal, including how AWS manages billing for AWS Marketplace products, how to get support for products you purchase on AWS Marketplace, and where AWS Marketplace fits in with Amazon DevPay or the AWS Partner Network, see the [AWS Marketplace Help and FAQ](https://aws.amazon.com/marketplace/help/)\.