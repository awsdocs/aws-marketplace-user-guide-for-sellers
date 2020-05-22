# AWS Marketplace security<a name="security"></a>

Cloud security at AWS is the highest priority\. As an AWS customer, you benefit from a data center and network architecture that is built to meet the requirements of the most security\-sensitive organizations\.

Security is a shared responsibility between AWS and you\. The [shared responsibility model](https://aws.amazon.com/compliance/shared-responsibility-model/) describes this as security *of* the cloud and security *in* the cloud:
+ **Security of the cloud** – AWS is responsible for protecting the infrastructure that runs AWS services in the AWS Cloud\. AWS also provides you with services that you can use securely\. The effectiveness of our security is regularly tested and verified by third\-party auditors as part of the [AWS compliance programs](https://aws.amazon.com/compliance/programs/)\. To learn about the compliance programs that apply to AWS Marketplace, see [AWS Services in Scope by Compliance Program](https://aws.amazon.com/compliance/services-in-scope/)\.
+ **Security in the cloud** – Your responsibility is determined by the AWS service that you use\. You're also responsible for other factors including the sensitivity of your data, your organization’s requirements, and applicable laws and regulations\. 

This documentation helps you understand how to apply the shared responsibility model when using AWS Marketplace\. The following topics show you how to configure AWS Identity and Access Management to manage access to AWS Marketplace in order to meet your security and compliance objectives\. You can also learn how to use other AWS services that can help you to monitor and secure your AWS Marketplace resources\. 

**Note**  
To learn about security on AWS Data Exchange for data products, see [Security](https://docs.aws.amazon.com/data-exchange/latest/userguide/security.html) in the *AWS Data Exchange User Guide*\.

**Topics**
+ [Controlling access to AWS Marketplace Management Portal](marketplace-management-portal-user-access.md)
+ [Policies and permissions for AWS Marketplace sellers](detailed-management-portal-permissions.md)
+ [AWS Marketplace Commerce Analytics Service account permissions](set-aws-iam-cas-permissions.md)
+ [AWS Marketplace Product Support Connection account permissions](set-aws-iam-psc-permissions.md)
+ [Amazon SQS permissions](set-aws-iam-sqs-permissions.md)
+ [AWS Marketplace metering and entitlement API permissions](iam-user-policy-for-aws-marketplace-actions.md)
+ [AMI security policies](product-and-ami-policies.md)
+ [Logging AWS Marketplace API calls with AWS CloudTrail](logging-aws-marketplace-api-calls-with-aws-cloudtrail.md)