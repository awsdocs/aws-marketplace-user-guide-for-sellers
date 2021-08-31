# Packaging your code into images<a name="ml-packaging-your-code-into-images"></a>

Machine learning products in AWS Marketplace use Amazon SageMaker to create and run the machine learning logic you provide for buyers\. SageMaker runs Docker container images that contain your logic\. SageMaker runs these containers in a secure and scalable infrastructure\. For more information, see [ Security and intellectual property](ml-security-and-intellectual-property.md)\.

**Topics**
+ [Which type of container image do I create?](#ml-which-type-of-container-image-do-i-create)
+ [Model package images](ml-model-package-images.md)
+ [Algorithm images](ml-algorithm-images.md)

## Which type of container image do I create?<a name="ml-which-type-of-container-image-do-i-create"></a>

 The two types of container images are an inference image and a training image\. 

 To create a model package product, you need only an inference image\. For detailed instructions, see [Model package images](ml-model-package-images.md)\. 

 To create an algorithm product, you need both training and inference images\. For detailed instructions, see [Algorithm images](ml-algorithm-images.md)\. 

 To package code properly into a container image, the container must adhere to the SageMaker file structure\. The container must expose the correct endpoints to ensure that the service can pass data to and from your container\. The following sections explain the details of this process\. 

**Important**  
 For security purposes, when a buyer subscribes to your containerized product, the Docker containers run in an isolated environment without an internet connection\. When you create your containers, don't rely on outgoing calls over the internet because they will fail\. Calls to AWS services will also fail\. For more information, see the [ Security and intellectual property](ml-security-and-intellectual-property.md) section\. 

 Optionally, when creating your inference and training images, use a container from [Available Deep Learning Containers Images](http://aws.amazon.com/releasenotes/available-deep-learning-containers-images/) as a starting point\. The images are already properly packaged with different machine learning frameworks\. 