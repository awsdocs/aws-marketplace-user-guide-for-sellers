# AMI\-based delivery using AWS CloudFormation<a name="cloudformation"></a>

AWS Marketplace sellers can list AMI\-based products that are delivered to AWS Marketplace buyers by using AWS CloudFormation templates\. You can use the templates to define a cluster or distributed architecture for the products or to select different AMI combinations or product configurations\. The AWS CloudFormation templates can be configured to deliver a single Amazon Machine Image \(AMI\) or multiple AMIs along with associated config files and Lambda functions\. Buyers can browse the selection of solutions on AWS Marketplace, buy with one click, and deploy by using AWS CloudFormation templates that you provide\.

Multi\-AMI solutions can contain up to 20 AMIs and up to 20 AWS CloudFormation templates\. Each AWS CloudFormation template can reference any combination or subset of the AMIs contained in the solution\. The buyer purchases a single solution that entitles them to all of the AMIs in that product\. When the product has multiple AMIs, each AMI has its own unique product code and can be priced and metered separately\. However, individual components of a solution aren't discoverable or procurable outside the context of the product\.

If you have existing single\-AMI products, you can't migrate or combine them into a new multi\-AMI listing\. However, your new solution can feature the same software or copies of AMIs used by existing products\. Each listing created on AWS Marketplace is a listing with new product codes\.

You can also include Lambda functions in a Serverless Application with your AMI so that buyers can deploy them through CloudFormation\. For instructions on how to include Lambda functions and serverless applications with your AMI, see [Adding serverless application components](cloudformation-serverless-application.md)\. 

## Building your product listing<a name="building-your-product-listing"></a>

To submit your product, you need to prepare and validate your AMI\(s\), create your AWS CloudFormation template\(s\), create a topology diagram, complete the product load form, and submit the materials to AWS Marketplace\. We recommend that you start by creating and validating your AMI\(s\) and then complete and validate the AWS CloudFormation template\(s\)\. After you complete those steps, you should create a topology diagram and estimate the software and infrastructure price\. AWS Marketplace validates your submission and works with you to make your product public\. Use the [AWS Pricing Calculator](https://calculator.aws/#/) to help estimate the infrastructure cost for your template\. Provide AWS Marketplace with a link to your saved calculator configuration\. The following are limitations of multi\-AMI solution products:
+ Updating existing AWS Marketplace products from a standalone product to a multi\-AMI product isn't supported\. To make a product available in a multi\-AMI product, copy the AMI and submit it as a component to a new multi\-AMI product\. The resulting AMI has a unique product code that's different from the previous product's code\.
+ Multi\-AMI solutions aren't visible on the **AWS Marketplace** tab of the **Launch Instance** page in the Amazon Elastic Compute Cloud \(Amazon EC2\) console\. 
+ An AWS CloudFormation template must not launch AMIs outside of those listed in the multi\-AMI solution\.
+ AWS CloudFormation templates must be submitted in the form of a public URL\. All nested template URLs contained in the template must also be publicly accessible\. 

## Preparing your AWS CloudFormation template<a name="aws-cloudformation-template-preparation"></a>

To build your AWS CloudFormation templates, you must meet the template prerequisites and provide the required input and security parameters\. When submitting your AWS CloudFormation template, use the guidelines in the following sections\.

### Template prerequisites<a name="template-prerequisites"></a>
+ Verify that the template is launched successfully through the AWS CloudFormation console **in all Regions enabled for your product**\. You can use this tool to test your templates: [https://github\.com/aws\-quickstart/taskcat](https://github.com/aws-quickstart/taskcat)\.
+ If you are creating a single\-AMI product, the template must contain only one AMI\.
+ AMIs must be in a [mapping table](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/mappings-section-structure.html) for each region\. The AWS Marketplace team updates the AMI IDs after they're cloned\.
+ Build templates so that they do not depend on the use in a particular availability zone \(AZ\)\. Not all customers have access to all AZs, and AZs are mapped differently for different accounts\.
+ You can include dependencies such as Lambda functions, config files, and scripts with your AMI\. For more information, see [Create a serverless application](cloudformation-serverless-application.md#cloudformation-serverless-application-procedure-step-1)\.
+ If you're building a clustered solution using an Auto Scaling group, we recommend that you account for a scaling event\. The new node should join the running cluster automatically\.
+ Even for single\-node products, we recommend using an [Auto Scaling group](http://docs.aws.amazon.com/autoscaling/latest/userguide/create-asg-from-instance.html)\.
+ If your solution involves a cluster of multiple instances, consider using placement groups if you want low network latency, high network throughput, or both among the instances\.
+ If your solution involves Docker containers, you must incorporate the Docker images into the AMI\.
+ For ease of review by the AWS Marketplace team and transparency to the customer, we recommend that you add comments in your **UserData** section\.

### Template input parameters<a name="template-input-parameters"></a>
+ Input parameters to the template must not include the AWS Marketplace customer's AWS credentials \(such as passwords, public keys, private keys, or certificates\) or personal information such as email address\.
+ Do not set defaults for parameters such as remote access, CIDR/IP, or passwords for databases\. The customer must provide these as input parameters\.
+ For sensitive inputs such as passwords, choose the `No Echo` property and enable stronger regular expression\. For other inputs, set the most common inputs along with appropriate helper text\.
+ Use AWS CloudFormation parameter types for inputs where available\.
+ Use `AWS::CloudFormation::Interface` to group and sort input parameters\.

### Network and security parameters<a name="networksecurity-parameters"></a>
+ Ensure that the default SSH port \(22\) or RDP port \(3389\) isn't open to 0\.0\.0\.0\.
+ Instead of using the default virtual private cloud \(VPC\), we recommend that you build a VPC with appropriate access control lists \(ACLs\) and security groups\. Only AWS accounts created before December 4, 2013, support EC2\-Classic\.
+ Access to the customer's AWS environment should be enabled using an IAM role to call [AssumeRole](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) from the AWS Security Token Service\. 
+ Set IAM roles and policies to [grant the least privilege](http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege) and enable write access only when absolutely necessary\. For example, if your application needs only `S3:GET`, `PUT`, and `DELETE` operations, specify those actions only\. We don't recommend the use of `S3:*` in this case\. 

After your template is received, AWS Marketplace validates the product configuration and information and provides feedback for any required revisions\.

## Getting the cost estimate for your template infrastructure<a name="template-infrastructure-cost-estimate"></a>

The infrastructure cost estimate for each template displayed to customers is based on an estimate that you provide by using the [AWS Pricing Calculator](https://calculator.aws/#/)\. The estimation should include the list of services to be deployed as part of the template, along with the default values for a typical deployment\.

After you calculate the template's estimated monthly cost, provide AWS Marketplace with the **Save and Share** link for the US East \(N\. Virginia\) Region\. This is part of the submission process\.

## Topology diagram<a name="topology-diagram"></a>

You must provide a topology diagram for each template\. The diagram must use the [AWS product icons](https://aws.amazon.com/architecture/icons/) for each AWS service deployed through the AWS CloudFormation template, and it must include metadata for the services\. The diagram must be 1100 x 700 pixels in size\. Make sure that your diagram meets this sizing requirement to avoid cropping or stretching, as shown in the following image\.

 ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/cloudformation-02.png) 

## Meeting the submission requirements<a name="requirements"></a>

To submit products delivered by using AWS CloudFormation templates, you must provide the following resources: 
+ AWS CloudFormation template or templates
  + A single\-AMI product can have one to three AWS CloudFormation templates
  + A multi\-AMI product can have up to 20 AWS CloudFormation templates
+ The estimated infrastructure price for the default configuration of each template
+ A topology diagram and topology metadata
+ Completed product form \(available from the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/)\)
  + For single\-AMI products, use the [Commercial Product](https://s3.amazonaws.com/awsmp-loadforms/ProductDataLoad-Current.xlsx) form
  + For multi\-AMI products, use the [Multi\-AMI Product form](https://s3.amazonaws.com/awsmp-loadforms/AWS_Marketplace_Product_Load_Form_CAR_Multi_AMI.xlsx) form

The product forms include example submissions for your reference\.

For each product, most of the required product data and metadata are the same as for traditional single\-AMI products\. Therefore, each AMI that is delivered by using an AWS CloudFormation template must continue to meet the standards and requirements described for AWS Marketplace\.

For each AWS CloudFormation template, you must also provide the following information\.


|  Field  |  Description  |  Restrictions  | 
| --- | --- | --- | 
|  Title  |  Title of the topology\. This appears on the detail and fulfillment pages and the pop\-up that shows the topology details\.  |  50 characters  | 
|  Short description  |  This appears on the detail and fulfillment pages\.  |  200 characters  | 
|  Long description  |  This appears in the topology details pop\-up\.  |  2000 characters  | 

For multi\-AMI products, the following fields are required:
+ Solution title
+ Solution short description
+ Solution long description
+ For AWS CloudFormation templates \(up to 20 per solution\)
  + Deployment title \(per template\)
  + Short description \(per template\)
  + Long description \(per template\)
  + Architecture diagram \(per template\)
  + Infrastructure pricing estimate \(per template\)
  + List of products/components contained in this AWS CloudFormation template
  + List of regions supported by this AWS CloudFormation template

## Submitting your product request<a name="submitting-your-listing"></a>

Use the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/) to submit your product\. On the **Assets** tab, choose **File Upload**\. Upload any files you want to submit and enter a brief description\. Allow three to five weeks for request processing, including:
+ Review of the AWS CloudFormation template, AMI, and metadata for the AMI and AWS CloudFormation template
+ Publication of your AWS CloudFormation template to AWS Marketplace products