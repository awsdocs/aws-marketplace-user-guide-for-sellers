# Preparing your product<a name="product-preparation"></a>

Preparing to publish a product on AWS Marketplace includes configuring your package, setting a pricing scheme, determining the relevant categories in which to list your product, and adding keywords so your product appears in relevant searches\. 

**Topics**
+ [Product delivery](#product-delivery)
+ [Product pricing](pricing.md)
+ [Regions and countries for your AWS Marketplace product](regions-and-countries.md)
+ [Private offers](private-offers-overview.md)
+ [Standardized contracts in AWS Marketplace](standardized-license-terms.md)
+ [Categories and metadata](categories-and-metadata.md)
+ [AMI and container product usage instructions](ami-container-product-usage-instructions.md)
+ [Search engine optimization for products](search-engine-optimization.md)

## Product delivery<a name="product-delivery"></a>

Each product delivery method has several options for packaging, pricing, and delivery\. Some methods aren't available to you as a seller on AWS Marketplace until you register for the program supporting it\. 

You can create products with a standard list price and end user license agreement \(EULA\)\. You can also create private offers for individual customers with custom pricing and EULAs\. If you need to make additional changes to the terms of the contract, you can work with the AWS Marketplace team to create a custom private offer\. 

**Tip**  
To simplify the procurement process, you can use [standardized license terms](standardized-license-terms.md) for both public product listings and private offers\.

The following table lists the methods that you can use to deliver software products and how AWS Marketplace buyers ﬁnd each type of deliverable in the AWS Marketplace console\.


**Product delivery methods**  

| Product delivery method | Delivery Method ﬁlter on the console | Description | 
| --- | --- | --- | 
| Single AMI | Amazon Machine Image \(AMI\) |  You deliver a single custom Amazon Machine Image \(AMI\) for your product\. The AMI provides the information required to launch an Amazon Elastic Compute Cloud \(Amazon EC2\) instance\. Buyers can use the single AMI to create Amazon EC2 instances with your product already installed and ready to use\. For more information, see [AMI\-based products](ami-products.md)\.  | 
| AMI delivered using AWS CloudFormation templates | CloudFormation Template |  You can list AMI\-based products that are delivered to AWS Marketplace buyers by using CloudFormation templates\. Buyers can purchase a single solution that entitles them to all of the AMIs in that product\. For more information about delivering AMIs as an CloudFormation template, see [AMI\-based delivery using AWS CloudFormation](https://docs.aws.amazon.com/marketplace/latest/userguide/cloudformation.html)\.  For more information about CloudFormation templates, see [AWS CloudFormation concepts](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-whatis-concepts.html) in the *AWS CloudFormation User Guide*\.  | 
| Private image build | Private Image Build |  You oﬀer products in a way that lets buyers install your product on a base gold image that meets their internal standards for operating system conﬁguration\. For more information, see [Private images](private-images.md)\.  | 
| Container\-based product or application | Container |  You deliver products packaged in container images\. Container products consist of options, which are a set of container images and deployment templates that work together\. For more information, see [Container\-based products](container-based-products.md)\.  | 
| Data products | AWS Data Exchange |  You use AWS Data Exchange to create data products\. For information about publishing and managing data products and oﬀers through AWS Data Exchange, see [Providing data products on AWS Data Exchange](https://docs.aws.amazon.com/data-exchange/latest/userguide/providing-data-sets.html) in the *AWS Data Exchange User Guide*\.  | 
| Machine learning algorithms and model packages | SageMaker Model |  You use Amazon SageMaker to create the algorithm or model package, and then publish it on AWS Marketplace\. For more information about delivering machine learning algorithms and model packages, see [Machine learning products](machine-learning-products.md)\.  For information about SageMaker, see [What is SageMaker?](https://docs.aws.amazon.com/sagemaker/latest/dg/whatis.html) in the *Amazon SageMaker Developer Guide*\.  | 
| Software as a service \(SaaS\) | SaaS |  You can oﬀer SaaS products with subscription\- based, contract\-based, or contract with consumption pricing models\. For more information, see [Software as a service \(SaaS\)–based products](saas-products.md)\.  | 
| Professional services | Professional Services |  You can oﬀer professional services that support or work with other AWS Marketplace products\.  | 