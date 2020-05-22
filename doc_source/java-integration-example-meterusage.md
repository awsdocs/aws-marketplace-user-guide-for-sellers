# Integrating your container product with the AWS Marketplace Metering Service using the AWS SDK for Java<a name="java-integration-example-meterusage"></a>

The following steps outline an example implementation using the AWS SDK for Java to integrate with the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html)'s `MeterUsage` action\. For the full source code, see [MeterUsage Java example](#meterusage-java-example)\. Many of these steps apply regardless of the language\. 

**Example steps for AWS Marketplace Metering Service integration**

1. Sign into the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour)\.

1. From **Assets** choose **Containers** to start creating a new container product\. Creating the product generates the product code for the product to integrate with your container image\. For more information about publishing, see [Publishing container products](container-product-getting-started.md#container-product-publishing)\. For information about setting IAM permissions, see [AWS Marketplace metering and entitlement API permissions](iam-user-policy-for-aws-marketplace-actions.md)\.

1.  Download the public [AWS Java SDK](https://aws.amazon.com/sdk-for-java/)\. 
**Important**  
 To call the metering APIs from Amazon EKS, you must [use a supported AWS SDK](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts-minimum-sdk.html) and run on an Amazon EKS cluster running Kubernetes 1\.13 or later\. 

1. Call `MeterUsage` action from the task or pod once every hour for the each dimension usage\. The API accepts one metering record for a unique combination of `Dimension`, `Resource` and `Hour`\. The resource is either a Amazon ECS task or Amazon EKS pod\.

   ```
   {
       "ProductCode" : "string", // (required)
       "UsageDimension" : "string", // (required)
       "UsageQuantity":  int, // (optional) Default is 0. Acceptable value from [0, 2147483647 (INT_MAX)]
       "Timestamp": Date // (required) Timestamp in UTC. Value can be one hour in the past.
   }
   ```

1. Rebuild a new version of your Docker container image that includes the `MeterUsage` call, tag the container, and push it to any Docker registry that is compatible with Amazon ECS or Amazon EKS, such as Amazon ECR or Docker Hub\. If you are using Amazon ECR, ensure that the account launching the Amazon ECS task or Amazon EKS pod has permissions on the Amazon ECR repository\. Otherwise, execution fails\.
**Note**  
 If you use a private Docker Hub repository, follow the steps in [Private Registry Authentication for Tasks](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/private-auth.html) in the *Amazon Elastic Container Service Developer Guide*\. 

1.  Create an [IAM](https://aws.amazon.com/iam/) role that grants permission for your container to call `MeterUsage`, as defined in the following code\. You must supply this IAM role in the [Task Role](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definition_parameters.html#task_role_arn) parameter of the Amazon ECS task or Amazon EKS pod definition\.

   ```
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Action": [
                   "aws-marketplace:MeterUsage"
                   ],
                   "Effect": "Allow",
                   "Resource": "*"
           }
       ]
   }
   ```

1. Create an Amazon ECS task or Amazon EKS pod definition that references the container that has integrated with AWS Marketplace and references the IAM role that you created in step 7\. You should enable AWS CloudTrail logging in the task definition if you want to see logging\. 

1. Create an Amazon ECS or Amazon EKS cluster to execute your task or pod\. For more information about creating an Amazon ECS cluster, see [Creating a Cluster](https://docs.aws.amazon.com/AmazonECS/latest/userguide/create_cluster.html) in the *Amazon Elastic Container Service Developer Guide*\. For more information about creating an Amazon EKS cluster \(using Kubernetes version 1\.1\.3\.x or later\), see [Creating an Amazon EKS Cluster](https://docs.aws.amazon.com/eks/latest/userguide/create_cluster.html)\.

1. Configure the Amazon ECS or Amazon EKS cluster and launch the Amazon ECS task definition or Amazon EKS pod that you created in step 8, in the us\-east\-1 AWS Region\. It's only during this testing process, before the product is live, that you have to use this region\.

1. When you get a valid response back from `MeterUsage` for each for dimensions being published for the product, you can begin creating your container product\. For questions, contact the [AWS Marketplace Seller Operations](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

## MeterUsage Java example<a name="meterusage-java-example"></a>

The following code sample uses the AWS SDK for Java and AWS Marketplace Metering Service to call the `MeterUsage` operation\.

```
import com.amazonaws.services.marketplacemetering.AWSMarketplaceMetering;
import com.amazonaws.services.marketplacemetering.AWSMarketplaceMeteringClientBuilder;
import com.amazonaws.services.marketplacemetering.model.MeterUsageRequest;
import com.amazonaws.services.marketplacemetering.model.MeterUsageResult;

import java.util.Date;

public class MeterUsage {
    private static final String PRODUCT_CODE = ".......";
    private final AWSMarketplaceMetering awsMarketplaceMetering;

    public MeterUsage() {
        awsMarketplaceMetering = AWSMarketplaceMeteringClientBuilder.standard().build();
    }

    /**
     * Submits metering record for a FCP Dimension. The API accepts 1 metering record per dimension
     * for a given buyer's resource for a given timestamp hour. Ex. If a buyer is running 10 tasks,
     * the API will accepts 1 call to MeterUsage in an hour for a given dimension for each running task.
     *
     * @param dimension - FCP dimension name provided during the publishing of the product.
     * @param quantity - FCP dimension consumption value for the hour.
     * @param timestamp - Timestamp, in UTC, for which the usage is being reported.
     *                  Timestamp cant be more than 1 hour in the past.
     *                  Make sure the timestamp value is not before the start of the software usage.
     */
    public void callMeterUsage(String dimension, int quantity, Date timestamp) {
        MeterUsageRequest meterUsageRequest = new MeterUsageRequest()
                .withProductCode(PRODUCT_CODE)
                .withUsageDimension(dimension)
                .withUsageQuantity(quantity)
                .withTimestamp(timestamp);
        MeterUsageResult meterUsageResult = awsMarketplaceMetering.meterUsage(meterUsageRequest);
    }
}
```