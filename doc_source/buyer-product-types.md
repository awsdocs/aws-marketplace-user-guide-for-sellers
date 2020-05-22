# Product types<a name="buyer-product-types"></a>

AWS Marketplace includes popular open source and commercial software, as well as free and paid data products from AWS Data Exchange\. These products are available in different ways: as individual Amazon Machine Images \(AMIs\), as a cluster of AMIs deployed through an AWS CloudFormation template, as software\-as\-a\-service \(SaaS\), and as AWS Data Exchange data products\.

## What is an AMI?<a name="what-is-an-ami"></a>

 AMI is the acronym for Amazon Machine Image\. An Amazon Machine Image \(AMI\) is an image of a server, including an operating system and often additional software, which runs on AWS\. 

## How are AMI products different than SaaS products?<a name="how-are-ami-products-different-than-saas-products"></a>

 Both AMI and SaaS \(software as a service\) product listings are from trusted sellers\. AMI products run within a customer's AWS account\. You retain more control over software configuration and over the servers that run the software, but you also have additional responsibilities regarding server configuration and maintenance\. 

## Why do AWS Marketplace products have more than one AMI?<a name="why-do-aws-marketplace-products-have-more-than-one-ami"></a>

 An AWS Marketplace product contains one AMI for each region in which the product is available\. These AMIs are identical except for their location\. Additionally, when sellers update their product with the latest patches and updates, they may add another set of AMIs to the product\. 

 Some AWS Marketplace products may launch multiple instances of an AMI because they are deployed as a cluster using CloudFormation templates\. This cluster of instances, along with additional AWS infrastructure services configured by the CloudFormation template, act as a single product deployment\. 

## What is AWS CloudFormation?<a name="what-is-aws-cloudformation"></a>

 AWS CloudFormation is a service that helps you model and set up your AWS resources so that you can spend less time managing those resources and more time focusing on your applications that run in AWS\. An AWS CloudFormation template describes the various AWS resources that you want \(like Amazon EC2 instances or Amazon Relational Database Service \(RDS\) database instances\), and AWS CloudFormation takes care of provisioning and configuring those resources for you\. For more information, see [Getting Started with AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/GettingStarted.html) \. 

## How can I use AWS CloudFormation templates to deploy software products from AWS Marketplace?<a name="how-can-i-use-aws-cloudformation-templates-to-deploy-software-products-from-aws-marketplace"></a>

Software sellers may offer AWS CloudFormation templates to define a preferred deployment topology consisting of multiple AMI instances and other AWS resources\. If an AWS CloudFormation template is available for a product it will be listed as a deployment option on the product listing page\. 

## How is deploying an AMI different from deploying a cluster of AMIs using an AWS CloudFormation template?<a name="how-is-deploying-an-ami-different-from-deploying-a-cluster-of-amis-using-an-aws-cloudformation-template"></a>

You can use an AMI to deploy a single EC2 instance\. You can use a CloudFormation template to deploy multiple instances of an AMI that act as a cluster—along with AWS resources such as Amazon RDS, Amazon Simple Storage Service \(S3\), or any other AWS service—as a single solution\. 

## How are these products different from the products I can find in the AWS Community AMI catalog?<a name="how-are-these-products-different-than-the-products-i-can-find-in-the-aws-community-ami-catalog"></a>

The AWS Marketplace catalog contains a curated selection of open source and commercial software from well\-known sellers\. Many products on AWS Marketplace can be purchased by the hour\. 

 The AMI catalog is a community resource where people and development teams can list and exchange software or projects under development, without having to go through extensive vetting\. Listings in the community AMI catalog may or may not be from well\-known sellers and generally have not undergone additional investigations\. 

## Does AWS Marketplace also sell software for me to install on my on\-premises servers or PCs?<a name="does-aws-marketplace-also-sell-software-for-me-to-install-on-my-on-premises-servers-or-pcs"></a>

 No\. The software listed in AWS Marketplace is only available to run on Amazon EC2\. It is not available for download\. 