# Integrating the AWS SDK Java and RegisterUsage<a name="aws-sdk-java-registerusage-integration"></a>

 The following steps outline an example implementation using the AWS SDK for Java to integrate with the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html)\. For the full source code, see [Java Integration Example](java-integration-example.md)\. Many of these steps apply regardless of the language\. 

**Example steps for `RegisterUsage` integration**

1.  From the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour), choose **Containers** to start creating a new container product\. Creating the product generates the product code for the product to integrate with your container image\. For more information about publishing, see [Publishing Container Products](publishing-container-products.md)\. For information about setting IAM permissions, see [AWS Marketplace Metering and Entitlement Service APIs Permissions](iam-user-policy-for-aws-marketplace-actions.md)\.

1.  Download the public [AWS Java SDK](https://aws.amazon.com/sdk-for-java/)\. 
**Important**  
 To call `RegisterUsage` from Amazon EKS, you must you must [use a supported AWS SDK](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts-minimum-sdk.html) and run on an Amazon EKS cluster running Kubernetes 1\.13 or later\. 

1.  \(Optional\) If you want to perform digital signature verification, you need to configure the [BouncyCastle](https://mvnrepository.com/artifact/org.bouncycastle/bcprov-jdk15on) signature verification library in your application classpath\. If you want to use JSON Web Token \(JWT\), you must also include [JWT Java](https://jwt.io/) libraries in your application classpath\. Using JWT provides a simpler approach to signature verification but is not required, and you can use standalone BouncyCastle instead\. Whether you use JWT or BouncyCastle, you need to use a build system such as Maven to include transitive dependencies of BouncyCastle or JWT in your application classpath\. 

   ```
   // Required for signature verification using code sample
   <dependency>
       <groupId>org.bouncycastle</groupId>
       <artifactId>bcpkix-jdk15on</artifactId>
       <version>1.60</version>
   </dependency>
   
   // This one is only required for JWT
   <dependency>
       <groupId>com.nimbusds</groupId>
       <artifactId>nimbus-jose-jwt</artifactId>
       <version>6.0</version>
   </dependency>
   ```

1.  Call `RegisterUsage` from each *paid* container image in your product offering\. `ProductCode` and `PublicKeyVersion` are required parameters, and all other inputs are optional\. The following is an example payload for `RegisterUsage`\. 

   ```
   {
       "ProductCode" : "string", // (required)
       "PublicKeyVersion": 1,    // (required)
       "Nonce": "string",        // (optional) to scope down the registration
                                 //            to a specific running software
                                 //            instance and guard against
                                 //            replay attacks
   }
   ```

1.  `RegisterUsage` generates an RSA\-PSS digital signature using SHA\-256 that you can use to verify request authenticity\. The signature includes the following fields: `ProductCode`, `PublicKeyVersion`, and `Nonce`\. To verify the digital signature, you must retain these fields from the request\. The following code is an example response to a `RegisterUsage` call\. 

   ```
   {
   "Signature": "<<JWT Token>>"
   }
   
   // Where the JWT Token is composed of 3 dot-separated, 
   // base-64 URL Encoded sections.
   // e.g. eyJhbGcVCJ9.eyJzdWIMzkwMjJ9.rrO9Qw0SXRWTe
   
   // Section 1: Header/Algorithm
   {
   "alg": "PS256",
   "typ": "JWT"
   }
   
   // Section 2: Payload
   {
   "ProductCode" : "string",
   "PublicKeyVersion": 1,
   "Nonce": "string",
   "iat": date // JWT issued at claim 
   }
   
   // Section 3: RSA-PSS SHA256 signature
   "rrO9Q4FEi3gweH3X4lrt2okf5zwIatUUwERlw016wTy_21Nv8S..."
   ```

1.  Rebuild a new version of your Docker container image that includes the `RegisterUsage` call, tag the container, and push it to any Docker registry that is compatible with Amazon ECS or Amazon EKS, such as Amazon ECR or Docker Hub\. If you are using Amazon ECR, ensure that the account launching the Amazon ECS task or Amazon EKS pod has permissions on the Amazon ECR repository\. Otherwise, execution fails\.
**Note**  
 If you use a private Docker Hub repository, follow the steps in [Private Registry Authentication for Tasks](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/private-auth.html) in the *Amazon Elastic Container Service Developer Guide*\. 

1.  Create an [IAM](https://aws.amazon.com/iam/) role that grants permission for your container to call `RegisterUsage`, as defined in the following code\. You must supply this IAM role in the [Task Role](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definition_parameters.html#task_role_arn) parameter of the Amazon ECS task or Amazon EKS pod definition\.

   ```
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Action": [
                   "aws-marketplace:RegisterUsage"
                   ],
                   "Effect": "Allow",
                   "Resource": "*"
           }
       ]
   }
   ```

1.  Create an Amazon ECS task or Amazon EKS pod definition that references the container that has integrated with AWS Marketplace and references the IAM role that you created in step 7\. You should enable AWS CloudTrail logging in the task definition if you want to see logging\. 

1.  Create an Amazon ECS or Amazon EKS cluster to execute your task or pod\. For more information about creating an Amazon ECS cluster, see [Creating a Cluster](https://docs.aws.amazon.com/AmazonECS/latest/userguide/create_cluster.html) in the *Amazon Elastic Container Service Developer Guide*\. For more information about creating an Amazon EKS cluster, see [Creating an Amazon EKS Cluster](https://docs.aws.amazon.com/eks/latest/userguide/create_cluster.html)\.
**Note**  
 You must use Kubernetes version 1\.1\.3\.x or later\. 

1.  Configure the Amazon ECS or Amazon EKS cluster and launch the Amazon ECS task definition or Amazon EKS pod that you created in step 8, in the us\-east\-1 Region\. 

1.  When you get a valid response back from `RegisterUsage`, you can begin creating your container product\. For more information, see [Publishing Container Products](publishing-container-products.md)\. For other questions, contact the [AWS Marketplace Seller Operations](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

## Preview Mode<a name="preview-mode"></a>

 You can't fully test the integration until your product is published with all the required metadata and pricing information\. However, `RegisterUsage` provides a preview mode for paid container products that aren't publicly available on AWS Marketplace\. Using `RegisterUsage` in preview mode enables you to integrate safely without having a fully published product\. If requested, AWS Marketplace catalog operations can verify receipt of your metering records in preview mode\. Using this approach helps to ensure the container images you submit will successfully integrate with `RegisterUsage`\. Preview mode operates identically to production mode, except preview mode does not perform verification of a customer subscription\. That is, it does not verify entitlement to use your product\. 