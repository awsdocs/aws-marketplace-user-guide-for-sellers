# Integrating Paid Container Software<a name="integrating-your-paid-container-software"></a>

## Integration Prerequisites<a name="integration-prerequisites"></a>

 You must complete the following prerequisite steps before you begin\. 
+  You have registered as a seller on AWS Marketplace\. 
+  You have obtained an AWS Marketplace product code and public key\. The product code is used to *register* your software with AWS Marketplace, and the public key can be used if you choose to perform digital signature verification\. 

## RegisterUsage Guidelines<a name="registerusage-guidelines"></a>

 Keep the following guidelines in mind as you create and publish your container products\. 
+  If `RegisterUsage` is not **directly integrated** into the software the customer is running via your container image, and you anticipate customers inserting new image layers that contain CMD or ENTRYPOINT instructions, calls to `RegisterUsage` executed via CMD or ENTRYPOINT from the base image will likely be **overridden** by the customer\. Alternatives to `RegisterUsage` include fixed monthly pricing or modifying the underlying software so that `RegisterUsage` is directly integrated \(assuming you have the rights to do so\)\. 
+  Do not configure AWS credentials within your software or the Docker container image, unless you are testing locally\. AWS credentials are automatically obtained at runtime when your container image is running within an Amazon ECS task or Amazon EKS pod\. 
+  You can use the `RegisterUsage` API to test your integration before submitting your image to AWS Marketplace for publication to the catalog\. To call the API, you use the product code you received when you created your product\.
**Important**  
 When you launch the container, you must use an account with the IAM policy applied that specifically provides permission to use the `RegisterUsage` API\. For a list of IAM managed policies for AWS Marketplace, see [AWS Marketplace Metering and Entitlement Service APIs Permissions](iam-user-policy-for-aws-marketplace-actions.md)\. 
+  Ensure that you launch at least one Amazon ECS task or Amazon EKS pod containing your paid container in the us\-east\-1 Region\. This allows AWS Marketplace product publishing to validate your `RegisterUsage` integration\. If your product supports both Amazon ECS and Amazon EKS, you only need to launch in Amazon EKS for us to validate your integration\. 
+  You can do local development, but you will receive `PlatformNotSupportedException`\. Receiving `PlatformNotSupportedException` is an indication that when you launch the container on Amazon ECS or Amazon EKS, it will function as expected\. 
+  To call `RegisterUsage` from Amazon EKS, you must [use a supported AWS SDK](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts-minimum-sdk.html)\. To test `RegisterUsage` integration of Amazon EKS, you must run an Amazon EKS cluster running Kubernetes 1\.13\.x or greater\. Kubernetes 1\.13 is required for IAM roles for pod support, which is a dependency for the running pod to obtain the AWS credentials required to invoke `RegisterUsage` on Amazon EKS\. 
+  All AWS Regions except for Asia Pacific \(Hong Kong\), Middle East \(Bahrain\), China \(Beijing\), and China \(Ningxia\) are supported\. 
+  AWS GovCloud \(US\-East\) Region and AWS GovCloud \(US\-West\) Region regions are not supported\.

## Managing AWS Marketplace Product Codes<a name="aws-marketplace-product-code-management"></a>

 Best practice is to manage the AWS Marketplace product codes your software uses as input to `RegisterUsage` in a manner customers cannot tamper with\. However, if your product manages product codes in manner customers can override, such as AWS CloudFormation, Helm chart, or Kubernetes manifest, you must maintain a list of *trusted* AWS Marketplace product codes to ensure the AWS Marketplace product code your software passes as input to `RegisterUsage` is valid\. Also, if any of the trusted product codes are for free products, you must ensure they can’t be used in place of a paid product code\. 

## Obtaining the AWS Region for RegisterUsage<a name="registerusage-aws-region-configuration"></a>

 Do **not** configure the AWS SDK to use a specific AWS Region\. The Region must be obtained dynamically at runtime\. For example, if a customer launches an Amazon ECS task or Amazon EKS pod, and `RegisterUsage` is called in an AWS Region that differs from that of where the Amazon ECS task or Amazon EKS pod was launched, `RegisterUsage` will throw `InvalidRegionException`\.

That said, AWS SDK languages do not determine the `AWS_REGION` in a consistent manner\. For example, the AWS SDK for Java automatically uses [Amazon EC2 instance metadata](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html) \(specifically, `ec2InstanceMetadata`\) to obtain the AWS Region when environment variables or other configuration are not present\. However, other AWS SDK languages do not automatically default to using `ec2InstanceMetadata` if environment variables or other AWS SDK configuration isn't present\. You should also only make a call to `ec2InstanceMetadata` if the `AWS_REGION` environment variable isn’t present\.

**Important**  
If you are using a language other than the AWS SDK for Java, you must update your `RegisterUsage` implementation to obtain the Region dynamically via `ec2InstanceMetadata`\. Otherwise, your task is likely to fail\.