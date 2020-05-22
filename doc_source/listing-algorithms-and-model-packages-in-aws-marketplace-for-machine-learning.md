# Putting your algorithms and model packages on the AWS Marketplace<a name="listing-algorithms-and-model-packages-in-aws-marketplace-for-machine-learning"></a>

To distribute your products to AWS customers using AWS Marketplace, you must perform these steps\.

**Topics**
+ [Package your code using Docker](#package-algorithms-Docker)
+ [Create your algorithm in Amazon SageMaker](#create-algorithms-in-sage-maker)
+ [Create your model package in Amazon SageMaker](#create-model-package)
+ [Add your algorithm or model package to AWS Marketplace](#listing-your-algorithm-or-model-package-in-aws-marketplace)
+ [Monetize your algorithm or model package](#monetizing-your-algorithm-or-model-package)

## Package your code using Docker<a name="package-algorithms-Docker"></a>

Amazon SageMaker is a fully managed machine learning platform that provides flexibility for training and deploying models\. Executable code – packaged using Docker containers – are run in secure and scalable infrastructure\. Depending on your use case, Amazon SageMaker can be used in one of the following ways:

1. Use the Amazon SageMaker built\-in algorithms to train and host models\.

1. Write and use Python scripts to use in the machine learning frameworks like TensorFlow, PyTorch, MXNet, and Chainer\.

1. Use Docker images with custom code\.

Amazon SageMaker builds and maintains the containers for the first and second use cases\. For the third use case, Amazon SageMaker lets customers package their own code into a Docker image\. This code can be written in any programming language with any dependencies\. These Docker images allow customers to run their code anywhere, without relying on the underlying hosting system\.

Your Docker image size is governed by the [Amazon ECR service limits](https://docs.aws.amazon.com/AmazonECR/latest/userguide/service_limits.html) in the *Amazon Elastic Container Registry User Guide*\. The Docker image size affects the start\-up time during training, batch transform, and endpoint creation jobs\. For better performance, we recommend that you maintain the optimal Docker image size\.

### Package your algorithm code<a name="package-algorithms"></a>

Before packaging your image as a usable Amazon SageMaker product, we strongly recommend that you use Amazon SageMaker to test your custom training, batch transform, and real\-time inference images\. To package an algorithm or model on AWS Marketplace, you must provide a self\-contained Docker image\. By packaging an algorithm in a container, you can use almost any code in Amazon SageMaker, regardless of programming language, environment, framework, or dependencies\.

After packaging your code into a Docker image, create the algorithm by entering metadata that allows Amazon SageMaker to expose the algorithms to customers on the AWS Marketplace\. 

**Important**  
When a buyer subscribes to your containerized product, the Docker containers are run in an isolated environment without internet\. When you create your containers, do not rely on making outgoing calls over the internet as they will fail\. Calls to AWS services will also fail\.

### Package your inference code<a name="package-inference-code"></a>

A model package can include the following elements:
+ An inference container
+ Optional model artifacts, which must be stored in Amazon S3

You create an inference container the same way as the algorithm container\. Providing the location of the model artifacts in Amazon S3 is optional\. You can choose to bundle your model artifacts within the inference container or let Amazon SageMaker retrieve them from your model storage location in Amazon S3\.

## Create your algorithm in Amazon SageMaker<a name="create-algorithms-in-sage-maker"></a>

An Amazon SageMaker algorithm has a training image and an inference image\. You can use the same image to perform both training and inference, or you can choose to separate them\. Training and inference images must remain compatible with each other and the model produced by the training image must be usable by the inference image\. We recommend that you verify the validation outputs, specifically the batch transform output\.

After packaging your code in Docker images, upload the images into Amazon Elastic Container Registry \(Amazon ECR\), and your Docker images will be scanned for known vulnerabilities\. You also need to create an IAM role that allows Amazon SageMaker to access the image\. For more information, see [https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-roles.html](https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-roles.html)\.

**To create your algorithm in Amazon SageMaker**

1. Open the Amazon SageMaker console and choose **Create algorithm**\.

1. Choose your Amazon ECR image\.

1. Enter the specifications for your algorithm\.

1. Provide a training specification, supported instance types, hyperparameters, inference and channel information, the input data type, and validation specifications\. You need a validation specification to sell the algorithm in AWS Marketplace\. It is used to create training and inference jobs when validating the algorithm\.

1. Your images will be scanned by default if you plan on selling your algorithm on AWS Marketplace\. 

Metadata helps buyers understand how to use your product and enables Amazon SageMaker to validate buyer requests synchronously after they have subscribed to your product\.

### Validate your algorithm<a name="validate-your-algorithm"></a>

To ensure that buyers and sellers can be confident that products work in Amazon SageMaker, we require that you validate your algorithms before listing them on AWS Marketplace\. To validate your algorithms, use your validation profile and sample data to run the following validation tasks:

1. Create a training job in your account to verify that your training image works with Amazon SageMaker\.

1. Create a model in your account using the algorithm's inference image and the model artifacts produced by the training job\.

1. Create a transform job in your account using the model to verify that your inference image works with Amazon SageMaker\.

When you list your product on AWS Marketplace, the inputs and outputs of this validation process persist as part of your product and are made available to your buyers\. This helps buyers understand and evaluate the product before they buy it\. For example, buyers can inspect the input data that you used, the outputs generated, and the logs and metrics emitted by your code\. The more comprehensive your validation specification, the easier it is for customers to evaluate your product\.

To see the status of the jobs in your account, in the Amazon SageMaker console, see the **Training jobs** and **Transform jobs** pages in the console\. If validation or scanning fail, you can access the scan and validation reports from the Amazon SageMaker console by clicking on their status\. For additional details, you also can review the training and transform jobs that were created during validation\. After fixing issues, recreate the algorithm\. When the status of the algorithm is **COMPLETED**, find it in the Amazon SageMaker console and start the process of putting your product on the AWS Marketplace\.

**Note**  
Scanning and validation can take up to a few hours\.

## Create your model package in Amazon SageMaker<a name="create-model-package"></a>

After you have packaged your code as an inference container, and have the optional model artifacts stored in Amazon S3, you are ready to create the model package in Amazon SageMaker\. To do this, use the following procedure:

**To create your model package**

1. Push the Docker image that you built to an Amazon ECR repository in your AWS account\. For more information, see [Pushing an Image](https://docs.aws.amazon.com/AmazonECR/latest/userguide/docker-push-ecr-image.html) in the Amazon Elastic Container Registry User Guide\.

1. Set up permissions that allow Amazon SageMaker to access the Amazon ECR images and Amazon S3 objects\.

1. Open the Amazon SageMaker console, choose **Create model package**, and follow the instructions\.

To finish creating your model package, provide inference image and validation specifications, and your Docker images will be scanned for known vulnerabilities\.

### Validate your model package<a name="validate-model-package"></a>

Before listing model packages on AWS Marketplace, you must validate them\. This ensures that buyers and sellers can be confident that products work in Amazon SageMaker\. You can list products on AWS Marketplace only if validation succeeds\. 

The validation procedure uses your validation profile and sample data to perform the following validations tasks:

1. Create a model in your account using the model package's inference image and the optional model artifacts that are stored in Amazon S3\.

1. Create a transform job in your account using the model to verify that your inference image works with Amazon SageMaker\.

1. Create a validation profile\.

When you list your products on AWS Marketplace, the inputs and outputs of the validation process persist as part of your product and are made available to your buyers\. This helps buyers understand and evaluate the product before they buy it\. For example, they can inspect the input data that you used, the outputs generated, and the logs and metrics emitted by your code\. The more comprehensive the validation specification, the easier it is for customers to evaluate your product\.

**Important**  
In your validation profile, provide only data that you want to expose publicly\. 

To see the status of the jobs in your account, in the Amazon SageMaker console, see the **Training jobs** and **Transform jobs** pages in the console\. If validation or scanning fail, you can access the scan and validation reports from the Amazon SageMaker console by clicking on their status\. For additional details, you also can review the training and transform jobs that were created during validation\. After fixing issues, recreate the algorithm\. When the status of the algorithm is **COMPLETED**, find it in the Amazon SageMaker console and start the process of putting your product on the AWS Marketplace\.

**Note**  
Scanning and validation can take up to a few hours\.

## Add your algorithm or model package to AWS Marketplace<a name="listing-your-algorithm-or-model-package-in-aws-marketplace"></a>

After creating and validating your algorithm or model package in Amazon SageMaker, you can put your product on the AWS Marketplace\. This process makes your products available in the AWS Marketplace and the Amazon SageMaker console\.

**Note**  
If you have not registered to sell on AWS Marketplace, review [Getting started as a seller](user-guide-for-sellers.md) and complete the registration process\. 

After you've registered, do one of the following to add your product to AWS Marketplace: 
+ From the Amazon SageMaker console, choose the product, choose **Actions**, and choose **Publish new AWS Marketplace listing**\. This carries over your product reference, the Amazon Resource Name \(ARN\), and directs you to the AMMP to create the listing\. 
+ Navigate to [ML listing process](https://aws.amazon.com/marketplace/management/ml-products/), manually enter the \(ARN, and start listing your product\. This process carries over the product metadata that you entered when you created the product in Amazon SageMaker\. This information includes the training specification, supported instance types, hyperparameters, inference and channel information, input data type, and sample data\. 

When adding a product on AWS Marketplace, you'll provide the following:
+ General product information 
+ Launch option 
+ Pricing and terms 

 **General product information** 

Enter the product description, promotional resources, support information, and region availability\. This information will appear on the AWS Marketplace product detail page\. It is searchable in AWS Marketplace\. 

The resources for your product must include sample input data and sample notebooks that customers can use to get started with your model or algorithm\. For more information, see [Best practices for sample input data and sample notebooks](best-practices-sample-ml.md)\.

 **Launch option** 

Define general usage information, a customer\-facing version number, and release notes\. Review the Amazon SageMaker metadata, such as Amazon SageMaker content types, MIME types, supported input methods, and hyperparameters\. 

 **Pricing and terms** 

Define a EULA, pricing, the product tax code, and the refund policy\. When you provide a paid algorithm, you can enter a training price for the algorithm and real\-time and batch inference prices for the inference image packaged with the algorithm\. When you list a model package, you can define real\-time and batch inference prices for the package\. 

For both algorithms and model packages, you can define prices for each supported instance type per hour\. You can enable a free\-trial and specify the number of days for its duration\.

 **Product publishing** 

You publish products through the AWS Marketplace Management Portal\. The publishing process has a few steps, which allows you to review your product information one last time before it's available for customers\.

The first step requires that you provide general information, launch options, and set the pricing and terms for your product\. The second step allows you to test your product before it's live\. At this point, your product has been published in a non\-public limited state\.

After testing has completed, you can choose **Sign off and publish** and select a version number for the product to be publicly available\. At this point, your product is in a **Published \(draft\)** state\.

Making your product public can take 30 to 60 minutes\. If you try to access the AWS Marketplace product detail page during the publishing process, you might get a 404 error\. This is expected while the information propagates through multiple systems\. 

## Monetize your algorithm or model package<a name="monetizing-your-algorithm-or-model-package"></a>

For algorithms and model packages, AWS Marketplace has an hourly pricing model per instance type\. Algorithms have two prices: training price and inference price\. Model packages have only an inference price\. Amazon SageMaker supports real\-time and batch inference modes, and you can set different prices for each mode\. Buyer usage is metered and billed in one\-second increments\. 