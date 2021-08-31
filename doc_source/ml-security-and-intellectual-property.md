# Security and intellectual property<a name="ml-security-and-intellectual-property"></a>

 Amazon SageMaker protects both your intellectual property and buyer data for models and algorithms obtained from AWS Marketplace\. 

## Protecting intellectual property<a name="ml-protecting-intellectual-property"></a>

 When you create a product, the code is packaged in Docker container images\. For more information, see [Prepare your product in SageMaker](ml-prepare-your-product-in-sagemaker.md), later in this guide\. When you upload a container image, the image and artifacts are encrypted in transit and at rest\. The images are also scanned for vulnerabilities before being published\. 

 To help safeguard your intellectual property, SageMaker allows only buyers to access your product through AWS service endpoints\. Buyers cannot directly access or pull container images or model artifacts, nor can they access the underlying infrastructure\. 

## No network access<a name="ml-no-network-access"></a>

 Unlike SageMaker models and algorithms that buyers create, when buyers launch your product from AWS Marketplace, the models and algorithms are deployed without network access\. SageMaker deploys images in an environment with no access to the network or AWS service endpoints\. For example, a container image can't make outbound API calls to services on the internet, [VPC endpoints](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints.html), or any other AWS services\. 

## Security of customer data<a name="ml-security-of-customer-data"></a>

 Your product runs in SageMaker within the buyer’s AWS account\. So, when a buyer uses your product to perform data inference, you as the seller can't access their data\. 

 For algorithm products, model artifacts are outputted by your training image after each training job\. Model artifacts are stored in the buyer’s account\. The model artifacts from the training job are used when the buyer deploys the model with your inference image\. To protect any intellectual property that may be contained in the model artifact, encrypt them before outputting them\. 

**Important**  
 This security model prevents your code from accessing the internet during runtime\. Therefore, your code can't use resources or libraries from the internet, so package your dependencies in the Docker container image\. This is especially important if you choose to encrypt your outputted artifacts from the training job\. The keys to encrypt and decrypt artifacts can't be accessed over the internet at runtime\. They must be packaged with your image\. 

 For more information, see [Security in Amazon SageMaker](https://docs.aws.amazon.com/sagemaker/latest/dg/security.html)\. 