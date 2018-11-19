# Launching Software<a name="buyer-launching-software"></a>

 After you have subscribed, you can launch AMIs that contain the product software using the 1\-Click Launch view in AWS Marketplace, or by using other AWS management tools, including the AWS Management Console, the Amazon EC2 console, Amazon EC2 APIs, or the AWS CloudFormation console\. 

 The 1\-Click Launch view allows you to quickly review, modify, and then launch a single instance of the software with settings recommended by the software seller\. The **Launch with EC2 Console** view provides an easy way to find the AMI identification number and other pertinent information that is required to launch the AMI using the AWS Management Console, Amazon EC2 APIs, or other management tools\. 

 For AWS Marketplace products with complex topologies, the **Custom Launch** view provides a **Launch with CloudFormation Console** button that loads the product in the AWS CloudFormation console with the appropriate AWS CloudFormation template\. You can then follow the steps in the AWS CloudFormation console wizard to create the cluster of AMIs and associated AWS resources for that product\. 

## Launching Software Frequently Asked Questions<a name="launching-software-frequently-asked-questions"></a>

### When would I use Launch with EC2 Console instead of Launch with 1\-Click?<a name="when-would-i-use-launch-with-ec2-console-instead-of-launch-with-1-click"></a>

The 1\-Click Launch option helps you launch quickly using the recommended options\. If you prefer more options, such as launching in a VPC or using Spot Instances, then **Launch with EC2 Console** provides the information that you need to launch AWS Marketplace products via channels other than the AWS Marketplace website\. Examples include the Amazon EC2 Console or Amazon EC2 APIs\. The **1\-Click Launch** option is not supported in the AWS GovCloud \(US\) Region\. 

### How do I launch an AWS Marketplace product with the Amazon EC2 console?<a name="how-do-i-launch-an-aws-marketplace-product-with-the-ec2-console"></a>

 Follow these steps to launch an AWS Marketplace product with the Amazon EC2 console\.

1.  Navigate to AWS Marketplace\. 

1.  Locate the product by choosing **Your Marketplace Software** at the top of the page\. 

1.  Choose **Launch more software**, and choose **Manual Launch**\. 

1.  Choose the version of the software that you want to launch\. The default version is the most recent version\. 

1.  Choose **Launch with EC2 Console** for the Region you prefer, and then follow the rest of the steps in the console launch wizard\. 

1.  For launches into the AWS GovCloud \(US\) Region, log in to the AWS GovCloud \(US\) Amazon EC2 console using your AWS GovCloud \(US\) credentials\. 

 Follow these steps to launch an AWS Marketplace product from the AWS CloudFormation console: 

1.  Navigate to AWS Marketplace\. 

1.  Locate the product by choosing **Your Marketplace Software** at the top of the page\. 

1.  Choose **Launch more software**, and choose **Custom Launch**\. 

1.  Choose the version of the software that you would like to launch\. The default version is the most recent version\. 

1.  Choose the Region in which you want to deploy the software\. 

1.  Choose **Launch with CloudFormation Console**, and then follow the rest of the steps in the AWS CloudFormation console launch wizard\. 

### Why do I need to associate an IAM role with the instance running metering\-enabled AWS Marketplace products?<a name="why-do-i-need-to-associate-an-iam-role-with-the-instance-running-metering-enabled-aws-marketplace-products"></a>

 Metering\-enabled products use an IAM role to authenticate to the AWS Marketplace Metering Service to record software usage\. Your AWS Marketplace instance must have an internet connection to AWS services, and the instance must have an IAM role associated at the time of launch in order to successfully connect and authenticate to the AWS Marketplace Metering Service\. If your instance does not have an IAM role, the software cannot be launched\. 

### What IAM policy do I need to attach to the IAM role?<a name="what-iam-policy-do-i-need-to-attach-to-the-iam-role"></a>

 You need to add the IAM permission `aws-marketplace:MeterUsage` to the IAM role associated with your EC2 instance\. The easiest way to do this is to attach the AWS managed policy `AWSMarketplaceMeteringFullAccess` to the role\. 

### Why do some products not show up in Your Marketplace Software?<a name="why-do-some-products-not-show-up-in-your-marketplace-software"></a>

 Products that are listed as *sold by* Amazon Web Services use a slightly different mechanism for tracking usage so the customer experience is a little different too\. For these products, you do not need to accept terms before using these products\. Their terms of use are included in the AWS Service terms\. Because you do not need to subscribe, you will not receive a confirmation email the first time you use it\. 

 These products will not appear in **Your Marketplace Software**, but you can always find them by searching for them\. Additionally, charges for these products will appear on your bill as part of your Amazon EC2 charges, not as a separate software line item\. 

### How do I cancel an AWS Marketplace software subscription?<a name="how-do-i-cancel-an-aws-marketplace-software-subscription"></a>

 You can cancel your software subscription by going to **Your Marketplace Software** and choosing **Cancel Subscription**\. Canceling your subscription means that you can no longer launch new EC2 instances of this AMI or new stacks through AWS CloudFormation\. If the product has a monthly fee, you will no longer be billed for it\. 

 If you have any running instances, you must first terminate all instances of the software before canceling your subscription\. You can terminate instances using the AWS Management Console\. If the product was launched using AWS CloudFormation, you will also need to delete the stack from the AWS CloudFormation console to avoid being charged for infrastructure charges\. 

### How many instances of my software can I run?<a name="how-many-instances-of-my-software-can-i-run"></a>

 Amazon EC2 initially limits the number of instances you can run to 20 per region\. If you need more instances, complete the Amazon EC2 instance request form\. Your request for instances is tied to the region you request them for\. 

 Similarly, AWS CloudFormation initially limits the number of stacks to 20 per region\. If you need more stacks, complete a limit increase support ticket for AWS CloudFormation\. 

 For more information on making a request to increase a limit, see [AWS Service Limits](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\. 

### What happens when a vendor updates their product?<a name="what-happens-when-a-vendor-updates-their-product"></a>

 When the vendor publishes an update for a product to which you are subscribed, you should receive a notification email from AWS Marketplace that contains information about the update and provides installation instructions\. You can always navigate to the **Your Marketplace Software** page to find the latest version provided by the vendor\. 

### How do I allow others at my company to subscribe to products?<a name="how-do-i-allow-others-at-my-company-to-subscribe-to-products"></a>

 Don’t give others your AWS root credentials\. Instead, use AWS Identity and Access Management \(IAM\) to create an IAM user for each person who should have access to AWS Marketplace and give them appropriate permissions to work with your subscriptions\. People can then log in to AWS Marketplace using the IAM user credentials you’ve created\. For details, see [Controlling Access to AWS Marketplace Subscriptions](ControllingAccessToAWSMarketplaceSubscriptions.md)\. For permissions within AWS GovCloud \(US\), see the *[AWS GovCloud \(US\) Documentation](https://docs.aws.amazon.com/govcloud-us/index.html?id=docs_gateway#lang/en_us)*\. 