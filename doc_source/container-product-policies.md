# Container\-based product requirements<a name="container-product-policies"></a>

AWS Marketplace maintains the following requirements for all container\-based products and offerings on AWS Marketplace\. These requirements help to promote a safe, secure, and trustworthy catalog for our customers\. We also encourage sellers to review implementation of additional controls and protocols as applicable to meet the needs of their specific products\.

All products and their related metadata are reviewed when submitted to ensure that they meet or exceed current AWS Marketplace requirements\. We review and adjust these policies to meet our evolving security and other usage requirements\. AWS Marketplace continuously verifies that existing products continue to meet any changes to these requirements\. If products fall out of compliance, AWS Marketplace will contact you to update your product\. In some cases, your product might temporarily be unavailable to new subscribers until issues are resolved\.

## Security requirements<a name="container-security-requirements"></a>

 All container\-based products must adhere to the following security requirements:
+ Docker container images must be free from any known malware, viruses, or vulnerabilities\. The self\-service container images ingestion tool can detect vulnerabilities\. To use the container scanning tool, sign into the AWS Marketplace Management Portal, select **Container** from the **Assets** menu, and submit an image for your product\.
+ If your container\-based products requires access to manage AWS resources, it must be achieved through [IAM roles for service accounts](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts.html) \(if run through Amazon Elastic Kubernetes Service \(Amazon EKS\)\) or [IAM roles for tasks](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-iam-roles.html) \(if run through Amazon Elastic Container Service \(Amazon ECS\)\) instead of requesting an access key from users\.
+ Container\-based products must only require least privileges to run\. For more information, see [ECS security](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/security.html) and [EKS security](https://docs.aws.amazon.com/eks/latest/userguide/security.html)\.
+ Container images should be configured to run with non\-root privileges by default\.

## Access requirements<a name="container-accessibility-requirements"></a>

 All container\-based products must adhere to the following access requirements: 
+ Container\-based products must use an initial randomized password\. Container\-based products must not use initial fixed or blank passwords for external administrative access \(for example, to log in to the application via a web interface\)\. The buyer must be prompted for this randomized password before being permitted to set or change their own credentials\.
+ Any outside access to the application must be explicitly agreed to and enabled by customers\.

## Customer information requirements<a name="container-customer-info-requirements"></a>

 All container\-based products must adhere to the following customer information requirements: 
+ Software must not collect or export customer data without the customer's knowledge and express consent except as required by BYOL \(Bring Your Own License\)\. Applications that collect or export customer data must follow these guidelines: 
  + The collection of the customer data must be self\-service, automated, and secure\. Buyers must not need to wait for sellers to approve to deploy the software\. 
  + The requirements for customer data must be clearly stated in the description or the usage instructions of the listing\. This includes what is collected, the location of where the customer data will be stored, and how it will be used\. For example, *This product collects your name and email address\. This information is sent to and stored by the <company name>\. This information will only be used to contact the buyer in regards to the <product name>\.* 
  + Payment information must not be collected\.

## Product usage requirements<a name="container-usage-requirements"></a>

 All container\-based products must adhere to the following product usage requirements: 
+ Sellers can only list fully functioning products\. Beta or prerelease products for trial or evaluation purposes are not allowed\. Developer, community, and BYOL editions of commercial software are supported if the seller provides an equivalent paid version on AWS Marketplace within 90 days of providing the free edition\.
+ All of a container\-based product's usage instructions must include all steps to deploy container\-based products\. Usage instructions must provide commands and deployment resources pointing to the corresponding container images on AWS Marketplace\.
+ Container\-based products must include all container images that a subscriber needs to use the software\. In addition, container\-based products must not require a user to launch the product using any images from outside AWS Marketplace \(for example, container images from third\-party repositories\)\.
+ Containers and their software must be deployable in a self\-service manner and must not require additional payment methods or costs\. Applications that require external dependencies on deployment must follow these guidelines:
  + The requirement must be disclosed in the description or the usage instructions of the listing\. For example, *This product requires an internet connection to deploy properly\. The following packages are downloaded on deployment: <list of package>\.* 
  + Sellers are responsible for the use of and ensuring the availability and security of all external dependencies\. 
  + If the external dependencies are no longer available, the product must be removed from AWS Marketplace as well\. 
  + The external dependencies must not require additional payment methods or costs\.
+ Containers that require an ongoing connection to external resources not under the direct control of the buyer—for example, external APIs or AWS services managed by the seller or a third party—must follow these guidelines:
  + The requirement must be disclosed in the description or the usage instructions of the listing\. For example, *This product requires an ongoing internet connection\. The following ongoing external services are required to properly function: <list of resources>\.* 
  + Sellers are responsible for the use of and ensuring the availability and security of all external resources\.
  + If the external resources are no longer available, the product must be removed from AWS Marketplace as well\.
  + The external resources must not require additional payment methods or costs and the setup of the connection must be automated\.
+ Product software and metadata must not contain language that redirects users to other cloud platforms, additional products, or upsell services that aren't available on AWS Marketplace\.
+ If your product is an add\-on to another ISV’s product, your product description must indicate that it extends the functionality of the other product and that without it, your product has very limited utility\. For example, *This product extends the functionality of <product name> and without it, this product has very limited utility\. Please note that <product name> might require its own license for full functionality with this listing\.*

## Architecture requirements<a name="container-architecture-requirements"></a>

 All container\-based products must adhere to the following architecture requirements: 
+ Source container images for AWS Marketplace must be pushed to the Amazon Elastic Container Registry \(Amazon ECR\) repository owned by AWS Marketplace\. You can create these repositories in the AWS Marketplace Management Portal under server products for each of your container product listings\.
+ Container images must be based on Linux\.
+ Paid container\-based products must be able to be deployed on [Amazon ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html), [Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html), or [AWS Fargate](https://docs.aws.amazon.com/AmazonECS/latest/userguide/what-is-fargate.html)\.