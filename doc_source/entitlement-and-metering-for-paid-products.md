# AWS Marketplace Metering Service integration<a name="entitlement-and-metering-for-paid-products"></a>

You use the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) for both checking entitlement to use your product and metering usage for billing\. If you want to define your own pricing units and meter that usage to us for billing, integrate with [MeterUsage](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_MeterUsage.html)\. If you want to price your product based on number of tasks or pods used and have us meter that usage automatically, integrate with the [RegisterUsage](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_RegisterUsage.html) action\. For both types of pricing, you can add a long term contract price without changing how you integrate with the AWS Marketplace Metering Service\.

When you create a new container product in AWS Marketplace Management Portal, we provide a set of product identifiers \(the product code and public key\) that are used to integrate your product with the AWS Marketplace Metering service\.

## Entitlement<a name="seller-container-entitlement"></a>

Integrating with the AWS Marketplace Metering Service allows you to verify that the customer running your paid software is subscribed to your product on AWS Marketplace, guarding you against unauthorized use at container startup\. You call the [MeterUsage](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_MeterUsage.html) or [RegisterUsage](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_RegisterUsage.html) action, depending on your pricing model, to verify entitlement\. For hourly and fixed monthly pricing models, use the `RegisterUsage` action\. For custom metering pricing models, use the `MeterUsage` action\.

If a buyer is not entitled to your product, either one of these API actions will return the `CustomerNotEntitledException` exception\.

**Note**  
If a buyer unsubscribes from your product while running it, they are entitled to continue running it\. However, they can't launch additional containers for your product\.

## Integration guidelines<a name="integration-guidelines"></a>

Keep the following guidelines in mind as you create and publish your container products and plan to use the AWS Marketplace Metering Service `MeterUsage` or `RegisterUsage` actions for entitlement and metering\.
+ Do not configure AWS credentials within your software or the Docker container image\. AWS credentials for the buyer are automatically obtained at runtime when your container image is running within an Amazon ECS task or Amazon EKS pod\.
+  To call `MeterUsage` or `RegisterUsage` from Amazon EKS, you must [use a supported AWS SDK](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts-minimum-sdk.html)\. To test `MeterUsage` or `RegisterUsage` integration of Amazon EKS, you must run an Amazon EKS cluster running Kubernetes 1\.13\.x or greater\. Kubernetes 1\.13 is required for IAM roles for pod support, which is a dependency for the running pod to obtain the AWS credentials required to invoke these actions on Amazon EKS\. 
+ You can do local development, but you will get a `PlatformNotSupportedException` exception\. This exception won't occur when you launch the container on AWS container services \(Amazon ECS, Amazon EKS, and Fargate\)

## Supported AWS Regions<a name="supported-regions-metering"></a>

For a list of all AWS Marketplace supported AWS Regions, see [Region Table](http://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) on the **Global Infrastructure** page\.

### Obtaining the AWS Region for metering<a name="metering-aws-region-configuration"></a>

When integrating your container with either `MeterUsage` or `RegisterUsage` for metering, don't configure the AWS SDK to use a specific AWS Region\. The AWS Region must be obtained dynamically at runtime\. For example, if a customer launches an Amazon ECS task or Amazon EKS pod, and `RegisterUsage` is called in an AWS Region that differs from that of where the Amazon ECS task or Amazon EKS pod was launched, `RegisterUsage` will throw `InvalidRegionException`\.

AWS SDK languages do not determine the `AWS_REGION` in a consistent manner\. For example, the AWS SDK for Java automatically uses [Amazon EC2 instance metadata](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html) \(specifically, `ec2InstanceMetadata`\) to obtain the AWS Region when environment variables or other configuration are not present\. In this instance, only call `ec2InstanceMetadata` if the `AWS_REGION` environment variable isn’t present\.

For information on how to dynamically obtain an AWS Region at runtime, refer to the [AWS SDK Developer Guide](http://aws.amazon.com/tools) for your programming language\.

## Preventing metering modification<a name="prevent-metering-modification"></a>

Introducing ways for buyers to modify or override calls to `RegisterUsage` or `MeterUsage` might result in undesirable billing and payment issues\. We strongly recommend that you Integrate the metering and entitlement logic\.

Keep the following in mind when engineering your product to prevent metering modification:
+ If buyers can insert new image layers that contain CMD or ENTRYPOINT instructions, directly integrate `RegisterUsage` or `MeterUsage` into the software the buyer is running through your container image\. Otherwise, calls to `RegisterUsage` or `MeterUsage` executed via CMD or ENTRYPOINT from the base image will likely be overridden by the buyer\.
+ We recommend that you manage the AWS Marketplace product codes your software uses as input to `RegisterUsage` or `MeterUsage` in a manner buyers can't modify\. However, if your product manages product codes in manner customers can override, such as AWS CloudFormation, Helm chart, or Kubernetes manifest, you must maintain a list of *trusted* AWS Marketplace product codes to ensure the one your software passes as input to `RegisterUsage` or `MeterUsage` is valid\.
+  If any of your trusted product codes are for free products, ensure that they can’t be used in place of a paid product code\.