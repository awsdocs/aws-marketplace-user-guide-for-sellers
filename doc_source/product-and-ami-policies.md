# AMI\-based product requirements<a name="product-and-ami-policies"></a>

AWS Marketplace maintains the following policies for all Amazon Machine Image \(AMI\) products and offerings in AWS Marketplace\. The policies promote a safe, secure, and trustworthy platform for our customers\.

All products and their related metadata are reviewed when they're submitted to ensure that they meet or exceed current AWS Marketplace policies\. These policies are reviewed and adjusted to meet evolving security guidelines\. AWS Marketplace continuously scans your products to verify that they meet changes to the security guidelines\. If products fall out of compliance, AWS Marketplace will contact you to update your AMI product to meet new standards\. Likewise, if a newly discovered vulnerability is found to affect the AMI, we will ask you to provide an updated AMI with the relevant updates in place\. You must use the [self\-service AMI scanning tool](https://aws.amazon.com/marketplace/management/manage-products) before submitting your AMI\. This tool helps ensure that the AMI meets AWS Marketplace policies\.

## Security policies<a name="security"></a>

All AMIs must adhere to the following security policies:
+ AMIs must not contain any known vulnerabilities, malware, or viruses as detected by the [self\-service AMI scanning tool](https://aws.amazon.com/marketplace/management/manage-products) or AWS Security\.
+ AMIs must use currently supported operating systems and other software packages\. Any version of an AMI with an End\-of\-Life \(EoL\) operating system or other software packages will be delisted from the AWS Marketplace\. You can build a new AMI with updated packages and publish it as a new version to AWS Marketplace\.
+ All instance authentication must use key pair access, not password\-based authentication, even if the password is generated, reset, or defined by the user at launch\. AMIs must not contain passwords, authentication keys, key pairs, security keys, or other credentials for any reason\.
+ AMIs must not request or use access or secret keys from users to access AWS resources\. If your AMI application requires access to the user account, it must be achieved through an AWS Identity and Access Management \(IAM\) role instantiated through AWS CloudFormation, which creates the instance and associates the appropriate role\. When single\-AMI launch is enabled for products with an AWS CloudFormation delivery method, corresponding usage instructions must include clear guidance for creating minimally privileged IAM roles\. For more information, see [AMI\-based delivery using AWS CloudFormation](cloudformation.md)\.
+ Linux\-based AMIs must not allow SSH password authentication\. Disable password authentication via your `sshd_config` file by setting `PasswordAuthentication` to `NO`\.

## Access policies<a name="accessibility"></a>

There are three categories of access policies: general, Linux\-specific, and Windows\-specific policies\. 

### General access policies<a name="general-ami-policies"></a>

All AMIs must adhere to the following general access policies:
+ AMIs must allow operating system \(OS\)\-level administration capabilities to allow for compliance requirements, vulnerability updates, and log file access\. Linux\-based AMIs use SSH, and Windows\-based AMIs use RDP\. 
+ AMIs must not contain authorized passwords or authorized keys\.
+ AMIs must not use fixed passwords for administrative access\. AMIs must use a randomized password instead\. An alternative implementation is to retrieve the instance metadata and use the `instance_id` as the password\. The administrator must be prompted for this randomized password before being permitted to set or change their own credentials\. For information about retrieving instance metadata, see [Instance Metadata and User Data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html) in the *Amazon EC2 User Guide for Linux Instances*\.
+ You must not have access to the customer's running instances\. The customer has to explicitly enable any outside access, and any accessibility built into the AMI must be off by default\.

### Linux\-specific access policies<a name="linux-specific-ami-policies"></a>

Linux\-based AMIs must adhere to the following access policies, as well as the general access policies:
+ Linux\-based AMIs must [disable password\-based remote logins](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/building-shared-amis.html#public-amis-disable-password-logins-for-root) for root access and allow only sudo access through a user account, not root\. Users must use sudo access through a user account and can't use root access\. Sudo access allows the administrator to control which users are allowed to perform root functions\. It also logs the activity for an audit trail\. AMIs must not contain authorized passwords or authorized keys\.
+ Linux\-based AMIs must not have blank or null root passwords\.

### Windows\-specific access policies<a name="windows-specific-ami-policies"></a>

Windows\-based AMIs must adhere to the following access policies, as well as the general access policies:
+ For Windows Server 2016 and later, use `EC2Launch`\.
+ For Windows Server 2012 R2 and earlier, use the most recent version of `Ec2ConfigService` and enable `Ec2SetPassword`, `Ec2WindowsActivate`, and `Ec2HandleUserData`\.
+ Remove guest accounts and remote desktop users, none of which are allowed\.

## Customer information policies<a name="customer-information"></a>

All AMIs must adhere to the following customer information policies:
+ Software must not collect or export customer data without the customer's knowledge and express consent except as required by BYOL \(Bring Your Own License\)\. Applications that collect or export customer data must follow these guidelines: 
  + The collection of the customer data must be self\-service, automated, and secure\. Buyers must not need to wait for sellers to approve to deploy the software\. 
  + The requirements for customer data must be clearly stated in the description or the usage instructions of the listing\. This includes what is collected, the location of where the customer data will be stored, and how it will be used\. For example, *This product collects your name and email address\. This information is sent to and stored by the <company name>\. This information will only be used to contact the buyer in regards to the <product name>\.* 
  + Payment information must not be collected\.

## Product usage policies<a name="product-usage"></a>

All AMIs must adhere to the following product usage policies:
+ Products must not restrict access to the product or product functionality by time, number of users, or other restrictions\. Beta and prerelease products, or products whose sole purpose is to offer trial or evaluation functionality, are not supported\. Developer, Community, and BYOL editions of commercial software are supported, provided an equivalent paid version is also available in AWS Marketplace\.
+ All AMIs must be compatible with either the Launch from Website experience or AMI\-based delivery through AWS CloudFormation\. For Launch from Website, the AMI can't require customer or user data at instance creation to function correctly\.
+ AMIs and their software must be deployable in a self\-service manner and must not require additional payment methods or costs\. Applications that require external dependencies on deployment must follow these guidelines:
  + The requirement must be disclosed in the description or the usage instructions of the listing\. For example, *This product requires an internet connection to deploy properly\. The following packages are downloaded on deployment: <list of package>\.* 
  + Sellers are responsible for the use of and ensuring the availability and security of all external dependencies\. 
  + If the external dependencies are no longer available, the product must be removed from AWS Marketplace as well\. 
  + The external dependencies must not require additional payment methods or costs\.
+ For all products except BYOL, the fulfillment process must not require the customer to leave AWS Marketplace\.
+ AMIs that require an ongoing connection to external resources not under the direct control of the buyer—for example, external APIs or AWS services managed by the seller or a third party—must follow these guidelines:
  + The requirement must be disclosed in the description or the usage instructions of the listing\. For example, *This product requires an ongoing internet connection\. The following ongoing external services are required to properly function: <list of resources>\.* 
  + Sellers are responsible for the use of and ensuring the availability and security of all external resources\.
  + If the external resources are no longer available, the product must be removed from AWS Marketplace as well\.
  + The external resources must not require additional payment methods or costs and the setup of the connection must be automated\.
+ Product software and metadata must not contain language that redirects users to other cloud platforms, additional products, or upsell services that aren't available in AWS Marketplace\.
+ If your product is an add\-on to another product or another ISV’s product, your product description must indicate that it extends the functionality of the other product and that without it, your product has very limited utility\. For example, *This product extends the functionality of <product name> and without it, this product has very limited utility\. Please note that <product name> might require its own license for full functionality with this listing\.*

## Architecture policies<a name="architecture"></a>

All AMIs must adhere to the following architecture policies:
+ Source AMIs for AWS Marketplace must be provided in the US East \(N\. Virginia\) Region\.
+ AMIs must use HVM virtualization\.
+ AMIs must use 64\-bit or 64\-bit ARM architecture\.
+ AMIs must be AMIs backed by Amazon Elastic Block Store \(Amazon EBS\)\. We don't support AMIs backed by Amazon Simple Storage Service \(Amazon S3\)\.
+ AMIs must not use encrypted EBS snaphots\.
+ AMIs must not use encrypted file systems\.
+ AMIs must be built so that they can run in all AWS Regions and are Region\-agnostic\. AMIs built differently for different Regions aren't allowed\.

## AMI product usage instructions<a name="ami-product-usage-instructions"></a>

When creating usage instructions for your AMI product, please follow the steps and guidance located in [AMI and container product usage instructions](ami-container-product-usage-instructions.md)\.