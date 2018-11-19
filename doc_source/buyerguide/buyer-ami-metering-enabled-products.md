# Metering\-Enabled AMI Products<a name="buyer-ami-metering-enabled-products"></a>

 Some products listed on AWS Marketplace are billed on usage measured by the software application\. Examples of metered usage dimensions include Data usage, Host/Agent usage, or Bandwidth usage\. These products require extra configuration to function correctly\. An IAM role with the permission to meter usage must be associated with your AWS Marketplace EC2 instance at the time of launch\. For more information on IAM roles for Amazon EC2, see [IAM Roles for Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html)\. 

## Frequently Asked Questions<a name="ami-metering-enabled-products-frequently-asked-questions"></a>

### Why do I need to associate an IAM role to metering\-enabled AWS Marketplace instances?<a name="why-do-i-need-to-associate-an-iam-role-to-metering-enabled-aws-marketplace-instances"></a>

 Metering\-enabled products use an IAM role to authenticate to the AWS Marketplace Metering Service to record software usage\. Your AWS Marketplace instance must have an internet connection to AWS services, and the instance must have an IAM role associated at the time of launch in order to successfully connect and authenticate to the AWS Marketplace Metering Service\. If your instance does not have an IAM role associated, the software cannot be launched\. 

### What permission or policy do I need to attach to the IAM role?<a name="what-permission-or-policy-do-i-need-to-attach-to-the-iam-role"></a>

 You can choose to have an IAM role with necessary permissions be automatically created for you during the **Configure Instance** step of the Launch Instance Wizard\. If you choose to create the IAM role manually, you will need to add a permission policy allowing `aws-marketplace:MeterUsage` action\. The easiest way to do this is to attach the AWS managed policy `AWSMarketplaceMeteringFullAccess` to the IAM role\. 

### What happens if I don’t associate an IAM role to the AWS Marketplace instance?<a name="what-happens-if-i-dont-associate-an-iam-role-to-the-aws-marketplace-instance"></a>

 If you do not associate an IAM role to your AWS Marketplace EC2 instance at launch time, the software will not function\. You cannot associate an IAM role to a running EC2 instance, so be sure to associate the IAM role at launch time\. 

### Am I still billed hourly for metering\-enabled products?<a name="am-i-still-billed-hourly-for-metering-enabled-products"></a>

 Yes, but instead of being billed a fixed hourly rate, you will be billed based on the amount of software usage \(Data, Hosts, or Bandwidth, depending on which billing dimension has been designated by the software’s vendor\) in each hour\. If you have no usage in an hour, you will not incur any software fees\. 