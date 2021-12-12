# Integrating your container product with the AWS Marketplace Metering Service using the AWS SDK for Java<a name="java-integration-example-meterusage"></a>

The following example outlines an implementation that uses the AWS SDK for Java to integrate with the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) `MeterUsage` operation\. For complete details, see [`MeterUsage` Java examples](#meterusage-java-example)\. Many of the following steps apply regardless of the language\. 

**Example: AWS Marketplace Metering Service integration**

1. Sign in to the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour)\.

1. From **Assets**, choose **Containers** to start creating a new container product\. Creating the product generates the product code for the product to integrate with your container image\. For more information about publishing, see [Publishing container products](container-product-getting-started.md#container-product-publishing)\. For information about setting AWS Identity and Access Management \(IAM\) permissions, see [AWS Marketplace metering and entitlement API permissions](iam-user-policy-for-aws-marketplace-actions.md)\.

1.  Download the public [AWS Java SDK](https://aws.amazon.com/sdk-for-java/)\. 
**Important**  
 To call the metering API operations from Amazon Elastic Kubernetes Service \(Amazon EKS\), you must [use a supported AWS SDK](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts-minimum-sdk.html) and run on an Amazon EKS cluster running Kubernetes 1\.13 or later\. 

1. Call the `MeterUsage` operation from the task or pod once every hour for each dimension usage\. The API operation accepts one metering record for a unique combination of `Dimension`, `Resource`, and `Hour`\. The resource is either an Amazon Elastic Container Service \(Amazon ECS\) task or an Amazon EKS pod\.

   ```
   {
       "ProductCode" : "string", // (required)
       "UsageDimension" : "string", // (required)
       "UsageQuantity":  int, // (optional) Default is 0. Acceptable value from [0, 2147483647 (INT_MAX)]
       "Timestamp": Date, // (required) Timestamp in UTC. Value can be one hour in the past.
       "UsageAllocations": List<UsageAllocation> // (optional) UsageAllocations across 1 or more tags.
   }
   ```
**Note**  
It is possible to see transient issues in connecting to the AWS Marketplace Metering Service\. AWS Marketplace strongly recommends implementing retries for up to 30 minutes, with exponential back off, to avoid short\-term outages or network issues\.

1. Rebuild a new version of your Docker container image that includes the `MeterUsage` call, tag the container, and push it to any Docker registry that is compatible with Amazon ECS or Amazon EKS, such as Amazon Elastic Container Registry \(Amazon ECR\) or Docker Hub\. If you are using Amazon ECR, ensure that the account launching the Amazon ECS task or Amazon EKS pod has permissions on the Amazon ECR repository\. Otherwise, the operation fails\.
**Note**  
 If you use a private Docker Hub repository, follow the steps in [Private registry authentication for tasks](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/private-auth.html) in the *Amazon Elastic Container Service Developer Guide*\. 

1.  Create an [IAM](https://aws.amazon.com/iam/) role that grants permission for your container to call `MeterUsage`, as defined in the following code example\. You must supply this AWS Identity and Access Management \(IAM\) role in the [Task Role](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definition_parameters.html#task_role_arn) parameter of the Amazon ECS task or Amazon EKS pod definition\.

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

1. Create an Amazon ECS task or Amazon EKS pod definition that references the container that has integrated with AWS Marketplace and references the IAM role that you created in step 6\. If you want to see logging, enable AWS CloudTrail logging in the task definition\. 

1. Create an Amazon ECS or Amazon EKS cluster to run your task or pod\. For more information about creating an Amazon ECS cluster, see [Creating a cluster](https://docs.aws.amazon.com/AmazonECS/latest/userguide/create_cluster.html) in the *Amazon Elastic Container Service Developer Guide*\. For more information about creating an Amazon EKS cluster \(using Kubernetes version 1\.1\.3\.x or later\), see [Creating an Amazon EKS Cluster](https://docs.aws.amazon.com/eks/latest/userguide/create_cluster.html)\.

1. Configure the Amazon ECS or Amazon EKS cluster and launch the Amazon ECS task definition or Amazon EKS pod that you created in step 8, in the us\-east\-1 AWS Region\. It's only during this testing process, before the product is live, that you have to use this Region\.

1. When you get a valid response from `MeterUsage` for each of the dimensions being published for the product, you can begin creating your container product\. For questions, contact the [AWS Marketplace Seller Operations](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

## `MeterUsage` Java examples<a name="meterusage-java-example"></a>

The following code examples use the AWS SDK for Java and AWS Marketplace Metering Service to call the `MeterUsage` operation\.

The following code example calls the `MeterUsage` operation without any `UsageAllocations`\.

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

The following code example calls the `MeterUsage` operation with `UsageAllocations`\.

```
private static String callMeterUsageWithAllocationsByTag(AWSMarketplaceMetering marketplaceMetering) {
        // Tag Keys for the product
        String tagKey1 = "Key1";
        String tagKey2 = "Key2";
        String tagKey3 = "Key3";

        // 1st Usage Allocation bucket which has two Tags [{Key1, Key1Value1},{Key2, Key2Value1}]
        List<Tag> tagsForUsageAllocation1 = Arrays.asList(new Tag().withKey(tagKey1).withValue("Key1Value1"),
                new Tag().withKey(tagKey2).withValue("Key2Value1"));
        UsageAllocation usageAllocation1 = new UsageAllocation()
                .withTags(tagsForUsageAllocation1)
                .withAllocatedUsageQuantity(20);

        // 2nd Usage Allocation bucket which has two Tags [{Key1, Key1Value2},{Key2, Key2Value1}]
        List<Tag> tagsForUsageAllocation2 = Arrays.asList(new Tag().withKey(tagKey1).withValue("Key1Value2"),
                new Tag().withKey(tagKey2).withValue("Key2Value1"));
        UsageAllocation usageAllocation2 = new UsageAllocation()
                .withTags(tagsForUsageAllocation2)
                .withAllocatedUsageQuantity(20);

        // 3rd Usage Allocation bucket which has two Tags [{Key1, Key1Value2},{Key2, Key2Value2},{Key3, Key3Value1}]
        List<Tag> tagsForUsageAllocation3 = Arrays.asList(new Tag().withKey(tagKey1).withValue("Key1Value2"),
                new Tag().withKey(tagKey2).withValue("Key2Value2"),
                new Tag().withKey(tagKey3).withValue("Key3Value1"));
        UsageAllocation usageAllocation3 = new UsageAllocation()
                .withTags(tagsForUsageAllocation3)
                .withAllocatedUsageQuantity(15);

        // 4th Usage Allocation bucket with no tags
        UsageAllocation usageAllocation4 = new UsageAllocation()
                .withAllocatedUsageQuantity(15);

        List<UsageAllocation> usageAllocationList = Arrays.asList(usageAllocation1,
                usageAllocation2,
                usageAllocation3,
                usageAllocation4);

        MeterUsageRequest meterUsageRequest = new MeterUsageRequest()
                .withProductCode("TestProductCode")
                .withUsageDimension("Dimension1")
                .withTimestamp(new Date())
                //UsageQuantity value must matach with sum of all AllocatedUsageQuantity
                .withUsageQuantity(70)
                .withUsageAllocations(usageAllocationList);

        MeterUsageResult meterUsageResult;
        try {
            meterUsageResult = marketplaceMetering.meterUsage(meterUsageRequest);
        } catch (Exception e) {
            // Log Error
            throw e;
        }

        return meterUsageResult.getMeteringRecordId();
    }
```