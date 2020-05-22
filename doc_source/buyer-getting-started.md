# Getting started<a name="buyer-getting-started"></a>

The following topics outline the process of getting started with software products as a AWS Marketplace buyer\.

**Topics**
+ [Step 1: Choose your software ](#step-1-choose-your-software)
+ [Step 2: Sign in to AWS Marketplace](#step-2-sign-in-to-the-aws-marketplace)
+ [Step 3: Launch your software on Amazon Elastic Compute Cloud \(Amazon EC2\)](#step-3-launch-your-software-on-amazon-elastic-compute-cloud-amazon-ec2)
+ [Step 4: Manage your software](#step-4-manage-your-software)
+ [Step 5: Terminate your instance](#step-5-terminate-your-instance)
+ [Where to go next](#where-to-go-next)
+ [Buying products](buyer-subscribing-to-products.md)
+ [Launching software](buyer-launching-software.md)
+ [Software and services on AWS Marketplace](buyer-software-and-services.md)

For information on getting started with data products, see [Subscribing to Data Products on AWS Data Exchange](https://docs.aws.amazon.com/data-exchange/latest/userguide/subscribe-to-data-sets.html) in the *AWS Data Exchange User Guide*\.

## Step 1: Choose your software <a name="step-1-choose-your-software"></a>

 At AWS Marketplace, you will find five different categories of software: 
+  Software Infrastructure 
+  Developer Tools 
+  Business Software 
+  IoT 
+  Desktop Apps 

Each major software category contains more specific subcategories of software\. So, for example, the Software Infrastructure category contains subcategories such as Application Development, Databases & Caching, and Operating Systems\. Software is available as either Amazon Machine Images \(AMIs\) or as Software as a Service \(SaaS\)\. For information on the differences AMIs and SaaS, see [Product types](buyer-product-types.md)\. 

 To aid you in choosing the software you need, AWS Marketplace provides the following information: 
+  Seller details 
+  Software version 
+  Type of software \(AMI or SaaS\), and information about the AMI if applicable 
+  Buyer rating 
+  Price 
+  Product information 

### To choose your software<a name="to-choose-your-software"></a>

1. Navigate to [AWS Marketplace](https://aws.amazon.com/marketplace)\. The **Shop All Categories** pane contains the list of categories you can choose from\. You can also choose software featured in the middle pane\. For this walkthrough, in the **Shop All Categories** pane, choose **Content Management**\. 

1.  From the **Content Management** list, choose **BitNami WordPress**\. 

1.  On the product details page, review the product information and choose **Continue**\. The product details page includes additional information such as: 
   +  Buyer rating 
   +  Support offering 
   +  Highlights 
   +  Detailed product description 
   +  Pricing details for instance types in each Region \(for AMIs\) 
   +  Additional resources to help you get started 

**Note**  
 If you chose a SaaS solution, choose **Visit Site** to get more information and to sign up\. 

## Step 2: Sign in to AWS Marketplace<a name="step-2-sign-in-to-the-aws-marketplace"></a>

 After you complete step 1, you are directed to sign in to the AWS Marketplace\. If you already have an AWS account, you can use that account to sign in\. If you don't already have an AWS account, use the following procedure to create one\. 

**Note**  
 When you create an account, AWS automatically signs up the account for all AWS services\. You are charged only for the services you use\. 

### To create an AWS account<a name="to-create-an-aws-account"></a>

1.  From the **Sign In or Create an Account** page, choose **Create a New Account**\. 

1.  Follow the on\-screen instructions\. 

 As part of the sign\-in procedure, you will receive a phone call and enter a PIN using your phone keypad\. 

## Step 3: Launch your software on Amazon Elastic Compute Cloud \(Amazon EC2\)<a name="step-3-launch-your-software-on-amazon-elastic-compute-cloud-amazon-ec2"></a>

If you chose your software as an AMI, your next step is to launch an Amazon EC2 instance running the software product you've subscribed to\.  Subscribing to a product means that you have accepted the terms of the product\. If the product has a monthly fee, then upon subscription you will be charged the fee, which will be prorated based on the time remaining in the month\. No other charges will be assessed until you launch an EC2 instance with the AMI you have chosen\. 

Before you launch your Amazon EC2 instance, you need to decide if you want to launch with 1\-Click Launch or if you want to launch using the Amazon EC2 console\. 1\-Click Launch helps you launch quickly with recommended default options such as security groups and instance types\. With 1\-Click Launch, you can also see your estimated monthly bill\. If you prefer more options, such as launching in an Amazon Virtual Private Cloud \(Amazon VPC\) or using Spot Instances, then you should launch using EC2 console\. The following procedures walk you through subscribing to the product and launching an EC2 instance using either 1\-Click Launch or the EC2 Console\. 

### To launch on Amazon EC2 using 1\-Click Launch<a name="to-launch-on-amazon-ec2-using-1-click-launch"></a>

1.  On the **Launch on EC2** page, choose the **1\-Click Launch** view, and review the default settings\. If you want to change any of them, do the following: 
   +  Expand **Version**, and select the AMI version you want\. 
   +  Expand **Region**, and select the Region you want from the list\. 
   +  Expand **EC2 Instance Type**, and choose an instance type\. You will see the pricing information change under Pricing Details to match your selection\. You can also review the Monthly Estimate in the right pane\. 
   + Expand **Firewall Settings**, and choose an existing security group, or choose **Click new based on seller settings** to accept the default settings\. For more information about security groups, see [Amazon EC2 Security Groups for Linux Instances](http://docs.amazonwebservices.com/AWSEC2/latest/UserGuide/using-network-security.html) in the *Amazon EC2 User Guide for Linux Instances*\. 
   + Expand **Key Pair**, and choose an existing key pair if you have one\. If you do not have a key pair, you are prompted to create one\. For more information about Amazon EC2 key pairs, see [Amazon EC2 Key Pairs](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html)\.

1.  When you are satisfied with your settings, choose **Accept Terms & Launch with 1\-Click**\. 

### To launch on Amazon EC2 Using Launch with EC2 Console<a name="to-launch-on-amazon-ec2-using-launch-with-ec2-console"></a>

1.  On the Launch on EC2 page, choose the **Launch with EC2 Console** view, and then select an AMI version from the **Select a Version** list\. 

1.  Review the **Firewall Settings**, **Installation Instructions**, and **Release Notes**, and then choose **Launch with EC2 Console**\. 

1.  In the EC2 console, you will launch your AMI using the Request Instance Wizard\. Follow the instructions in [Getting Started with Amazon EC2 Linux Instances](http://docs.amazonwebservices.com/AWSEC2/latest/GettingStartedGuide/Welcome.html?r=9803) to navigate through the wizard\. 

## Step 4: Manage your software<a name="step-4-manage-your-software"></a>

 At any time, you can manage your software subscriptions in the AWS Marketplace by using the Your Software page\. On the **Your Software Subscriptions** page, you can do the following: 
+  View your instance status by product 
+  View your current monthly charges 
+  Run a new instance 
+  View seller profiles for your instance 
+  Link to the AWS Management Console to manage your instances 
+  Link directly to your Amazon EC2 instance so you can configure your software 

### To manage your software<a name="to-manage-your-software"></a>

1.  Navigate to [AWS Marketplace](https://aws.amazon.com/marketplace), and choose **Your Software**\. 

1. Use the **Your Software** page to manage your software subscriptions\. 

## Step 5: Terminate your instance<a name="step-5-terminate-your-instance"></a>

 When you've decided that you no longer need the instance, you can terminate it\. 

**Note**  
 You cannot restart a terminated instance\. However, you can launch additional instances of the same AMI\. 

### To terminate an instance<a name="to-terminate-an-instance"></a>

1.  Navigate to [AWS Marketplace](https://aws.amazon.com/marketplace/), and choose **Your Software**\. 

1.  On the **Your Software** page, next to the instance you want to terminate, choose **Manage in AWS Console**\. 

1.  In the AWS Management Console, open the EC2 console, right\-click the instance, and then choose **Terminate**\. 

1.  Choose **Yes, Terminate** when prompted for confirmation\. 

## Where to go next<a name="where-to-go-next"></a>

 For more information about product categories and types, see [Product categories](buyer-product-categories.md) and [Product types](buyer-product-types.md)\. 

 For more information about Amazon EC2, see the service documentation at [Amazon Elastic Compute Cloud Documentation](http://docs.aws.amazon.com/ec2/)\. 

 To learn more about AWS, see [https://aws\.amazon\.com/](https://aws.amazon.com/)\. 