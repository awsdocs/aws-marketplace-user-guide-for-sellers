# Integrating the AWS SDK Java and RegisterUsage<a name="aws-sdk-java-registerusage-integration"></a>

 The following steps outline an example implementation using the AWS SDK for Java to integrate with the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html)\. For the full source code, see [Java Integration Example](java-integration-example.md)\. Many of these steps apply regardless of the language\. 

1.  To create a new container product, email awsmp\-containers@amazon\.com\. You’ll receive an email with detailed instructions on the steps to take to register your product with AWS Marketplace\. 

1.  Download the public [AWS Java SDK](https://aws.amazon.com/sdk-for-java/)\. 

1.  Access the S3 bucket included in the email that you received from AWS Marketplace\. Download the AWS Marketplace Metering Service \.jar file from the S3 bucket and ensure that it's in your application classpath\. This gives you access to the `RegisterUsage` operation on the AWS Marketplace Metering Service\. All publicly accessible AWS SDKs have a version of the AWS Marketplace Metering Service that includes `RegisterUsage`\. 

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

1.  Rebuild a new version of your Docker container image that includes the `RegisterUsage` call, tag the container, and push it to any docker registry that is compatible with Amazon ECS, such as Amazon ECR or Docker Hub\. If you are using Amazon ECR, ensure that the account launching the Amazon ECS task has permissions on the Amazon ECR repository, or Amazon ECS task execution will fail\.
**Note**  
 If you use a private Docker Hub repository, follow the steps in [Private Registry Authentication for Tasks](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/private-auth.html) in the *Amazon Elastic Container Service Developer Guide*\. 

1.  Create an [IAM](https://aws.amazon.com/iam/) role that grants permission for your container to call `RegisterUsage`, as defined in the following code\. You must supply this IAM role in the [Task Role](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definition_parameters.html#task_role_arn) parameter of the Amazon ECS task definition\. 

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

1.  Create an Amazon ECS task definition that references the container that has integrated with AWS Marketplace and references the IAM role that you created in step \#7\. You should enable AWS CloudTrail logging in the task definition if you want to see logging\. 

1.  Create an Amazon ECS cluster to execute your task\. For more information, see [Creating a Cluster](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/create_cluster.html) in the *Amazon Elastic Container Service Developer Guide*\. 

1.  Configure the Amazon ECS cluster and launch the Amazon ECS task definition that you created in step \#9, in the us\-east\-1 Region\. 

1.  If you get a valid response back from `RegisterUsage`, email awsmp\-containers@amazon\.com and include the Amazon ECS `task-id` and `product-code`\. AWS Marketplace can verify that we have successfully received your call and are metering software usage\. 

## Preview Mode<a name="preview-mode"></a>

 You will not be able to fully test the integration until your product has been published with all the necessary metadata and pricing information\. However, `RegisterUsage` also supports a preview mode for paid container products that aren't yet fully onboarded to AWS Marketplace, allowing sellers to integrate safely with `RegisterUsage` without having a fully published product\. AWS Marketplace catalog operations can also verify receipt of your metering records under preview mode to ensure the container images you submit during product publishing can successfully integrate with `RegisterUsage`\. The functionality of preview mode and a fully onboarded product is identical except for the following: 
+  `RegisterUsage` returns a valid response for up to 30 minutes after the first successful call\. The response also contains a shortened `TimeToLiveInMillis` of 12 minutes\. After 30 minutes, you will get `CustomerNotEntitledException` and can take appropriate action, exactly as if a customer weren't entitled to use your product during production usage\. 
+  Preview mode will *not* perform verification of customer subscription \(that is, entitlement\)\. 