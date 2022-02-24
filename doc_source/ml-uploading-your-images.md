# Uploading your images<a name="ml-uploading-your-images"></a>

 This section provides a walkthrough for uploading your inference and training images to Amazon Elastic Container Registry\. [Amazon ECR](http://aws.amazon.com/ecr/)is a fully managed Docker registry\.  This is where Amazon SageMaker pulls images from to create a model package for inference or algorithm for training jobs\. This is also where AWS Marketplace retrieves the images to publish your model package and algorithm products\. 

## Which images must I upload?<a name="ml-which-images-must-i-upload"></a>

 If you're publishing a model package, upload only an inference image\. If you're publishing an algorithm, upload both an inference image and a training image\. If the inference and training images are combined, upload the combined image only once\. 

## What IAM permissions are required?<a name="ml-what-iam-permissions-are-required"></a>

 The following steps assume that the local machine has the correct AWS credentials for an AWS Identity and Access Management \(IAM\) role or user in the seller AWS account\. The role or user must have the correct policies in place for both AWS Marketplace and Amazon ECR\. For example, you could use the following AWS managed policies: 
+  AWSMarketplaceSellerProductsFullAccess – For access to AWS Marketplace 
+  AmazonEC2ContainerRegistryFullAccess – For access to Amazon ECR 

## Log your Docker client into AWS<a name="ml-log-in-your-docker-client"></a>

 Set a variable for the AWS Region that you want to publish from \(see [Supported AWS Regions for publishing](ml-service-restrictions-and-limits.md#ml-supported-aws-regions-for-publishing)\)\. For this example, use the US East \(Ohio\) Region\. 

```
region=us-east-2
```

 Run the following command to set a variable with your AWS account ID\. This example assumes that the current AWS Command Line Interface \(AWS CLI\) credentials belong to the seller’s AWS account\. 

```
account=$(aws sts get-caller-identity --query Account --output text)
```

 To authenticate your Docker CLI client with your AWS account Amazon ECR Docker registry for your Region, run the following command\.

```
aws ecr get-login-password \
--region ${region} \
| sudo docker login \
--username AWS \
--password-stdin \
${account}.dkr.ecr.${region}.amazonaws.com
```

## Create repository and upload image<a name="ml-create-repository-and-upload-image"></a>

 Set a variable for the tag of the uploaded image and another variable for the name of the uploaded image repository\. 

```
image=my-inference-image
repo=my-inference-image
```

**Note**  
 In previous sections of this guide where the inference and training images were built, they were tagged as **my\-inference\-image** and **my\-training\-image**, respectively\. For this example, create and upload the inference image to a repository with the same name\. 

 Run the following command to create the image repository in Amazon ECR\. 

```
aws ecr --region ${region} create-repository --repository-name "${repo}"
```

 The full name of the Amazon ECR repository location is made up of the following parts: ` <account-id>.dkr.ecr.<region>.amazonaws.com/<image-repository-name>` 

 To push the image to the repository, you must tag it with the full name of the repository location\. 

 Set a variable for the full name of the image repository location along with the `latest` tag\. 

```
fullname="${account}.dkr.ecr.${region}.amazonaws.com/${repo}:latest"
```

 Tag the image with the full name\. 

```
sudo docker tag ${image} ${fullname}
```

 Finally, push the inference image to the repository in Amazon ECR\. 

```
sudo docker push ${fullname}
```

 After the upload completes, the image appears in the [repository list of the Amazon ECR console](https://console.aws.amazon.com/ecr/repositories?region=us-east-2) in the Region that you are publishing from\. In the previous example, the image was pushed to a repository in the US East \(Ohio\) Region\. 

## Scan your uploaded image<a name="ml-scan-your-uploaded-image"></a>

 In the [Amazon ECR console](https://console.aws.amazon.com/ecr/repositories?region=us-east-2), choose the AWS Region that you are publishing from, and open the repository that the image was uploaded to\. Select your uploaded image and start a scan to check for known vulnerabilities\. AWS Marketplace checks the Amazon ECR scan results of the container images used in your Amazon SageMaker resource before publishing it\. Before you can create your product, you must fix container images that have vulnerabilities with either a Critical or High severity\. 

 After your images are scanned successfully, they can be used to create a model package or algorithm resource\. 

If you believe that your product had errors in the scan that are false positives, contact [AWS Marketplace Seller Operations](http://aws.amazon.com/marketplace/management/contact-us) with information about the error\.

 **Next steps** 
+  See size limits in [Requirements and best practices for creating machine learning products](ml-listing-requirements-and-best-practices.md) 
+  Continue to [Creating your Amazon SageMaker resource](ml-creating-your-amazon-sagemaker-resource.md) 