# Prepare your product in SageMaker<a name="ml-prepare-your-product-in-sagemaker"></a>

Before publishing your product in AWS Marketplace, you must prepare it in Amazon SageMaker\. There are three steps to preparing your product:

1. [Packaging your code into images](ml-packaging-your-code-into-images.md) – To prepare a model package or algorithm product, you must create the Docker container images for your product\. 

1. [Uploading your images](ml-uploading-your-images.md) – After packaging your code in container images and testing them locally, upload the images and scan them for known vulnerabilities\. Fix any vulnerabilities before continuing\. 

1.  [Creating your Amazon SageMaker resource](ml-creating-your-amazon-sagemaker-resource.md) – After your images are scanned successfully, they can be used to create a model package or algorithm resource in SageMaker\. 