# Product and AMI Policies<a name="product-and-ami-policies"></a>

These policies exist to ensure that the products and offerings on AWS Marketplace contribute to a safe, secure, and trusted source for customers\. 

**All** products and meta data are reviewed to ensure they meet or exceed current AWS Marketplace policies\. Product policies are always being reviewed and adjusted to meet current security guidelines, and products might no longer be compliant with current policy\. With the introduction of AMI Self\-Service Scanning, use the [self\-service AMI scanning tool](https://aws.amazon.com/marketplace/management/manage-products/#/manage-amis.unshared), which helps ensure that the AMI meets AWS Marketplace policies\. 

## Security<a name="security"></a>
+ AMIs **must not** contain any known vulnerabilities, malware, or viruses\. 
+ AMIs **must not** contain default passwords, authentication keys, key pairs, security keys, or other credentials for any reason\. All instance authentication must use key pair access, not password\-based authentication, even if the password is generated, reset, or defined by the user at launch\. 
+ AMIs **must not** request or use access /secret keys from users to access AWS resources\. If your AMI application requires access to the customer account, it must be achieved through an IAM role instantiated through a [AMI\-based Delivery Using AWS CloudFormation](cloudformation.md) which creates the instance and associates the appropriate role\.
+ AWS Marketplace AMIs must not allow password authentication\. Disable password authentication via your `sshd_config` file by setting `PasswordAuthentication` to NO\. 

## Accessibility<a name="accessibility"></a>
+ Linux\-based AMIs **must** [lock/disable root login](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/building-shared-amis.html) and allow only sudo access through a user account, not root\. Sudo allows you to control which users are allowed to perform root functions and logs the activity for an audit trail\. 
+ AMIs **must** allow OS\-level administration capabilities to allow for compliance requirements, vulnerability updates, and log file access\. Linux\-based AMIs use SSH, and Windows\-based AMIs use RDP\. 
+ Linux\-based AMIs **must not** have blank or null root passwords\. 
+ AMIs **must not** contain authorized passwords or authorized keys\.
+ AMIs **must not** use default passwords for user interface access\. We recommend a randomization process such as using the `instance_id`\. 
+ Windows\-based AMIs **must** do the following:
  + Use the most recent version of [Ec2ConfigService](http://aws.amazon.com/developertools/5562082477397515)\.
  + Enable `Ec2SetPassword`, `Ec2WindowsActivate`, and `Ec2HandleUserData` 
  + Remove guest accounts or remote desktop users \(none are allowed\) 
+  The seller **must not** maintain access to the customer's running instances\. The customer has to explicitly enable any outside access, and any accessibility built into the AMI must be off by default\. 

## Customer Information<a name="customer-information"></a>

1. All non\-BYOL \(Bring Your Own License\) AMI products **must not** require customer registration with the seller or require customer information \(e\.g\., email address\) to use the product\. 

1. Software **must not** require, collect, or export customer data without the customer's knowledge and express consent\. 

1. AWS **will not** share private or personally identifying customer information \(name, email address, contact information, etc\.\) with any seller or outside party without the consent of the customer\. 

## Product Usage<a name="product-usage"></a>

1. Products **must not** restrict access to the product or product functionality by time or other restrictions\. trial, beta, and evaluation products aren't supported\.

1. All AMIs **must** meet be compatible with either the AWS 1\-Click fulfillment experience or the [Clusters and AWS Resources](https://aws.amazon.com/mp/clusters/) feature\. For 1\-Click, the AMI cannot require customer or user data at instance creation in order to function correctly\.

1. Each AMI **must** contain everything a subscriber needs to use the software, including any client applications\.

1. For free or paid products, the fulfillment process **must not** require the customer to leave AWS Marketplace\.

1. AMIs **must not** require a subscription API or launches from outside AWS Marketplace\.

1. Products **must not** use copyrighted material that you don't have the rights to use\.

1. Product software and metadata **must not** contain language that redirects users to other cloud platforms, additional products, or upsell services that aren't available on AWS Marketplace\.

## Architecture<a name="architecture"></a>

1. Source AMIs for AWS Marketplace **MUST** be provided in the US East \(N\. Virginia\) Region\.

1. AMIs **must** use HVM virtualization\.

1. AMIs **must** use 64\-bit architecture\.

1. AMIs **must** be AMIs backed by Amazon EBS\. Currently we don't support AMIs backed by Amazon S3\.

1. AMIs **must** use a supported file system to pass AMI Self\-Service Scanning\. The supported file systems are Ext2, Ext3, Ext4, Xfs, Vfat, Lvm, and NTFS\. Encrypted file systems aren't supported\.

1. FreeBSD products **must** be built from a Linux\-based OS\.

1. AMIs **must** be built so that they can run in all regions and are region\-agnostic\. AMIs built differently for different regions aren't allowed\.

## AMI File Upload<a name="amis-file-upload"></a>

Self\-service AMI scanning is available in the AWS Marketplace Management Portal\. With this feature, you can initiate scans of your AMIs and receive scanning results quickly—typically in less than an hour—with clear feedback in a single location\. For more information, see [AMI Self\-Service Scanning](https://aws.amazon.com/marketplace/management/manage-products/#/build.build-new)\. 

To upload a new product load form, click the **File Upload** tab at the top of the AWS Marketplace Management Portal\. From there, you can download the most recent product load template\. We strongly recommend checking that the form is the most recent because it's consistently updated with more instance types and regions as they become available\. Using AMI Self\-Service Scanning significantly increases the ease of loading the page\. 