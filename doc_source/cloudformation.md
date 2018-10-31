# AMI\-based Delivery Using AWS CloudFormation<a name="cloudformation"></a>

AWS Marketplace vendors can list AMI\-based products that are delivered to AWS Marketplace customers by using AWS CloudFormation templates\. This feature was previously known as Clusters and AWS Resources \(CAR\)\. You can use the templates to define a cluster or distributed architecture for the products or to select different AMI combinations or product configurations\. The AWS CloudFormation templates can be configured to deliver a single Amazon Machine Image \(AMI\) or multiple AMIs\. Customers can browse the selection of solutions on AWS Marketplace, subscribe with one click, and deploy by using AWS CloudFormation templates that you provide\.

Multi\-AMI solutions can contain up to 20 AMIs and up to 20 AWS CloudFormation templates\. Each AWS CloudFormation template can reference any combination or subset of the AMIs contained in the solution\. The customer subscribes to a single solution that entitles them to all of the AMIs in that product listing\. When the product has multiple AMIs, each AMI has its own unique product code and can be priced and metered separately\. However, individual components of a solution aren't discoverable or procurable outside the context of the listing\.

If you have existing single\-AMI products, you can't migrate or combine them into a new multi\-AMI listing\. However, your new solution can feature the same software or copies of AMIs used by existing products\. Each listing created on AWS Marketplace is a listing with new product codes\.

## Building Your Product Listing<a name="building-your-product-listing"></a>

To submit your product, you need to prepare and validate your AMI\(s\), create your AWS CloudFormation template\(s\), create a topology diagram, complete the product load form, and submit the materials to AWS Marketplace\. We recommend that you start by creating and validating your AMI\(s\) and then complete and validate the AWS CloudFormation template\(s\)\. After those steps are complete, you should create a topology diagram and estimate the software and infrastructure price\. AWS Marketplace validates your submission and works with you to make your listing public\. Use the [AWS Simple Monthly Calculator](http://calculator.s3.amazonaws.com/index.html) to help estimate the infrastructure cost for your template\. Provide AWS Marketplace with a link to your saved calculator configuration\. The following are limitations of multi\-AMI solution listings:
+  Updating existing AWS Marketplace listings from a standalone listing to a multi\-AMI listing isn't currently supported\. To make a product available in a multi\-AMI listing, copy the AMI and submit it as a component to a new multi\-AMI listing\. The resulting AMI has a unique product code, different from that of the previous listing\.
+ Multi\-AMI solutions aren't visible on the **AWS Marketplace** tab of the **Launch Instance** page in the Amazon Elastic Compute Cloud \(Amazon EC2\) console\. 
+ An AWS CloudFormation template must not launch AMIs outside of those listed in the multi\-AMI solution\.
+  AWS CloudFormation templates must be submitted in the form of a public URL\. All nested template URLs contained in the template must also be publicly accessible\. 

## Preparing Your AWS CloudFormation Template<a name="aws-cloudformation-template-preparation"></a>

To build your AWS CloudFormation templates, you must meet the template prerequisites and provide the required input and security parameters\. When submitting your AWS CloudFormation template, use the guidelines in the following sections\.

### Template Prerequisites<a name="template-prerequisites"></a>
+ Verify that the template is launched successfully through the AWS CloudFormation console **in all regions enabled for your product**\. You can use this tool to test your templates: [https://github\.com/aws\-quickstart/taskcat](https://github.com/aws-quickstart/taskcat)\.
+ If you are creating a single\-AMI product, the template must contain only one AMI\.
+ AMIs must be in a [mapping table](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/mappings-section-structure.html) for each region\. The AWS Marketplace team updates the AMI IDs after they're cloned\.
+ Build templates so that they do not depend on the use in a particular Availability Zone \(AZ\)\. Not all customers have access to all AZs, and AZs are mapped differently for different accounts\.
+ Every piece of software and its dependencies must be fully incorporated into the AMI\. You can't use scripts to update the package or prepare the package for use\. If you have AWS Lambda functions, they must be either incorporated into an AMI or written inline as part of the template\. They can't be loaded from an Amazon Simple Storage Service bucket\.
+ If you're building a clustered solution using an Auto Scaling group, we recommend that you account for a scaling event\. The new node should join the running cluster automatically\.
+ Even for single\-node products, we recommend using an [Auto Scaling group](http://docs.aws.amazon.com/autoscaling/latest/userguide/create-asg-from-instance.html)\.
+ If your solution involves a cluster of multiple instances, consider using placement groups if you want low network latency, high network throughput, or both among the instances\.
+ If your solution involves Docker containers, you must incorporate the Docker images into the AMI\.
+ For ease of review by the AWS Marketplace team and transparency to the customer, we recommend that you add comments in your **UserData** section\.

### Template Input Parameters<a name="template-input-parameters"></a>
+ Input parameters to the template must not include the AWS Marketplace customer's AWS credentials \(such as passwords, public keys, private keys, or certificates\) or personal information such as email address\.
+ Do not set defaults for parameters such as remote access, CIDR/IP, or passwords for databases\. The customer must provide these as input parameters\.
+ For sensitive inputs such as passwords, choose the `No Echo` property and enable stronger regular expression\. For other inputs, set the most common inputs along with appropriate helper text\.
+ Use AWS CloudFormation parameter types for inputs where available\.
+ Use `AWS::CloudFormation::Interface` to group and sort input parameters\.

### Network and Security Parameters<a name="networksecurity-parameters"></a>
+ Ensure that the default SSH port \(22\) or RDP port \(3389\) isn't open to 0\.0\.0\.0\.
+ Instead of using the default virtual private cloud \(VPC\), we recommend that you build a VPC with appropriate access control lists \(ACLs\) and security groups\. Only AWS accounts created before December 4, 2013, support EC2\-Classic\.
+ Access to the customer's AWS environment should be enabled using an IAM role to call [AssumeRole](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) from the AWS Security Token Service\. 
+ Set IAM roles and policies to [grant the least privilege](http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege) and enable write access only when absolutely necessary\. For example, if your application needs only `S3:GET`, `PUT`, and `DELETE` operations, specify those actions only\. We don't recommend the use of `S3:*` in this case\. 

After your template is received, AWS Marketplace validates the product configuration and information and provides feedback for any required revisions\.

## Getting the Cost Estimate for Your Template Infrastructure<a name="template-infrastructure-cost-estimate"></a>

The infrastructure cost estimate for each template displayed to customers is based on an estimate that you provide by using the [AWS Simple Monthly Calculator](http://calculator.s3.amazonaws.com/index.html), as shown in the following image\. The estimation should include the list of services to be deployed as part of the template, along with the default values for a typical deployment\.

 ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/cloudformation-01.png) 

After you have calculated the template's estimated monthly cost, provide AWS Marketplace with the **Save and Share** link for the US East \(N\. Virginia\) Region\. This is part of the submission process\.

## Topology Diagram<a name="topology-diagram"></a>

You must provide a topology diagram for each template\. The diagram must use the [AWS product icons](https://aws.amazon.com/architecture/icons/) for each AWS service deployed through the AWS CloudFormation template, and it must include metadata for the services\. The diagram must be 1100 x 700 pixels in size\. Make sure that your diagram meets this sizing requirement to avoid cropping or stretching, as shown in the following image\.

 ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/cloudformation-02.png) 

## Meeting the Submission Requirements<a name="requirements"></a>

To submit products delivered by using AWS CloudFormation templates, you must provide the following resources: 
+ AWS CloudFormation template\(s\)
  + A single\-AMI listing can have one to three AWS CloudFormation templates
  + A multi\-AMI listing can have up to 20 AWS CloudFormation templates
+ The estimated infrastructure price for the default configuration of each template
+ A topology diagram and topology metadata
+ Completed product form \(available from the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/)\)
  + For single\-AMI products, use the [Commercial Product](https://s3.amazonaws.com/awsmp-loadforms/ProductDataLoad-Current.xlsx) form
  + For multi\-AMI products, use the [Multi\-AMI Product form](https://s3.amazonaws.com/awsmp-loadforms/AWS_Marketplace_Product_Load_Form_CAR_Multi_AMI.xlsx) form

The product forms include example submissions for your reference\.

For each listing, most of the required product data and metadata are the same as for traditional single\-AMI products\. Therefore, each AMI that is delivered by using an AWS CloudFormation template must continue to meet the standards and requirements described for AWS Marketplace\.

For each AWS CloudFormation template you must also provide the following information\.


|  **Field**  |  **Description**  |  **Restrictions**  | 
| --- | --- | --- | 
|  Title  |  Title of the topology\. This appears on the detail and fulfillment pages and the pop\-up that shows the topology details\.  |  50 characters  | 
|  Short description  |  This appears on the detail and fulfillment pages\.  |  200 characters  | 
|  Long description  |  This appears in the topology details pop\-up\.  |  2000 characters  | 

For multi\-AMI listings, the following fields are required:
+ Solution title
+ Solution short description
+ Solution long description
+ For AWS CloudFormation templates \(up to 20 per solution\)
  + Deployment title \(per template\)
  + Short description \(per template\)
  + Long description \(per template\)
  + Architecture diagram \(per template\)
  + Infrastructure pricing estimate \(per template\)
  + List of software products/components contained in this AWS CloudFormation template
  + List of regions supported by this AWS CloudFormation template

## Submitting Your Listing<a name="submitting-your-listing"></a>

Use the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/) to submit your listing\. On the **File Upload** tab, attach your file and choose **Upload**\. After we receive your template and metadata, we start the processing of your listing\. Allow three to five weeks for the following:
+ Review of the AWS CloudFormation template, AMI, and metadata for the AMI and AWS CloudFormation template
+ Publication of your AWS CloudFormation template to AWS Marketplace listings

## Frequently Asked Questions<a name="cft-frequently-asked-questions"></a>

### Which scenarios are addressed by multi\-AMI listings?<a name="cft-faq-question-01"></a>

 You can list solutions that include multiple distinct AMIs in a single listing that customers purchase with a single subscription\. This includes deployments with multiple images configured in different ways\. The type of solution falls into two categories: 

 **Multi\-component products** – For example, a software product that requires a front\-end web server and a middle\-tier application server can be offered as a single combined solution\. Another example is a product that has one server functioning as a controller, with other servers running as a clustered set of workers\. 

 **Multi\-product solutions** – For example, a new solution that combines two or more products to deliver a better\-together experience\. In this case, these solutions are distinct from any existing AWS Marketplace products that you already offer, even if those software products are the same or similar\. 

### Which scenarios aren't addressed by multi\-AMI listings?<a name="cft-faq-question-02"></a>

 Multi\-AMI listings don't allow buyers to combine existing AWS Marketplace product listings into a bundle\. Buyers subscribe to a single new offering rather than combining separate listings in AWS Marketplace\. Similarly, the price you set for each component of a solution has no connection to, or dependency on, other AWS Marketplace product listings\. Buyers can't customize the solution by choosing only a subset of AMIs thatthey want to subscribe to\. However, you can offer different AWS CloudFormation templates for the solution that deploy different combinations or subsets of the AMIs included\. 

### Is there any dependency between my single\-AMI and multi\-AMI products?<a name="cft-faq-question-03"></a>

 No\. Individual software products and multi\-AMI solutions that include the same software offerings are separate listings\. If you update a product listing, it has no effect on any multi\-AMI solution listing\. 

### Are there any limitations on where I can offer or deploy these solutions?<a name="cft-faq-question-04"></a>

 You can offer or deploy multi\-AMI solutions in all AWS regions where AWS Marketplace is available\. However, some solutions that you offer might not be available in certain regions if they reference AWS resources that are not available in those regions\. 

### How do customers discover multi\-AMI solution listings?<a name="cft-faq-question-05"></a>

 Customers discover solutions through the AWS Marketplace website\. Multi\-AMI solutions are listed the same way single\-AMI products are listed today\. Searching or browsing for software by name, keyword, category, or vendor shows multi\-AMI solutions alongside other AWS Marketplace listings\. Solutions are also included in search results filtered by **CloudFormation Stack** under **Delivery Method**\. 

### Will my seller reports change if I use AWS CloudFormation templates?<a name="cft-faq-question-06"></a>

 Multi\-AMI solutions are reported on the existing reports\. Each AMI in a solution appears as its own line item on the daily usage reports\. Each solution appears as a single line item on the revenue reports\. Disbursement reports are unchanged\. 

### Are single\-AMI and multi\-AMI AWS CloudFormation templates supported in the AWS GovCloud \(US\) region?<a name="cft-faq-question-07"></a>

 Yes\. The PDT region does support single\-AMI and multi\-AMI CloudFormation templates\. The configuration of the end\-points in the template needs to be directed to the PDT region\. Additionally, both the ISV and purchasing customer must have a AWS GovCloud \(US\) account\. 

### What's the process to enable my templates for the AWS GovCloud \(US\)?<a name="cft-faq-question-08"></a>
+ Provide the AWS Marketplace operations team your AWS GovCloud \(US\) account ID\.
+ Submit an updated CFT that has a space for the GovCloud AMI in the Mappings section\.
+ The AWS Marketplace operations team will clone your latest us\-east\-1 region AMI to the AWS GovCloud \(US\) region, insert the AMI into an AWS CloudFormation template and test\.

 Once the test are successful, the AWS Marketplace operations team will finish publishing\. 