# Preparing your product<a name="product-preparation"></a>

Preparing to publish a product on AWS Marketplace includes configuring your package, setting a pricing scheme, determining what categories your product shows under, and adding keywords so your product appears in relevant searches\. 

The following list describes the ways you can deliver products, how AWS Marketplace buyers find each type of deliverable, and links to procedures for creating each type of deliverable\.
+ **Amazon Machine Image \(AMI\)** – You can offer AMI\-based products in the following ways:
  + As a single AMI\.

    Buyers can find these products using the **Amazon Machine Image** delivery method filter\. 

    For more information, see [AMI\-based products](ami-products.md)\.
  + As AMIs delivered using AWS CloudFormation templates\.

    Buyers can find these products using the **CloudFormation** delivery method filter\.

    For more information about delivering AMIs as a AWS CloudFormation template, see [AMI\-based delivery using AWS CloudFormation](cloudformation.md)\. For more information about AWS CloudFormation templates, see [AWS CloudFormation concepts](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-whatis-concepts.html) in the *AWS CloudFormation User Guide*\.
  + As a private image build\. With this method, you offer products in a way that lets buyers install your product on a base gold image that meets their internal standards for operating system configuration\. 

    Buyers can find these products using the **Private Amazon Machine Image** delivery method filter\.

    For more information, see [Private images](private-images.md)\.
+ **Container** – You can deliver products in Docker containers\. Container products consist of fulfillment options, which are a set of container images and deployment templates that go together\.

  Buyers can find these products using the **Container** delivery method filter\.

  For more information, see [Getting started with container products](container-product-getting-started.md)\.
+ **File\-based data sets** – To deliver file\-based data sets, you use AWS Data Exchange, a separate AWS service\.

  Buyers can find these products using the **AWS Data Exchange** delivery method filter\.

  For information about publishing and managing data products and offers through AWS Data Exchange, see [Providing Data Products on AWS Data Exchange](https://docs.aws.amazon.com/data-exchange/latest/userguide/providing-data-sets.html) in the *AWS Data Exchange User Guide*\.
+ **Machine learning algorithms and model packages** – With this method, you use Amazon SageMaker a separate AWS service, to create the algorithm or model package, and then publish it on AWS Marketplace\.

  Buyers can find these products using the **Amazon SageMaker** delivery method filter\. 

  For more information on delivering machine learning algorithms and model packages, see [Putting your algorithms and model packages on the AWS Marketplace](listing-algorithms-and-model-packages-in-aws-marketplace-for-machine-learning.md)\. For information on Amazon SageMaker, see [What is Amazon SageMaker?](https://docs.aws.amazon.com/sagemaker/latest/dg/whatis.html) in the *Amazon SageMaker Developer Guide*\.
+ **Software as a service \(SaaS\)** – You can offer SaaS products with subscription\-based or contract\-based pricing models\.

  Buyers find these products using the **SaaS** delivery method filter\.

  For more information, see [Software as a service \(SaaS\)–based products](saas-products.md)\.

Each delivery method has several options for packaging, pricing, and delivery\. Some methods are not available to you as a seller on AWS Marketplace until you register for the program supporting it\. You can create products with a standard list price and end user license agreement \(EULA\), and you can create private offers for individual customers with custom pricing and EULAs\. If you need to make additional changes to the terms of the contract, you can work with the AWS Marketplace team to create a custom private offer\. 

**Tip**  
To simplify the procurement process, you can use [standardized license terms](standardized-license-terms.md) for both public product listings and private offers\.

**Topics**
+ [Product pricing](pricing.md)
+ [Private offers](private-offers-overview.md)
+ [Standardized license terms](standardized-license-terms.md)
+ [Categories and metadata](categories-and-metadata.md)
+ [Search engine optimization](search-engine-optimization.md)