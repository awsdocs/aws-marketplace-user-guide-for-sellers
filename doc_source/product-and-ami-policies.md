# AMI security policies<a name="product-and-ami-policies"></a>

AWS Marketplace maintains the following policies for all products and offerings on AWS Marketplace to promote a safe, secure, and trustworthy platform for our customers\.

All products and metadata are reviewed when they're submitted to ensure that they meet or exceed current AWS Marketplace policies\. These policies are reviewed and adjusted to meet evolving security guidelines\. AWS Marketplace continuously scans your products to verify that they meet changes to the security guidelines\. If products fall out of compliance, we might require that you update your AMI product to meet new standards\. Likewise, if a newly discovered vulnerability is found to affect the AMI, you will be asked to provide an updated AMI with the relevant updates in place\. You must use the [self\-service AMI scanning tool](https://aws.amazon.com/marketplace/management/manage-products/#/manage-amis.unshared) before submitting your AMI\. This helps ensure that the AMI meets AWS Marketplace policies\.

## Security<a name="security"></a>

All AMIs must adhere to the following security policies:
+ AMIs must not contain any known vulnerabilities, malware, or viruses as detected by the [self\-service AMI scanning tool](https://aws.amazon.com/marketplace/management/manage-products/#/manage-amis.unshared) or AWS Security\.
+ All instance authentication must use key pair access, not password\-based authentication, even if the password is generated, reset, or defined by the user at launch\. AMIs must not contain passwords, authentication keys, key pairs, security keys, or other credentials for any reason\.
+ AMIs must not request or use access or secret keys from users to access AWS resources\. If your AMI application requires access to the user account, it must be achieved through an IAM role instantiated through AWS CloudFormation, which creates the instance and associates the appropriate role\. Where single\-AMI launch is enabled for products with an AWS CloudFormation delivery method, corresponding usage instructions must include clear guidance for creating minimally privileged IAM roles\. For more information, see [AMI\-based delivery using AWS CloudFormation](cloudformation.md)\.
+ Linux\-based AMIs must not allow SSH password authentication\. Disable password authentication via your `sshd_config` file by setting `PasswordAuthentication` to `NO`\.

## Accessibility<a name="accessibility"></a>

The are three categories of accessibility policies: general, Linux\-specific, and Windows\-specific policies\. 

### General accessibility policies<a name="general-ami-policies"></a>

All AMIs must adhere to the following policies:
+ AMIs must allow OS\-level administration capabilities to allow for compliance requirements, vulnerability updates, and log file access\. Linux\-based AMIs use SSH, and Windows\-based AMIs use RDP\. 
+ AMIs must not contain authorized passwords or authorized keys\.
+ AMIs must not use fixed passwords for administrative access\. AMIs must use a randomized password instead\. An alternative implementation is to retrieve the instance metadata and use the `instance_id` as the password\. The administrator must be prompted for this randomized password before being permitted to set or change their own credentials\. For information about retrieving instance metadata, see [Instance Metadata and User Data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html) in the *Amazon EC2 User Guide for Linux Instances*\.
+ You must not have access to the customer's running instances\. The customer has to explicitly enable any outside access, and any accessibility built into the AMI must be off by default\.

### Linux\-specific policies<a name="linux-specific-ami-policies"></a>

Linux\-based AMIs must adhere to the following policies, as well as the general\-accessibility policies:
+ Linux\-based AMIs must [disable password\-based remote logins](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/building-shared-amis.html#public-amis-disable-password-logins-for-root) for root and allow only sudo access through a user account, not root\. Users must use sudo access through a user account and can't use root access\. Sudo access allows the administrator to control which users are allowed to perform root functions\. It also logs the activity for an audit trail\. AMIs must not contain authorized passwords or authorized keys\.
+ Linux\-based AMIs must not have blank or null root passwords\.

### Windows\-specific policies<a name="windows-specific-ami-policies"></a>

Windows\-based AMIs must adhere to the following policies, as well as the general\-accessibility policies:
+ For Windows Server 2012 R2 and earlier, use the most recent version of `Ec2ConfigService` and enable `Ec2SetPassword`, `Ec2WindowsActivate`, and `Ec2HandleUserData`\.
+ For Windows Server 2016 and later, use `EC2Launch`\.
+ Remove guest accounts or remote desktop users, none of which are allowed\.

## Customer information<a name="customer-information"></a>

All AMIs must adhere to the following customer\-information policies:
+ AMI products must not require customers to register with the seller or require customers provide any identifying information to use the product, except as required by BYOL \(Bring Your Own License\) products\. 
+ Software must not require, collect, or export customer data without the customer's knowledge and express consent\. 

## Product usage<a name="product-usage"></a>

All AMIs must adhere to the following product\-usage policies:
+ Products must not restrict access to the product or product functionality by time, number of users or other restrictions\. Beta and pre\-release products, or products whose sole purpose is to offer trial or evaluation functionality, are not supported\. Developer, Community, and BYOL editions of commercial software are supported, provided an equivalent paid version is also available on AWS Marketplace\.
+ All AMIs must be compatible with either the Launch from Website experience or AMI\-based delivery through AWS CloudFormation\. For Launch from Website, the AMI can't require customer or user data at instance creation to function correctly\.
+ Each AMI must contain everything that a buyer needs to use the software, including any client applications\.
+ For all products except BYOL, the fulfillment process must not require the customer to leave AWS Marketplace\.
+ AMIs must not require a subscription API or launches from outside AWS Marketplace\.
+ Product software and metadata must not contain language that redirects users to other cloud platforms, additional products, or up sell services that aren't available on AWS Marketplace\.

## Architecture<a name="architecture"></a>

All AMIs must adhere to the following architecture policies:
+ Source AMIs for AWS Marketplace must be provided in the US East \(N\. Virginia\) Region\.
+ AMIs must use HVM virtualization\.
+ AMIs must use 64\-bit or 64\-bit ARM architecture\.
+ AMIs must be AMIs backed by Amazon EBS\. We don't support AMIs backed by Amazon S3\.
+ AMIs must use a supported file system to pass [self\-service AMI scanning tool](https://aws.amazon.com/marketplace/management/manage-products/#/manage-amis.unshared) validation\. The supported file systems are Ext2, Ext3, Ext4, Xfs, Vfat, Lvm, and NTFS\. Encrypted file systems aren't supported\.
+ FreeBSD products must be built from a Linux\-based OS\.
+ AMIs must be built so that they can run in all Regions and are Region\-agnostic\. AMIs built differently for different Regions aren't allowed\.