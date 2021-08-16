# Troubleshooting<a name="ml-troubleshooting"></a>

 This section provides help for some common errors that you might encounter during the publishing process of your machine learning product\. If your issue isn't listed, contact [AWS Marketplace Seller Operations](http://aws.amazon.com/marketplace/management/contact-us/)\. 

**General: I get a 400 error when I add the Amazon Resource Name \(ARN\) of my model package or algorithm in the AWS Marketplace Management Portal**

 If you used the Amazon SageMaker console to create your resource, you must choose **Yes** on the final page of the process for **Publish this model package in AWS Marketplace** or **Yes** for **Publish this algorithm in AWS Marketplace**\. You can't choose **No** and later publish it\. Selecting **Yes** doesn't publish the model package or algorithm\. However, it validates your model package or algorithm resource when it is created, which is necessary for use in AWS Marketplace\.

 If you're using the AWS SDK to [create a model package](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_CreateModelPackage.html#sagemaker-CreateModelPackage-request-CertifyForMarketplace) or [ create an algorithm](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_CreateAlgorithm.html#sagemaker-CreateAlgorithm-request-CertifyForMarketplace), ensure that the parameter `CertifyForMarketplace` is set to `true`\. 

After you re\-create your certified and validated model package or algorithm resource, add the new ARN in the AWS Marketplace Management Portal\. 

**General: I get a 404 error when I add the ARN of my model package or algorithm in the AWS Marketplace Management Portal**

 This error can happen for several reasons: 
+  The ARN might be invalid\. Ensure that you are using the correct ARN\. 
  +  For model packages, the ARNs should look similar to `arn:aws:sagemaker:us-east-2:000123456789:model-package/my-model-package-name`\. 
  +  For algorithms, the ARNs should look similar to `arn:aws:sagemaker:us-east-2:000123456789:algorithm/my-algorithm`\. 
+  The model package or algorithm resource wasn't created in the same AWS account as the seller account\. Ensure that all resources and assets for publishing are in the seller account that you are publishing from\. 
+  The AWS Identity and Access Management \(IAM\) user or role that you use for publishing doesn't have the correct IAM permissions to access the model package or algorithm resource\. Ensure that your IAM user or role has the following permissions: 
  +  For model packages, the action `sagemaker:DescribeModelPackage` on the model package resource must be allowed\. 
  +  For algorithms, the action `sagemaker:DescribeAlgorithm` on the algorithm resource must be allowed\. 

**General: I get a 500 error when I specify the pricing for my algorithm product in the AWS Marketplace Management Portal**

 This error can happen when you attempt to publish an algorithm resource with only a training image and without an accompanying inference image\. Algorithm resources that are published on AWS Marketplace must have both components\. For more information, see [Prepare your product in SageMaker](ml-prepare-your-product-in-sagemaker.md)\. 

**Amazon SageMaker: I get a “Client error: Access denied for registry” failure message when I create a model package or algorithm resource**

This error can happen when the image that is being used to create the model package or algorithm is stored in an [Amazon ECR](http://aws.amazon.com/ecr/) repository that belongs to another AWS account\. Model package or algorithm validation does not support cross\-account images\. Copy the image to an Amazon ECR repository owned by the AWS account that you are using to publish\. Then, proceed with creating the resource using the new image location\. 

**Amazon SageMaker: I get “Not Started” and “Client error: No scan scheduled\.\.\.” failure messages when I create a model package or algorithm resource**

This error can happen when SageMaker fails to start a scan of your Docker container image stored in Amazon ECR\. If this happens, open the [ Amazon ECR console](https://console.aws.amazon.com/ecr/repositories?region=us-east-2), find the repository where your image was uploaded to, choose the image, and then choose **Scan**\. 