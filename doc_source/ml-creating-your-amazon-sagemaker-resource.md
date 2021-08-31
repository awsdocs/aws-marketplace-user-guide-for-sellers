# Creating your Amazon SageMaker resource<a name="ml-creating-your-amazon-sagemaker-resource"></a>

 To publish a model package or algorithm product, you must create the respective [ model package resource](https://docs.aws.amazon.com/marketplace/latest/userguide/ml-creating-your-amazon-sagemaker-resource.html#ml-creating-your-model-package-product) or [ algorithm resource](https://docs.aws.amazon.com/marketplace/latest/userguide/ml-creating-your-amazon-sagemaker-resource.html#ml-creating-your-algorithm-product) in Amazon SageMaker\. 

 When you create your resource for an AWS Marketplace product, it must be certified through a validation step\. The validation step requires that you provide data to test your model package or algorithm resource before it can be published\. 

**Note**  
If you haven't yet created the images for your product and uploaded them to Amazon Elastic Container Registry \(Amazon ECR\), see [Packaging your code into images](ml-packaging-your-code-into-images.md) and [Uploading your images](ml-uploading-your-images.md) for information about how to do so\.

## Creating your model package<a name="ml-creating-your-model-package-product"></a>

 The following are requirements for creating a model package for AWS Marketplace: 
+  An inference image stored in [Amazon ECR](http://aws.amazon.com/ecr/) 
+  \(Optional\) Model artifacts, stored separately in [Amazon S3](http://aws.amazon.com/s3/) 
+ Your test data used for inferences, stored in Amazon Simple Storage Service \(Amazon S3\) 

**Note**  
 The following is about creating a model package product\. For more information about model packages in SageMaker, see [Create a Model Package Resource](https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-mkt-create-model-package.html)\. 

### Creating the model package resources<a name="ml-create-model-package"></a>

The following procedures step you through creating the model package resources\.

**Step 1: To create the model package resources**

1. Open the [ Amazon SageMaker console](https://us-east-2.console.aws.amazon.com/sagemaker/home)\.

1. Ensure that you are in the AWS Region that you want to publish from by looking at the top right of the page\. For publishing, see the [Supported AWS Regions for publishing](ml-service-restrictions-and-limits.md#ml-supported-aws-regions-for-publishing) section\. The inference image you uploaded to Amazon ECR in previous steps must be in the same Region\. 

1. In the left navigation menu, choose **Model packages**\.

1. Choose **Create model package**\.

After you create the package, you need to set the specifications of the inference package\.

**Step 2: To set inference specifications**

1.  Provide a **Name** for your model package \(for example, *my\-model\-package*\)\. 

1.  For **Location of inference image**, enter the URI of your inference image that was uploaded to Amazon ECR\. You can retrieve the URI by locating your image in the [Amazon ECR console](https://us-east-2.console.aws.amazon.com/ecr/repositories)\. 

1.  If your model artifacts from training are bundled with your logic in your inference image, leave the **Location of model data artifacts** empty\. Otherwise, specify the full Amazon S3 location of the compressed file \(\.tar\.gz\) of your model artifacts\. 

1.  Using the dropdown box, choose the supported instance types of your inference image for both real\-time inference \(also known as *endpoint*\) and batch\-transform jobs\. 

1.  Choose **Next**\. 

 Before your model package can be created and published, validation is necessary to ensure that it functions as expected\. This requires that you run a batch transform job with test data for inference that you provide\. The validation specifications tell SageMaker how to perform the validation\. 

**Step 3: To set validation specifications**

1.  Set **Publish this model package in AWS Marketplace** to **Yes**\. If you set this to **No**, you can't publish this model package later\. Choosing **Yes** [ certifies](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_CreateModelPackage.html#sagemaker-CreateModelPackage-request-CertifyForMarketplace) your model package for AWS Marketplace and requires the validation step\. 

1.  If this is the first time completing this process, choose **Create a new role** for the **IAM role**\. Amazon SageMaker uses this role when it deploys your model package\. This includes actions, such as pulling images from Amazon ECR and artifacts from Amazon S3\. Review the settings, and choose **Create role**\. Creating a role here grants permissions described by the [ AmazonSageMakerFullAccess](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AmazonSageMakerFullAccess) IAM policy to the role that you create\. 

1.  Edit the **JSON** in the validation profile\. For details about allowed values, see [TransformJobDefinition](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_TransformJobDefinition.html)\. 

   1.  `TransformInput.DataSource.S3Uri`: Set to where your test data for inference is stored\. 

   1.  `TransformInput.ContentType`: Specify your test data content type \(for example, `application/json`, `text/plain`, `image/png `, or any other value\)\. SageMaker does not validate the actual input data\. This value is passed to your container HTTP endpoint in the `Content-type` header value\. 

   1.  `TransformInput.CompressionType`: Set to `None` if your test data for inference in Amazon S3 is not compressed\. 

   1.  `TransformInput.SplitType`: Set to `None` to pass each object in Amazon S3 as a whole for inference\. 

   1.  `TransformOutput.S3OutputPath`: Set to the location that the inference output is stored\. 

   1.  `TransformOutput.AssembleWith`: Set to `None` to output each inference as separate objects in Amazon S3\. 

1.  Choose **Create model package**\. 

 SageMaker pulls the inference image from Amazon ECR, copies any artifacts to the inference container, and runs a batch transform job using your test data for inference\. After the validation succeeds, the status changes to **Completed**\. 

**Note**  
 The validation step does not evaluate the accuracy of the model with your test data\. The validation step checks if the container runs and responds as expected\. 

 You have completed creating your model product resources\. Continue to [Publishing your product in AWS Marketplace](ml-publishing-your-product-in-aws-marketplace.md)\. 

## Creating your algorithm<a name="ml-creating-your-algorithm-product"></a>

 The following are requirements for creating an algorithm for AWS Marketplace: 
+ An inference image, stored in Amazon ECR 
+ A training image, stored in Amazon ECR 
+  Your test data for training, stored in Amazon S3 
+ Your test data for inference, stored in Amazon S3 

**Note**  
 The following walkthrough creates an algorithm product\. For more information, see [Create an Algorithm Resource](https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-mkt-create-algo.html)\. 

### Creating the algorithm resources<a name="ml-create-algorithm"></a>

The following procedures step you through creating the resources in your algorithm package\.

**Step 1: To create the algorithm resources**

1.  Open the [ Amazon SageMaker console](https://us-east-2.console.aws.amazon.com/sagemaker/home)\. 

1.  Ensure that you are in the AWS Region that you want to publish from by looking at the top right of the page \(see [Supported AWS Regions for publishing](ml-service-restrictions-and-limits.md#ml-supported-aws-regions-for-publishing)\)\. The training and inference images you uploaded to Amazon ECR in previous steps must be in this same Region\. 

1.  In the left navigation menu, choose **Algorithms**\. 

1.  Choose **Create algorithm**\. 

After you have created the algorithm package, you must set the specifications for the training and tuning of your model\.

**Step 2: To set the training and tuning specifications**

1.  Enter the **Name** for your algorithm \(for example, *my\-algorithm*\)\. 

1.  For **Training image**, paste the full URI location of your training image that was uploaded to Amazon ECR\. You can retrieve the URI by locating your image in the [Amazon ECR console](https://us-east-2.console.aws.amazon.com/ecr/repositories)\. 

1.  Using the dropdown box, choose the **instance types for training** that your training image supports\. 

1.  Under the **Channel specification** section, add a channel for each input dataset that your algorithm supports, up to 20 channels of input sources\. For more information, see [ Input Data Configuration](https://docs.aws.amazon.com/sagemaker/latest/dg/your-algorithms-training-algo-running-container.html#your-algorithms-training-algo-running-container-inputdataconfig)\. 

1.  Choose **Next**\. 

1. If your algorithm supports hyperparameters and hyperparameter tuning, you must specify the tuning parameters\.

1.  Choose **Next**\. 

**Note**  
 We highly recommend that your algorithm supports hyperparameter tuning and makes appropriate parameters tunable\. This allows data scientists to tune models to get the best results\. 

After you have set the tuning parameters, if any, you must set the specifications for your inference image\.

**Step 3: To set inference image specification**

1.  For **Location of inference image**, paste the URI of the inference image that was uploaded to Amazon ECR\. You can retrieve the URI by locating your image in the [Amazon ECR Console](https://us-east-2.console.aws.amazon.com/ecr/repositories)\. 

1.  Using the dropdown box, choose the supported instance types for your inference image for both real\-time inference \(also known as *endpoint*\) and batch\-transform jobs\. 

1.  Choose **Next**\. 

 Before your algorithm can be created and published, validation is necessary to ensure that it functions as expected\. This requires that you run both a training job with test data for training and a batch transform job with test data for inference that you provide\. The validation specifications tell SageMaker how to perform the validation\. 

**Step 4: To set validation specifications**

1.  Set **Publish this algorithm in AWS Marketplace** to **Yes**\. If you set this to **No**, you can't publish this algorithm later\. Choosing **Yes** [ certifies](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_CreateAlgorithm.html#sagemaker-CreateAlgorithm-request-CertifyForMarketplace) your algorithm for AWS Marketplace and requires the validation specification\.

1.  If this is your first time creating a machine learning package for AWS Marketplace, choose **Create a new role** for the **IAM role**\. Amazon SageMaker uses this role when training your algorithm and deploying the subsequent model package\. This includes actions such as pulling images from Amazon ECR, storing artifacts in Amazon S3, and copying training data from Amazon S3\. Review the settings, and choose **Create role**\. Creating a role here grants permissions described by the [ AmazonSageMakerFullAccess](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AmazonSageMakerFullAccess) IAM policy to the role that you create\. 

1.  Edit the **JSON** file in the validation profile for **Training job definition**\. For more information about allowed values, see [ TrainingJobDefinition](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_TrainingJobDefinition.html)\. 

   1.  `InputDataConfig`: In this JSON array, add a [Channel object](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_Channel.html) for each channel that you specified in the training\-specification step\. For each channel, specify where your test data for training is stored\. 

   1.  `OutputDataConfig`: After the training completes, the model artifacts in the training container directory path `/opt/ml/model/` are compressed and copied out to Amazon S3\. Specify the Amazon S3 location of where the compressed file \(\.tar\.gz\) is stored\. 

1.  Edit the JSON file in the validation profile for **Transform job definition**\. For more information about allowed values, see [ TransformJobDefinition](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_TransformJobDefinition.html)\. 

   1.  `TransformInput.DataSource.S3Uri`: Set to where your test data for inference is stored\. 

   1.  `TransformInput.ContentType`: Specify your test data content type\. For example, `application/json`, `text/plain`, `image/png`, or any other value\. Amazon SageMaker does not validate the actual input data\. This value is passed to your container HTTP endpoint in the `Content-type` header value\. 

   1.  `TransformInput.CompressionType`: Set to `None` if your test data for inference in Amazon S3 is not compressed\. 

   1.  `TransformInput.SplitType`: Choose how you want objects in S3 split\. For example, `None` passes each object in Amazon S3 as a whole for inference\. For more details, see [ SplitType](https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_TransformInput.html#sagemaker-Type-TransformInput-SplitType) in the Amazon SageMaker API Reference\. 

   1.  `TransformOutput.S3OutputPath`: Set to the location where the inference output is stored\. 

   1.  `TransformOutput.AssembleWith`: Set to `None` to output each inference as separate objects in Amazon S3\. 

1. Choose **Create algorithm package**\.

 SageMaker pulls the training image from Amazon ECR, runs a test\-training job using your data, and stores the model artifacts in Amazon S3\. It then pulls the inference image from Amazon ECR, copies the artifacts from Amazon S3 into the inference container, and runs a batch transform job using your test data for inference\. After the validation succeeds, the status changes to **Completed**\. 

**Note**  
 The validation step does not evaluate the accuracy of the training or the model with your test data\. The validation step checks if the containers run and respond as expected\.   
The validation step only validates batch processing\. It is up to you to validate that real\-time processing works with your product\.

 You have completed creating your algorithm product resources\. Continue to [Publishing your product in AWS Marketplace](ml-publishing-your-product-in-aws-marketplace.md)\. 