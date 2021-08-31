# Machine learning products<a name="machine-learning-products"></a>

 As a seller, you can use AWS Marketplace to create machine learning \(ML\) algorithms and models that your buyers can deploy in AWS\. There are two types of Amazon SageMaker products listed in AWS Marketplace: 

**Model package**  
 A pre\-trained model for making predictions that does not require any further training by the buyer\. 

**Algorithm**  
 A model that requires the buyer to supply training data before it makes predictions\. The training algorithm is included\. 

 These products are available to buyers through the Amazon SageMaker console or AWS Marketplace\. Buyers can review product descriptions, documentation, customer reviews, pricing, and support information\. When they subscribe to either a model package product or algorithm product, it’s added to their product list on the SageMaker console\. Buyers can also use AWS SDKs, the AWS Command Line Interface \(AWS CLI\), or the SageMaker console to create a fully managed REST inference endpoint or perform inference on batches of data\. 

 For support with creating machine learning products with Amazon SageMaker, contact [AWS Marketplace Seller Operations](http://aws.amazon.com/marketplace/management/contact-us/)\. 

## Getting started with machine learning products<a name="ml-getting-started"></a>

 AWS Marketplace supports two machine learning product types, using Amazon SageMaker\. Both types, the model package products and the algorithm products, produce a deployable inference model for making predictions\. 

### SageMaker model package<a name="ml-amazon-sagemaker-model-package"></a>

 An [ Amazon SageMaker model package](https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-marketplace.html#sagemaker-mkt-model-package) product contains a pre\-trained model\. Pre\-trained models can be deployed in SageMaker to make inferences or predictions in real time or in batches\. This product contains a trained inference component with model artifacts, if any\. As a seller, you can train a model using SageMaker or bring your own model\. 

### SageMaker algorithm<a name="ml-amazon-sagemaker-algorithm"></a>

 Buyers can use a [SageMaker algorithm](https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-marketplace.html#sagemaker-mkt-algorithm) product to perform complete machine learning workloads\. An algorithm product has two logical components: training and inference\. In SageMaker, buyers use their own datasets to create a training job with your training component\. When the algorithm in your training component completes, it generates the model artifacts of the machine learning model\. SageMaker saves the model artifacts in the buyers’ Amazon Simple Storage Service \(Amazon S3\) bucket\. In SageMaker, buyers can then deploy your inference component along with those generated model artifacts to perform inference \(or prediction\) in real time or in batches\. 

### Deploying an inference model<a name="ml-deploying-an-inference-model"></a>

 Whether the inference model is created from a model package or an algorithm, there are two methods to deploy them: 
+  **Endpoint** – This method uses SageMaker to deploy the model and create an API endpoint\. The buyer can use this endpoint as part of their backend service to power their applications\. When data is sent to the endpoint, SageMaker passes it to the model container and returns the results in an API response\. The endpoint and the container continue to run until stopped by the buyer\.
**Note**  
 In AWS Marketplace, the endpoint method is referred to as *real\-time inference*, and in the SageMaker documentation, it is referred to as *hosting services*\. For more information, see [Deploy a Model in Amazon SageMaker](https://docs.aws.amazon.com/sagemaker/latest/dg/how-it-works-deployment.html)\. 
+  **Batch transform job** – In this method, a buyer stores datasets for inference in Amazon S3\. When the batch transform job starts, SageMaker deploys the model, passes data from an S3 bucket to the model’s container, and then returns the results to an S3 bucket\. When the job completes, SageMaker stops the job\. For more information, see [Get Inferences for an Entire Dataset with Batch Transform](https://docs.aws.amazon.com/sagemaker/latest/dg/how-it-works-batch.html)\. 
**Note**  
 Both methods are transparent to the model because SageMaker passes data to the model and returns results to the buyer\. 