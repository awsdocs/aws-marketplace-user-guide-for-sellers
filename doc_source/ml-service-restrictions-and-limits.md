# Service restrictions and quotas<a name="ml-service-restrictions-and-limits"></a>

This section describes restrictions and quotas on your machine learning \(ML\) products in AWS Marketplace\.

## Network isolation<a name="ml-network-isolation"></a>

For security purposes, when a buyer subscribes to your containerized product, the Docker containers are run in an isolated environment without network access\. When you create your containers, don't rely on making outgoing calls over the internet because they will fail\. Calls to AWS services will also fail\. 

## Image size<a name="ml-image-size"></a>

Your Docker image size is governed by the Amazon Elastic Container Registry \(Amazon ECR\) [service quotas](https://docs.aws.amazon.com/AmazonECR/latest/userguide/service_limits.html)\. The Docker image size affects the startup time during training jobs, batch\-transform jobs, and endpoint creation\. For better performance, maintain an optimal Docker image size\. 

## Storage size<a name="ml-storage-size"></a>

When you create an endpoint, Amazon SageMaker attaches an Amazon Elastic Block Store \(Amazon EBS\) storage volume to each ML compute instance that hosts the endpoint\. \(An endpoint is also known as *real\-time inference* or *Amazon SageMaker hosting service*\.\) The size of the storage volume depends on the instance type\. For more information, see [Host Instance Storage Volumes](https://docs.aws.amazon.com/sagemaker/latest/dg/host-instance-storage.html)\. For batch transform, keep these limits in mind\. 

## Instance size<a name="ml-instance-size"></a>

SageMaker provides a selection of instance types that are optimized to fit different ML use cases\. Instance types are comprised of varying combinations of CPU, GPU, memory, and networking capacity\. Instance types give you the flexibility to choose the appropriate mix of resources for building, training, and deploying your ML models\. For more information, see [Amazon SageMaker ML Instance Types](http://aws.amazon.com/sagemaker/pricing/instance-types/)\. 

## Payload size for inference<a name="ml-payload-size-for-inference"></a>

 For an endpoint, the maximum size of the input data per invocation is 25 MB\. This value can't be adjusted\. If your software expects larger input sizes, your buyers can deploy endpoints configured for [Amazon SageMaker Asynchronous Inference](https://docs.aws.amazon.com/sagemaker/latest/dg/async-inference.html)\. If Asynchronous Inference is needed, provide detailed usage information so that your buyers configure the endpoint properly\.

For batch transform, the maximum size of the input data per invocation is 100 MB\. This value can't be adjusted\. 

## Processing time for inference<a name="ml-processing-time-for-inference"></a>

For an endpoint, the maximum processing time per invocation is 60 seconds\. If your software requires longer processing times, your buyers can deploy endpoints configured for [Amazon SageMaker Asynchronous Inference](https://docs.aws.amazon.com/sagemaker/latest/dg/async-inference.html)\. If Asynchronous Inference is needed, provide detailed usage information so that your buyers configure the endpoint properly\.

For batch transform, the maximum processing time per invocation is 60 minutes\. This value can't be adjusted\. 

## Service quotas<a name="ml-service-quotas"></a>

For more information about quotas related to training and inference, see [Amazon SageMaker Service Quotas](https://docs.aws.amazon.com/general/latest/gr/sagemaker.html#limits_sagemaker)\. 

## Managed spot training<a name="ml-managed-spot-training"></a>

For all algorithms from AWS Marketplace, the value of `MaxWaitTimeInSeconds` is set to 3,600 seconds \(60 minutes\), even if the checkpoint for [managed spot training](https://docs.aws.amazon.com/sagemaker/latest/dg/model-managed-spot-training.html) is implemented\. This value can't be adjusted\. 

## Docker images and AWS accounts<a name="ml-docker-images-and-aws-accounts"></a>

For publishing, images must be stored in Amazon ECR repositories owned by the AWS account of the seller\. It isn't possible to publish images that are stored in a repository owned by another AWS account\. 

## Publishing model packages from built\-in algorithms or AWS Marketplace<a name="ml-publishing-model-packages-from-built-in-algorithms-or-aws-marketplace"></a>

Model packages created from training jobs using an [Amazon SageMaker built\-in algorithm](https://docs.aws.amazon.com/sagemaker/latest/dg/algos.html) or an algorithm from an AWS Marketplace subscription can't be published\. 

You can still use the model artifacts from the training job, but your own inference image is required for publishing model packages\. 

## Supported AWS Regions for publishing<a name="ml-supported-aws-regions-for-publishing"></a>

AWS Marketplace supports publishing model package and algorithm resources from AWS Regions where the following are both true: 
+ A Region that [ Amazon SageMaker supports](http://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) 
+ An [available Region](http://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) that is opted\-in by default \(for example, [ describe\-regions](https://docs.aws.amazon.com/general/latest/gr/rande-manage.html#ec2-describe-regions) returns `"OptInStatus": "opt-in-not-required"`\) 

All assets required for publishing a model package or algorithm product must be stored in the same Region that you choose to publish from\. This includes the following: 
+ Model package and algorithm resources that are created in Amazon SageMaker 
+ Inference and training images that are uploaded to Amazon ECR repositories 
+ Model artifacts \(if any\) that are stored in Amazon Simple Storage Service \(Amazon S3\) and dynamically loaded during model deployment for model package resources 
+ Test data for inference and training validation that are stored in Amazon S3 

You can develop and train your product in any Region that is supported by SageMaker\. But, before you can publish, you must copy all assets to and re\-create resources in a Region that AWS Marketplace supports publishing from\. 

During the listing process, regardless of the AWS Region that you publish from, you can choose the Regions that you want to publish to and make your product available in\. 