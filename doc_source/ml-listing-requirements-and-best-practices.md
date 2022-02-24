# Requirements and best practices for creating machine learning products<a name="ml-listing-requirements-and-best-practices"></a>

It is important that your buyers find it easy to test your model package and algorithm products\. The following sections describe the requirements for creating machine learning \(ML\) product listings and best practices for ML products\. For a complete summary of requirements and recommendations, see the [Summary of requirements and recommendations for ML product listings](#ml-summary-table-of-requirements-and-recommendations)\.

**Note**  
An AWS Marketplace representative might contact you to help you meet these requirements if your published products don't meet them\.

**Topics**
+ [Required assets](#ml-required-assets)
+ [General best practices for ML products](#ml-general-best-practices)
+ [Requirements for usage information](#ml-requirements-for-usage-information)
+ [Requirements for inputs and outputs](#ml-requirements-for-inputs-and-outputs)
+ [Requirements for Jupyter notebook](#ml-requirements-for-jupyter-notebook)
+ [Summary of requirements and recommendations for ML product listings](#ml-summary-table-of-requirements-and-recommendations)

## Required assets<a name="ml-required-assets"></a>

Before creating a machine learning product listing, ensure that you have the following required assets: 
+ **Amazon Resource Name \(ARN\)** – Provide the ARN of the model package or algorithm resource in the AWS Region that you are publishing from \(see [Supported AWS Regions for publishing](ml-service-restrictions-and-limits.md#ml-supported-aws-regions-for-publishing)\)\. 
  +  An ARN for a model package has this form: `arn:aws:sagemaker:<region>:<account-id>:model-package/<model-package-name>` 
  +  An ARN for an algorithm has this form: `arn:aws:sagemaker:<region>:<account-id>:algorithm/<algorithm-name>` 
+ [Requirements for usage information](#ml-requirements-for-usage-information) – Provide details about inputs, outputs, and code examples\. 
+  [Requirements for inputs and outputs](#ml-requirements-for-inputs-and-outputs) – Provide either files or text\. 
+ [Requirements for Jupyter notebook](#ml-requirements-for-jupyter-notebook) – Demonstrate complete product usage\. 

## General best practices for ML products<a name="ml-general-best-practices"></a>

 Provide the following information for your machine learning product: 
+  For product descriptions, include the following: 
  +  What your model does 
  +  Who the target customer is 
  +  What the most important use case is 
  +  How your model was trained or the amount of data that was used 
  +  What the performance metrics are and the validation data used 
  +  If medical, whether or not your model is for diagnostic use 
+  Optionally, for paid products, offer a free trial of 14–30 days for customers to try your product\. For more information, see [Machine learning product pricing](machine-learning-pricing.md)\. 
+  Optionally, for model package products, if you want to enable a real\-time product demo on your product listing page, contact [AWS Marketplace Seller Operations](http://aws.amazon.com/marketplace/management/contact-us/)\. The product demo allows a prospective buyer to try your model directly on the listing page without subscribing to or deploying the model themselves\. 

## Requirements for usage information<a name="ml-requirements-for-usage-information"></a>

Clear usage information that describes the expected inputs and outputs of your product \(with examples\) is crucial for driving a positive buyer experience\. 

With each new version of your resource that you add to your product listing, you must provide usage information\. 

To add usage information for a new product that you are publishing for the first time, sign into the AWS Marketplace Management Portal console\. From the Products dropdown, choose **Machine learning**\. Select your product\. In the **Product Overview** under **Launch option**, provide the ARN of your model package or algorithm resource, and choose **Add**\. 

To edit the existing usage information for a specific version, choose **Edit** under **Launch option** and then **Edit version**\. 

## Requirements for inputs and outputs<a name="ml-requirements-for-inputs-and-outputs"></a>

A clear explanation of your format, with examples of inputs and outputs, is important to help your buyers to understand and use your product\. This understanding helps your buyers to perform any necessary transformations on the input data to get the best inference results\. 

You will be prompted for the following when adding your SageMaker resource to your product listing\.

### Inference inputs and outputs<a name="ml-inference-inputs-and-outputs"></a>

For inference input, provide the input format for both the real\-time endpoint and batch transform job\. Include code snippets for any necessary preprocessing of the data\. Include supported MIME content types \(for example, **image/jpeg**, **image/png**, **image/bmp**\), descriptions of values if applicable, and limitations\. Include input samples hosted on [GitHub](https://github.com)\.

For inference output, provide the output format for the both real\-time endpoint and batch transform job\. Include output MIME content type \(for example, **application/json**, **image/jpeg**\) and description of values if applicable\. Include output samples hosted on [GitHub](https://github.com)\. 

For samples, provide input files that work with your product\. If your model performs multiclass classification, provide at least one sample input file for each class\. 

### Training inputs<a name="ml-training-inputs"></a>

In the **Information to train a model** section, provide the input data format and code snippets for any necessary preprocessing of the data\. Include supported MIME content types \(for example, **image/jpeg**, **image/png**, **image/bmp**\), description of values if applicable, and limitations\. Ensure to include input samples hosted on [GitHub](https://github.com)\. 

Explain both optional and mandatory features that can be provided by the buyer, and specify whether the PIPE input mode is supported\. If [distributed training](https://docs.aws.amazon.com/sagemaker/latest/dg/your-algorithms-training-algo-running-container.html#your-algorithms-training-algo-running-container-dist-training) \(training with more than 1 CPU/GPU instance\) is supported, specify this\. For tuning, list the recommend hyperparameters\. 

## Requirements for Jupyter notebook<a name="ml-requirements-for-jupyter-notebook"></a>

When adding your SageMaker resource to your product listing, provide a link to a sample Jupyter notebook hosted on [GitHub](https://github.com) that demonstrates the complete workflow without asking the buyer to upload or find any data\. 

Use the AWS SDK for Python \(Boto\)\. A well\-developed sample notebook makes it easier for buyers to try and use your listing\. 

For model package products, your sample notebook demonstrates the preparation of input data, creation of an endpoint for real\-time inference, and performance of batch\-transform jobs\. For more information, see [Model Package listing and Sample notebook](https://github.com/awslabs/amazon-sagemaker-examples/tree/master/aws_marketplace/curating_aws_marketplace_listing_and_sample_notebook/ModelPackage) on GitHub\. For sample notebooks, see [generic\_sample\_notebook](https://github.com/awslabs/amazon-sagemaker-examples/tree/master/aws_marketplace/using_model_packages/generic_sample_notebook) and [auto\_insurance](https://github.com/awslabs/amazon-sagemaker-examples/tree/master/aws_marketplace/using_model_packages/auto_insurance)\. The latter sample notebook works in all Regions, without entering any parameters and without a buyer needing to locate sample data\.

**Note**  
An underdeveloped sample Jupyter notebook that does not show multiple possible inputs and data preprocessing steps might make it difficult for the buyer to fully understand your product's value proposition\. 

For algorithm products, the sample notebook demonstrates complete training, tuning, model creation, the creation of an endpoint for real\-time inference, and the performance of batch\-transform jobs \(see [Algorithm listing and Sample notebook](https://github.com/awslabs/amazon-sagemaker-examples/tree/master/aws_marketplace/curating_aws_marketplace_listing_and_sample_notebook/Algorithm) on GitHub\)\. For sample notebooks, see [amazon\_demo\_product](https://github.com/awslabs/amazon-sagemaker-examples/tree/master/aws_marketplace/using_algorithms/amazon_demo_product) and [automl](https://github.com/awslabs/amazon-sagemaker-examples/tree/master/aws_marketplace/using_algorithms/automl) on GitHub\. These sample notebooks work in all Regions without entering any parameters and without a buyer needing to locate sample data\. 

**Note**  
A lack of example training data might prevent your buyer from running the Jupyter notebook successfully\. An underdeveloped sample notebook might prevent your buyers from using your product and hinder adoption\. 

## Summary of requirements and recommendations for ML product listings<a name="ml-summary-table-of-requirements-and-recommendations"></a>

The following table provides a summary of the requirements and recommendations for a machine learning product listing page\.


|  **Details**  |  **For model package listings**  |  **For algorithm listings**  | 
| --- |--- |--- |
| Product descriptions | 
| --- |
| Explain in detail what the product does for supported content types \(for example, “detects X in images"\)\.  |  Required  |  Required  | 
| Provide compelling and differentiating information about the product \(avoid adjectives like "best" or unsubstantiated claims\)\.  |  Recommended  |  Recommended  | 
| List most important use case\(s\) for this product\.  |  Required  |  Required  | 
| Describe the data \(source and size\) it was trained on and list any known limitations\.  |  Required  |  Not applicable | 
| Describe the core framework that the model was built on\.  |  Recommended  |  Recommended  | 
| Summarize model performance metric on validation data \(for example, "XX\.YY percent accuracy benchmarked using the Z dataset"\)\.  |  Required  |  Not applicable | 
| Summarize model latency and/or throughput metrics on recommended instance type\.  |  Required  |  Not applicable | 
| Describe the algorithm category\. For example, “This decision forest regression algorithm is based on an ensemble of tree\-structured classifiers that are built using the general technique of bootstrap aggregation and a random choice of features\.”  |  Not applicable |  Required  | 
| Usage information | 
| --- |
| For inference, provide the input format for both the real\-time endpoint and batch transform job\. Include supported MIME content types \(for example, image/jpeg, image/png, image/bmp\), description of values if applicable, and limitations\. See [Requirements for inputs and outputs](#ml-requirements-for-inputs-and-outputs)\.  |  Required  |  Required  | 
| For inference, provide input samples for both the real\-time endpoint and batch transform job\. Samples must be hosted on GitHub\. See [Requirements for inputs and outputs](#ml-requirements-for-inputs-and-outputs)\.  |  Required  |  Required  | 
| For inference, provide the output format for both the real\-time endpoint and batch transform job\. Include output MIME content type \(for example, application/json, image/jpeg\) and description of values if applicable\. See [Requirements for inputs and outputs](#ml-requirements-for-inputs-and-outputs)\.  |  Required  |  Required  | 
| For inference, provide output samples for both the real\-time endpoint and batch transform job\. Samples must be hosted on GitHub\. See [Requirements for inputs and outputs](#ml-requirements-for-inputs-and-outputs)\.  |  Required  |  Required  | 
| For inference, provide an example of using an endpoint or batch transform job\. Include a code example using the AWS Command Line Interface \(AWS CLI\) commands or using an AWS SDK\.  |  Required  |  Required  | 
| For training, provide input format\. Include supported MIME content types \(for example, image/jpeg, image/png, image/bmp\), description of values if applicable, and limitations \(for example, minimum rows of data required\)\. See [Requirements for inputs and outputs](#ml-requirements-for-inputs-and-outputs)\.  |  Not applicable |  Required  | 
| For training, provide input samples hosted on GitHub\. See [Requirements for inputs and outputs](#ml-requirements-for-inputs-and-outputs)\.  |  Not applicable |  Required  | 
| For training, provide an example of performing training jobs\. Describe the supported hyperparameters, their ranges, and their overall impact\. Specify if the algorithm supports hyperparameter tuning, distributed training, or GPU instances\. Include code example such as AWS CLI commands or using an AWS SDK, for example\.  |  Not applicable |  Required  | 
| Provide a Jupyter notebook hosted on GitHub demonstrating complete use of your product\. See [Requirements for Jupyter notebook](#ml-requirements-for-jupyter-notebook)\.  |  Required  |  Required  | 
| Provide technical information related to the usage of the product, including user manuals and sample data\.  |  Recommended  |  Recommended  | 