# Container product billing, metering, and licensing integrations<a name="container-products-billing-integration"></a>

AWS Marketplace integrates with other AWS services to provide both metering and contract\-based pricing for your container product\.

## Hourly and custom metering with AWS Marketplace Metering Service<a name="entitlement-and-metering-for-paid-products"></a>

To both check entitlement to use your product and to meter usage for billing, use the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html)\. If you want to define your own pricing units and meter that usage to us for billing, integrate by using the [MeterUsage](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_MeterUsage.html) API operation\. If you want to price your product based on number of tasks or pods used and have AWS meter that usage automatically, integrate by using the [RegisterUsage](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_RegisterUsage.html) API operation\. For both types of pricing, you can add a long\-term contract price without changing how you integrate with the AWS Marketplace Metering Service\.

When you create a new container product in the AWS Marketplace Management Portal, we provide a set of product identifiers \(the product code and public key\) that are used to integrate your product with the AWS Marketplace Metering Service\.

### Entitlement<a name="seller-container-entitlement"></a>

Integrating with the AWS Marketplace Metering Service allows you to verify that the customer running your paid software is subscribed to your product on AWS Marketplace, guarding you against unauthorized use at container startup\. To verify entitlement, use the [MeterUsage](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_MeterUsage.html) or [RegisterUsage](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_RegisterUsage.html) API operations, depending on your pricing model\. For hourly and fixed monthly pricing models, use the `RegisterUsage` API operation\. For custom metering pricing models, use the `MeterUsage` API operation\.

If a buyer isn't entitled to your product, these API operations return the `CustomerNotEntitledException` exception\.

**Note**  
If a buyer unsubscribes from your product while running it, they are entitled to continue running it\. However, they can't launch additional containers for your product\.

### Integration guidelines<a name="integration-guidelines"></a>

As you create and publish your container products and use the `MeterUsage` or `RegisterUsage` API operations for entitlement and metering, keep the following guidelines in mind:
+ Don't configure AWS credentials within your software or the Docker container image\. AWS credentials for the buyer are automatically obtained at runtime when your container image is running within an Amazon ECS task or Amazon EKS pod\.
+  To call the `MeterUsage` or `RegisterUsage` API operations from Amazon EKS, you must [use a supported AWS SDK](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts-minimum-sdk.html)\. To test `MeterUsage` or `RegisterUsage` integration of Amazon EKS, you must run an Amazon EKS cluster running Kubernetes 1\.13\.x or greater\. Kubernetes 1\.13 is required for AWS Identity and Access Management \(IAM\) roles for pod support\. IAM roles are required for the running pod to obtain the AWS credentials required to invoke these actions on Amazon EKS\. 
+ You can do local development, but you will get a `PlatformNotSupportedException` exception\. This exception won't occur when you launch the container on AWS container services \(Amazon ECS, Amazon EKS, and Fargate\)\.

### Supported AWS Regions<a name="supported-regions-metering"></a>

For a list of all AWS Marketplace supported AWS Regions, see [Region Table](http://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) on the Global Infrastructure website\.

#### Obtaining the AWS Region for metering<a name="metering-aws-region-configuration"></a>

When integrating your container for metering with either the `MeterUsage` or `RegisterUsage` API operation, don't configure the AWS SDK to use a specific AWS Region\. The Region must be obtained dynamically at runtime\. 

**Example**  
For example, a customer launches an Amazon ECS task or Amazon EKS pod\. The `RegisterUsage` API operation is called in a Region that differs from the Region where the Amazon ECS task or Amazon EKS pod was launched\. Therefore, the `RegisterUsage` API operation throws an `InvalidRegionException` error\.



AWS SDK languages don't determine the `AWS_REGION` in a consistent manner\. If your SDK does not automatically pick up the `AWS_REGION`, software needs to be written manually to determine the `AWS_Region`\. For example, the AWS SDK for Java automatically uses [Amazon EC2 instance metadata](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html) \(specifically, `ec2InstanceMetadata`\) to obtain the Region when environment variables or other configuration aren't present\. In this instance, only call `ec2InstanceMetadata` if the `AWS_REGION` environment variable isn’t present\.

For information about how to dynamically obtain an AWS Region at runtime, refer to the [AWS SDK Developer Guide](http://aws.amazon.com/tools) for your programming language\.

### Preventing metering modification<a name="prevent-metering-modification"></a>

Introducing ways for buyers to modify or override calls to `RegisterUsage` or `MeterUsage` might result in undesirable billing and payment issues\. We strongly recommend that you integrate the metering and entitlement logic\.

When engineering your product to prevent metering modification, keep the following in mind:
+ If buyers can insert new image layers that contain `CMD` or `ENTRYPOINT` instructions, directly integrate `RegisterUsage` or `MeterUsage` into the software that the buyer is running through your container image\. Otherwise, calls to `RegisterUsage` or `MeterUsage` executed via `CMD` or `ENTRYPOINT` from the base image will likely be overridden by the buyer\.
+ We recommend that you manage the AWS Marketplace product codes that your software uses as input to `RegisterUsage` or `MeterUsage` in a manner buyers can't modify\. However, if your product manages product codes in a manner customers can override, such as AWS CloudFormation, Helm chart, or Kubernetes manifest, you must maintain a list of *trusted* AWS Marketplace product codes\. This is to ensure that the product code your software passes as input to `RegisterUsage` or `MeterUsage` is valid\.
+  If any of your trusted product codes are for free products, ensure that they can’t be used in place of a paid product code\.

## Contract pricing with AWS License Manager<a name="container-products-contracts-license-manager"></a>

For container\-based products with contract pricing, you use AWS License Manager to associate licenses with your product\. 

AWS License Manager is a license management tool that enables your application to track and update licenses \(also known as entitlements\) that have been purchased by a customer\. This section provides information about how to integrate your product with AWS License Manager\. After the integration is complete, you can publish your product listing on AWS Marketplace\.

For more information about AWS License Manager, see the [AWS License Manager User Guide](https://docs.aws.amazon.com/license-manager/latest/userguide/license-manager.html) and the [AWS License Manager](https://docs.aws.amazon.com/cli/latest/reference/license-manager/index.html) section of the *AWS CLI Command Reference*\.

**Note**  
Customers can't launch new instances of the container after the contract expiry period\. However, during the contract duration, they can launch any number of instances\. These licenses are not bound to a specific node or instance\. Any software running on any container on any node can checkout the license as long as it has the assigned AWS credentials\.
**Private Offer Creation** – Sellers can generate private offers for the products using the Private offer creation tool in the AWS Marketplace Management Portal\.
**Reporting** – You can set up data feeds by setting up an Amazon S3 bucket in the **Report** section in the AWS Marketplace Management Portal\. For more information, see [Seller reports and data feeds](reports-and-data-feed.md)\.

### Integration workflow<a name="container-LM-LM-workflow"></a>

The following steps show the workflow for integrating your container product with AWS License Manager:

1. Seller creates a product with AWS License Manager integration\.

1. Seller lists the product on AWS Marketplace\.

1. Buyer finds the product on AWS Marketplace and purchases it\.

1. A license is sent to the buyer in their AWS account\.

1. Buyer uses the software by launching the Amazon EC2 instance, Amazon ECS task, or Amazon EKS pod software\. The customer deploys using an IAM role\.

1. Software reads the license in the buyer's AWS License Manager account, discovers the entitlements purchased, and provisions the features accordingly\. 
**Note**  
License Manager doesn't do any tracking or updates; this is done by the seller’s application\.