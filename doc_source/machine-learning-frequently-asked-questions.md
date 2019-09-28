# Frequently Asked Questions<a name="machine-learning-frequently-asked-questions"></a>

## How safe is my intellectual property?<a name="machine-learning-how-safe-is-my-intellectual-property"></a>

When you upload your algorithms or pre\-trained models, Amazon SageMaker scans your product for any vulnerabilities and encrypts the product artifacts and other system artifacts in transit and at rest\. When buyers launch your product, Amazon SageMaker deploys it in a secure environment with no access to the internet\. Amazon SageMaker allows access to your product only through the secure AWS SDK endpoints\. Buyers can't access your code or the infrastructure\. This helps safeguard your intellectual property\. You can also choose to encrypt the model artifacts to protect intellectual property that might be contained in the model files\. 

**Important**  
This security model prevents your code from accessing the internet during runtime\. Therefore, your code can't use any resources or libraries from the internet\. You must package your dependencies in your Docker container\. This is especially important if you choose to encrypt your artifacts because the keys to decrypt artifacts can't be accessed over the internet at run time\. They must be packaged with your image\. 

## How can I include algorithms and models that I built outside Amazon SageMaker?<a name="machine-learning-how-can-i-include-algorithms-and-models-that-i-have-built-outside-amazon-sagemaker"></a>

 With Amazon SageMaker, you can package and host your own machine learning algorithms and models on any framework\. You can use technology that you are familiar with to build algorithms and models\. To speed up the development process, AWS Marketplace offers open source base containers for Apache MXNet, TensorFlow, and other frameworks and a wide range of built\-in, high\-performance machine learning algorithms\. If you want to use an alternative framework, you can package it in your own Docker container and host it on Amazon SageMaker\. 

## What artifacts do I need to provide to list my algorithm or model?<a name="machine-learning-what-artifacts-do-i-need-to-provide-to-list-my-algorithm-or-model"></a>

 When you upload your product into Amazon SageMaker, you need to provide a product description, configuration information such as instance types, endpoint configurations, supported input types, and hyperparameters\. When you list your products on AWS Marketplace, you need to provide product marketing information, a sample Jupyter notebook, usage instructions, documentation, a sample data set, and support information\. 

## Can I support distributed algorithms?<a name="machine-learning-can-i-support-distributed-algorithms"></a>

 Yes\. When creating your algorithm on Amazon SageMaker, you can specify the number of concurrent instances supported for your algorithm\. 

## If I change my software resource on Amazon SageMaker, how does it affect my product and my customers?<a name="machine-learning-if-i-change-my-software-resource-on-amazon-sagemaker-how-will-it-affect-my-listing-and-my-customers"></a>

 Your product is created based on a deep \(escrowed\) copy of your software at the time it is added and is managed separately by AWS to protect buyers\. Making changes to or deleting algorithms or model packages on Amazon SageMaker doesn't affect your buyers\.

## Can I call external APIs \(for example, the seller's Amazon SageMaker APIs\) for ensemble modeling? Are there limitations?<a name="machine-learning-is-it-possible-to-call-external-apis-for-example-the-sellers-amazon-sagemaker-apis-or-others-for-ensemble-modeling-what-are-the-limitations"></a>

 You can perform ensembling internally by inferring from multiple models and taking a decision, all within a single container\. Currently, this operation can't span container boundaries\. 

## How can I offer a free trial for an algorithm or model?<a name="machine-learning-how-can-i-offer-a-free-trial-for-an-algorithm-or-model"></a>

 You can create a free trial for your product by creating a new offer in the AWS Marketplace Management Portal\. Choose **Offer a free trial** and define the number of free usage hours that a buyer gets and the duration of the trial, in days\. Next, define a pay\-as\-you\-go price and define the maximum number of hours that a customer can use for the free trial\. Buyers aren't charged for using the free units that you include in the trial, but are charged pay\-as\-you\-go prices for usage beyond the allowed free units\. 

## Which machine learning frameworks does Amazon SageMaker support?<a name="machine-learning-which-machine-learning-frameworks-are-supported-by-amazon-sagemaker"></a>

 Currently, Amazon SageMaker supports TensorFlow, Apache MXNet, PyTorch, and Chainer\. 

## Is there a limit on the size of my Docker image?<a name="machine-learning-is-there-a-limit-on-the-size-of-my-docker-image"></a>

 Your Docker image size is governed by the [Amazon ECR service limits](https://docs.aws.amazon.com/AmazonECR/latest/userguide/service_limits.html)\. The Docker image size affects the start\-up time during training, batch transform, and endpoint creation jobs\. For better performance, we recommend that you maintain the optimal Docker image size\. 

## Do I need to provide different Docker images for CPU and GPU instances?<a name="machine-learning-do-i-need-to-provide-different-docker-images-for-cpu-and-gpu-instances"></a>

 You can use the same Docker image to support CPU and GPU instances\. If your Docker image can't handle both GPU and CPU seamlessly, provide one image for each\. This requires two separate products\. 

## Can I provide a Docker image that takes more than 60 seconds of processing time to start?<a name="machine-learning-can-i-provide-a-docker-image-that-takes-more-than-60-seconds-of-processing-time-to-start"></a>

 Model containers must respond to requests within 60 seconds\. The model itself can take a maximum processing time of 60 seconds before responding to the /invocations\. If your model takes 50–60 seconds of processing time, set the SDK socket timeout to 70 seconds\. 

## Should I manage authentication and signature verification of the invocation endpoint for my algorithms and model packages?<a name="machine-learning-should-i-manage-authentication-and-signature-verification-of-the-invocation-endpoint-for-my-algorithms-and-model-packages"></a>

 No\. Amazon SageMaker enforces secure access to API endpoints\. 

## Can buyers view the logs that my algorithm or model package emits?<a name="machine-learning-will-buyers-be-able-to-view-the-logs-emitted-by-my-algorithm-or-model-package"></a>

 Yes\. See [What Is Amazon CloudWatch?](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html) for information on viewing log stream information in your account\. To protect your IP, be careful when emitting log messages\. 

## Can I view the buyer’s data trained with my models or the response that my model returned?<a name="machine-learning-can-i-view-the-buyers-data-trained-with-my-models-or-the-response-that-my-model-returned"></a>

 No\. To ensure the security of buyers’ data, we don't support this feature\. 

## I haven’t trained my model in Amazon SageMaker\. Can I list it?<a name="machine-learning-i-havent-trained-my-model-in-amazon-sagemaker-can-i-list-it"></a>

 Yes\. You can bring in models that you trained in your own environment and list them on Amazon SageMaker by following the instructions for packaging Docker images\. To assess your model's performance, we recommend benchmarking them on Amazon SageMaker\. 

## How do I inform buyers about data pre\-processing requirements?<a name="machine-learning-how-do-i-inform-buyers-about-data-pre-processing-requirements"></a>

When you list your product on AWS Marketplace, include data pre\-processing requirements in your documentation and link to the documentation\. We strongly recommend providing a sample notebook and sample data to help your buyers get started with your product\. 